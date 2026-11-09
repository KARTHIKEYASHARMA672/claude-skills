# Kronos Fine-tuning Guide

## Overview

Fine-tuning trains two components sequentially:
1. **KronosTokenizer** — learns to quantize your domain's price distributions
2. **Kronos predictor** — learns temporal patterns using the fine-tuned tokenizer

---

## Step 1: Prepare Data

CSV format (required columns):

```
timestamps, open, high, low, close, volume, amount
2019/11/26 9:35, 182.45, 184.45, 184.95, 182.45, 15136000, 0
2019/11/26 9:40, 184.35, 183.85, 184.55, 183.45, 4433300, 0
```

- `volume` and `amount` can be 0 if not available
- Reference example: `finetune_csv/data/HK_ali_09988_kline_5min_all.csv`

---

## Step 2: Edit Config

Copy and edit `finetune_csv/configs/config_ali09988_candle-5min.yaml`:

```yaml
data:
  data_path: "/path/to/your/data.csv"
  lookback_window: 512    # historical points for training
  predict_window: 48      # future points to predict per sample
  max_context: 512        # max context length (match model)

model:
  pretrained_model_path: "NeoQuasar/Kronos-base"  # or local path
  pretrained_tokenizer_path: "NeoQuasar/Kronos-Tokenizer-base"

training:
  epochs: 50
  batch_size: 32
  learning_rate: 1e-4
  base_save_path: "./checkpoints"
  exp_name: "my_experiment"
```

---

## Step 3: Train

### Method 1: Sequential (Recommended)
```bash
cd finetune_csv
# Full pipeline
python train_sequential.py --config configs/your_config.yaml

# Skip tokenizer if already trained
python train_sequential.py --config configs/your_config.yaml --skip-tokenizer

# Skip predictor if already trained
python train_sequential.py --config configs/your_config.yaml --skip-basemodel

# Skip if model already exists on disk
python train_sequential.py --config configs/your_config.yaml --skip-existing
```

### Method 2: Train components separately
```bash
# Step 1: Train tokenizer
python finetune_tokenizer.py --config configs/your_config.yaml

# Step 2: Train predictor (requires fine-tuned tokenizer)
python finetune_base_model.py --config configs/your_config.yaml
```

### Multi-GPU (DDP)
```bash
DIST_BACKEND=nccl torchrun --standalone --nproc_per_node=8 \
  train_sequential.py --config configs/your_config.yaml
```
Use `gloo` backend for CPU or mixed environments.

---

## Step 4: Check Outputs

```
{base_save_path}/{exp_name}/
├── tokenizer/best_model/   ← fine-tuned tokenizer
├── basemodel/best_model/   ← fine-tuned predictor
└── logs/                   ← training logs
```

---

## Step 5: Use Fine-tuned Model

```python
from model import Kronos, KronosTokenizer, KronosPredictor

tokenizer = KronosTokenizer.from_pretrained("./checkpoints/my_experiment/tokenizer/best_model")
model = Kronos.from_pretrained("./checkpoints/my_experiment/basemodel/best_model")
predictor = KronosPredictor(model, tokenizer)
```

Then use `predictor.predict()` as normal.
