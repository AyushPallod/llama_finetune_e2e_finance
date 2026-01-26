```markdown
---
base_model: unsloth/llama-3.2-3b-instruct-bnb-4bit
library_name: peft
pipeline_tag: text-generation
tags:
- base_model:adapter:unsloth/llama-3.2-3b-instruct-bnb-4bit
- lora
- sft
- transformers
- trl
- unsloth
- finance
- sentiment-analysis
---

# Finance Llama 3.2 3B - Phase 3 Master Run

This model is a fine-tuned version of **Llama 3.2 3B Instruct** optimized for financial sentiment analysis. It was trained using **Unsloth** and **LoRA** adapters to classify financial news into Positive, Neutral, or Negative sentiments.

## Model Details

### Model Description

- **Developed by:** Ayush Pallod
- **Model type:** Large Language Model (Causal LM)
- **Language(s) (NLP):** English
- **License:** Apache-2.0 (based on Llama 3.2 license)
- **Finetuned from model:** unsloth/llama-3.2-3b-instruct-bnb-4bit

## Uses

### Direct Use
This model is intended for analyzing financial text, specifically headlines and short phrases, to determine market sentiment.

### Out-of-Scope Use
The model should not be used as financial advice. It is a sentiment classifier and does not predict future stock prices or market movements.

## How to Get Started with the Model

```python
from unsloth import FastLanguageModel

model, tokenizer = FastLanguageModel.from_pretrained(
    model_name = "AyushPallod/llama_finetune_e2e_finance",
    max_seq_length = 2048,
    load_in_4bit = True,
)
FastLanguageModel.for_inference(model)

```

## Training Details

### Training Data

The model was trained on the **FinanceMTEB/financial_phrasebank** dataset (Sentences from financial news with sentiment labels).

### Training Procedure

#### Training Hyperparameters

* **Epochs:** 3.0
* **Learning Rate:** 2e-4
* **Optimizer:** AdamW 8-bit
* **Batch Size:** 4 (with Gradient Accumulation Steps: 4)
* **Precision:** BF16 Mixed Precision (Optimized for NVIDIA L4)

#### Speeds, Sizes, Times

* **Train Runtime:** 258.23 seconds
* **Train Samples Per Second:** 14.68
* **Final Training Loss:** 1.0244

## Evaluation

The model was monitored via **Weights & Biases** during the master run to ensure loss convergence.

### Results

* **Final Loss:** 1.02
* **Training Steps:** 237

## Environmental Impact

* **Hardware Type:** NVIDIA L4 GPU (24GB VRAM)
* **Hours used:** ~0.1 (Training) + ~2.0 (Setup/Dev)
* **Cloud Provider:** E2E Networks
* **Compute Region:** India

## Technical Specifications

### Compute Infrastructure

The model was trained on a single **NVIDIA L4** node on **E2E Networks** using the Ada Lovelace architecture.

### Software

* **PEFT Version:** 0.18.1
* **Unsloth Engine:** Latest (GitHub build)
* **Transformers:** Latest
* **Python:** 3.12

## Model Card Authors

Ayush Pallod

```

---

To make this perfectly accurate, I have filled in:
1. **Your Name:** As the developer.
2. **The Loss:** 1.0244 (from your terminal output).
3. **The Runtime:** 258 seconds.
4. **Hardware:** NVIDIA L4 on E2E Networks.


```
