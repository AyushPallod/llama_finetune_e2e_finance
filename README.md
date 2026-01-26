# 📈 Finance Llama: End-to-End Sentiment Analysis Pipeline

A professional-grade fine-tuning project that transforms a base **Llama 3.2 3B** model into a specialized financial sentiment classifier. This project covers the entire MLOps lifecycle: from a **Kaggle** prototype to a high-performance **NVIDIA L4** production-grade training run.

---

## 🚀 Project Overview
This model is trained to classify financial news headlines into three categories: **Positive**, **Neutral**, and **Negative**. It achieves high precision by leveraging **LoRA (Low-Rank Adaptation)** and the **Unsloth** optimization engine.

### **Key Metrics (Phase 3 Final Run)**
- **Base Model:** Llama 3.2 3B
- **Hardware:** NVIDIA L4 (24GB VRAM)
- **Training Time:** ~4 minutes (Optimized via Unsloth)
- **Final Training Loss:** 1.02
- **Precision Format:** BFloat16 (Native L4 support)

---

## 🛠️ Tech Stack
- **Engine:** [Unsloth](https://github.com/unslothai/unsloth) (2x faster training, 70% less memory)
- **Framework:** PyTorch, Hugging Face Transformers, TRL
- **Tracking:** [Weights & Biases (W&B)](https://wandb.ai/) for real-time loss monitoring
- **Infrastructure:** Kaggle (Phase 2) ➡️ E2E Networks (Phase 3 Scaling)

---

---
## 📊 Training Reports
The full training logs, including hardware utilization and loss convergence, are available here: 
[Llama 3.2 3B Training Report](https://api.wandb.ai/links/kaggle_llama_project/kkgpodcr)
---
## 📂 Repository Structure
- `master_train.py`: The main execution script for Phase 3.
- `SSH_SETUP.md`: Full guide on connecting to cloud GPUs from Windows.
- `MASTER_TRAINING.md`: Deep dive into Linux setup, `venv`, and Nano editor usage.
- `final_fin_llama_3b/`: The finalized model weights (Adapters).

---

## 💻 Quick Start: Environment Setup

### **1. Create a Virtual Environment**
Always isolate your AI projects to prevent library conflicts.
```bash
# Create and enter the "bubble"
python3 -m venv venv
source venv/bin/activate
