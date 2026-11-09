---
name: kronos
description: >
  Expert guide for working with the Kronos financial time-series prediction model (by NeoQuasar).
  Use this skill whenever the user mentions Kronos, KronosPredictor, Kronos-mini/small/base, stock prediction with Kronos,
  fine-tuning Kronos on CSV data, running the Kronos WebUI, or loading/using Kronos from HuggingFace.
  Also trigger when the user asks how to predict OHLCV (open/high/low/close/volume) data, set up a financial
  forecasting pipeline, prepare data for Kronos, or troubleshoot Kronos inference/training errors.
  Always consult this skill before attempting to write Kronos usage code or advise on fine-tuning steps.
---

# Kronos Skill

Kronos is a financial time-series foundation model developed by NeoQuasar, designed for autoregressive prediction of OHLCV (open, high, low, close, volume, amount) candlestick data. It uses a two-stage architecture: a **KronosTokenizer** (BSQ-based quantizer) + a **Kronos predictor** (hierarchical transformer).

---

## Architecture Overview

| Component | Role |
|---|---|
| `KronosTokenizer` | Encodes raw OHLCV data into discrete tokens via Binary Spherical Quantization (BSQ). Has encode/decode methods. |
| `Kronos` | Autoregressive transformer that predicts next tokens (s1 + s2 hierarchy). |
| `KronosPredictor` | High-level wrapper combining tokenizer + model. Exposes `predict()` and `predict_batch()`. |

**Token hierarchy**: Each time step produces two tokens — `s1` (coarse) and `s2` (fine, conditioned on s1). This is the "Dual Head" design.

---

## Available Models (HuggingFace)

| Model | HF ID | Tokenizer HF ID | Context | Params |
|---|---|---|---|---|
| Kronos-mini | `NeoQuasar/Kronos-mini` | `NeoQuasar/Kronos-Tokenizer-2k` | 2048 | 4.1M |
| Kronos-small | `NeoQuasar/Kronos-small` | `NeoQuasar/Kronos-Tokenizer-base` | 512 | 24.7M |
| Kronos-base | `NeoQuasar/Kronos-base` | `NeoQuasar/Kronos-Tokenizer-base` | 512 | 102.3M |

---

## Quick Start: Inference

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Load model and run prediction

```python
import pandas as pd
from huggingface_hub import hf_hub_download
from model import Kronos, KronosTokenizer, KronosPredictor

# Load tokenizer and model from HuggingFace
tokenizer = KronosTokenizer.from_pretrained("NeoQuasar/Kronos-Tokenizer-base")
model = Kronos.from_pretrained("NeoQuasar/Kronos-base")

# Create predictor (auto-detects device: CUDA > MPS > CPU)
predictor = KronosPredictor(model, tokenizer)

# Load your OHLCV data
df = pd.read_csv("your_data.csv")
df['timestamps'] = pd.to_datetime(df['timestamps'])

# Define input window and prediction window
x_timestamp = df['timestamps'].iloc[:400]   # historical timestamps
y_timestamp = pd.date_range(                # future timestamps to predict
    start=x_timestamp.iloc[-1],
    periods=121, freq='5min'
)[1:]

# Run prediction
pred_df = predictor.predict(
    df=df.iloc[:400],
    x_timestamp=x_timestamp,
    y_timestamp=y_timestamp,
    pred_len=120,
    T=1.2,          # temperature: 1.2-1.5 recommended
    top_k=0,
    top_p=0.95,
    sample_count=2  # average multiple samples for stability
)

print(pred_df)  # DataFrame with open/high/low/close/volume/amount columns
```

---

## Data Format Requirements

CSV must have these columns:

| Column | Required | Notes |
|---|---|---|
| `timestamps` | Yes | Parseable datetime string |
| `open` | Yes | Numeric |
| `high` | Yes | Numeric |
| `low` | Yes | Numeric |
| `close` | Yes | Numeric |
| `volume` | No | Set to 0 if unavailable |
| `amount` | No | Set to 0 if unavailable |

- No NaN values allowed in price/volume columns
- If `volume` or `amount` is missing, KronosPredictor fills them with 0 automatically

---

## Prediction Parameters

| Parameter | Type | Default | Notes |
|---|---|---|---|
| `pred_len` | int | — | Number of future steps to predict |
| `T` | float | 1.0 | Temperature. Higher = more diverse. Try 1.2–1.5 |
| `top_k` | int | 0 | Top-k sampling. 0 = disabled |
| `top_p` | float | 0.9 | Nucleus sampling threshold. 0.95–1.0 recommended |
| `sample_count` | int | 1 | Number of parallel samples (averaged). 2–3 improves quality |
| `verbose` | bool | True | Show autoregressive progress bar |

---

## Batch Prediction

Predict multiple series in parallel (all series must have same historical length and pred_len):

```python
pred_dfs = predictor.predict_batch(
    df_list=[df1, df2, df3],
    x_timestamp_list=[ts1, ts2, ts3],
    y_timestamp_list=[future_ts1, future_ts2, future_ts3],
    pred_len=120,
    T=1.2, top_p=0.95, sample_count=2
)
```

---

## WebUI

Launch the web interface for GUI-based prediction:

```bash
cd webui
python run.py
# OR
python app.py
# Visit http://localhost:7070
```

**WebUI features**: CSV/Feather upload, 400+120 sliding window selection, K-line chart output, temperature/top_p/sample_count controls, prediction vs actual comparison.

---

## Fine-tuning on Custom Data

See `references/finetuning.md` for the full fine-tuning guide.

**Quick summary:**
1. Prepare CSV with `timestamps, open, high, low, close, volume, amount`
2. Edit `finetune_csv/configs/config_ali09988_candle-5min.yaml` (set `data_path`, `pretrained_model_path`)
3. Run sequential training:
   ```bash
   cd finetune_csv
   python train_sequential.py --config configs/your_config.yaml
   ```
4. Fine-tuned models saved to `{base_save_path}/{exp_name}/tokenizer/best_model/` and `.../basemodel/best_model/`

---

## Common Errors & Fixes

| Error | Cause | Fix |
|---|---|---|
| `Missing price columns` | CSV missing open/high/low/close | Rename columns to match required names |
| `NaN values in price columns` | NaN in data | Use `df.dropna()` or fill before passing |
| `Inconsistent seq lengths in predict_batch` | Different history lengths across batch | Pad or truncate all series to same length |
| `CUDA out of memory` | Large batch or long context | Reduce `sample_count` or use `Kronos-mini` |
| Model download slow | First-time HF download | Be patient; models are cached after first load |

---

## References

- Full fine-tuning guide: `references/finetuning.md`
- Architecture internals: `references/architecture.md`
