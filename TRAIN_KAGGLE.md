# 🚀 Finance Llama: Initial training part

This document chronicles the foundational steps of the project, from initial environment setup to the first prototype fine-tuned on Kaggle.

---

## 🏗️ Phase 1: Infrastructure & Base Selection

The goal of Phase 1 was to select a model and environment that could balance financial "reasoning" with extreme efficiency.

### **1. Base Model Selection**

* **Model:** `unsloth/llama-3.2-3b-instruct-bnb-4bit`
* **Why 3B?** We chose the 3-Billion parameter version of Llama 3.2 because it is the optimal size for financial sentiment analysis—powerful enough to detect market nuance but small enough to fit within the 16GB–24GB VRAM limits of modern cloud GPUs.
* **Quantization:** **4-bit (BNB)** was used to reduce the memory footprint by 70% without significant loss in accuracy.

### **2. The Development Stack**

* **Engine:** [Unsloth AI](https://github.com/unslothai/unsloth) (Used to achieve 2x faster training).
* **Library Patching:** Custom patches were applied to `transformers` and `trl` to avoid recursion errors during 4-bit loading.

---

## 🧪 Phase 2: The Kaggle Prototype

In Phase 2, we moved to **Kaggle** to run our first Supervised Fine-Tuning (SFT) experiments using their free T4 GPUs.

### **1. The Training Dataset**

* **Dataset:** `FinanceMTEB/financial_phrasebank` (sentences_allagree configuration).
* **Structure:** 4,840 sentences from English financial news.
* **Annotation:** Each sentence was human-annotated by 5–8 finance professionals into **Positive**, **Neutral**, or **Negative**.

### **2. Initial Hyperparameters (The Experiment)**

| Parameter | Value | Reason |
| --- | --- | --- |
| **LoRA Rank (r)** | 16 | Sufficient "memory" for sentiment patterns. |
| **LoRA Alpha** | 16 | Balances adapter influence vs base model. |
| **Learning Rate** | 2e-4 | Standard for stable instruction tuning. |
| **Epochs** | 1 (Initial) | Fast iteration to check for convergence. |
| **Batch Size** | 2 per device | Optimized for the 16GB Tesla T4. |

### **3. Phase 2 Key Outcomes**

* **Initial Loss:** Started at ~2.4.
* **Convergence:** The model successfully identified "Neutral" as the majority class, which is critical for financial news to avoid false buy/sell signals.
* **The Bottleneck:** Kaggle's T4 was too slow for the 3-epoch "Master Run," leading to our migration to **E2E Networks** in Phase 3.
