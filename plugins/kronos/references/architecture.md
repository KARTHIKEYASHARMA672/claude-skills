# Kronos Architecture Internals

## High-Level Flow

```
Raw OHLCV → [KronosTokenizer] → (s1_ids, s2_ids) → [Kronos Transformer] → predicted tokens → [KronosTokenizer.decode] → predicted OHLCV
```

---

## KronosTokenizer

- **Encoder**: Stack of `TransformerBlock` layers
- **BSQuantizer** (Binary Spherical Quantization): Converts encoder output into two codebooks:
  - `s1` (s1_bits): Coarse token (pre-token)
  - `s2` (s2_bits): Fine token (post-token, conditioned on s1)
- **Decoder**: Stack of `TransformerBlock` layers, reconstructs OHLCV from quantized tokens
- Loss: `bsq_loss` (reconstruction loss from quantizer)

### Key methods
- `encode(x, half=False)` → `(s1_ids, s2_ids)` tuple
- `decode(x, half=False)` → reconstructed tensor
- `indices_to_bits(x, half)` → bipolar bit representation

---

## Kronos (Predictor)

- **HierarchicalEmbedding**: Embeds `(s1_ids, s2_ids)` into model dimension
- **TemporalEmbedding**: Adds time features (minute, hour, weekday, day, month). Can be learnable (`learn_te=True`)
- **TransformerBlock stack** (n_layers): Self-attention + FFN with causal masking
- **RMSNorm** + **DependencyAwareLayer**: Conditions s2 prediction on predicted s1
- **DualHead**: Separate output heads for s1 logits and s2 logits

### Two-stage decoding (at inference)
1. `decode_s1(s1_ids, s2_ids, stamp)` → `s1_logits, context`
2. Sample `new_s1_id` from `s1_logits`
3. `decode_s2(context, new_s1_ids)` → `s2_logits`
4. Sample `new_s2_id` from `s2_logits`

This keeps s2 conditioned on the predicted s1 at each step.

---

## auto_regressive_inference

The core inference loop in `model/kronos.py`:
- Runs for `pred_len` steps
- Maintains a sliding buffer of `max_context` tokens
- At each step: encode input → decode s1 → sample s1 → decode s2 → sample s2 → append to buffer
- Runs `sample_count` parallel samples (averaged at the end)
- Returns `preds` as numpy array of shape `(batch, pred_len, 6)` (open/high/low/close/volume/amount)

---

## Sampling Parameters

| Parameter | Effect |
|---|---|
| `T` (temperature) | Scales logits before softmax. Lower = more peaked/deterministic. Higher = more diverse. |
| `top_k` | Keeps only top-k tokens. 0 = disabled. |
| `top_p` | Nucleus sampling: cumulative probability cutoff. 0.95–1.0 = more exploration. |
| `sample_count` | Number of independent autoregressive rollouts; their decoded outputs are averaged. |

---

## Time Stamp Features

`calc_time_stamps()` converts datetime index to 5 features:
- `minute`, `hour`, `weekday`, `day`, `month`

Both `x_stamp` (historical) and `y_stamp` (future prediction window) are required during inference.
