# 🧠 Complete Master Training & Environment Guide

This document is a comprehensive guide for setting up and executing a high-accuracy fine-tuning run on an **NVIDIA L4 GPU**. It covers the entire lifecycle from server entry to model export.

---

## 🛠️ 1. Virtual Environment Setup

To prevent library conflicts and protect the system Python installation, we use a **Virtual Environment (venv)**. This creates an isolated "bubble" for your project.

### **Creation & Activation**

1. **Move to your project folder:**
```bash
cd ~/llama_finetune_e2e_finance
```

2. **Create the environment:**
```bash
python3 -m venv venv
```

3. **Activate the environment:**
```bash
source venv/bin/activate
```

*Your command prompt will now show `(venv)` at the beginning, indicating you are working inside the isolated environment.*

---

## 📦 2. Dependency Installation

Run these commands to install the optimized AI engine and its necessary patches:

```bash
# 1. Install Unsloth Engine (Optimized for L4)
pip install --no-deps "unsloth[colab-new] @ git+https://github.com/unslothai/unsloth.git"

# 2. Apply Compatibility Patches (Crucial for avoiding recursion errors)
pip install --upgrade "datasets==4.3.0" protobuf tyro

# 3. Install Core Training Utilities
pip install --no-deps "xformers<0.0.29" "trl<0.9.0" peft accelerate bitsandbytes unsloth_zoo wandb
```

---

## 📝 3. Coding on the Server (Nano Guide)

Since cloud servers do not have a graphical interface, we use **Nano**, a terminal-based text editor.

### **The Nano Workflow:**

1. **Open/Create File:** Type `nano master_train.py`
2. **Writing Code:** Type or paste your Python code into the window
3. **Saving Changes:** Press `Ctrl + O` (Write Out), then press **Enter** to confirm the filename
4. **Exiting the Editor:** Press `Ctrl + X` to return to the main terminal

---

## 🚀 4. Executing the Master Run

To ensure your training doesn't stop if you lose your internet connection, use the **`screen`** utility to run the process in the background.

### **Step-by-Step Execution:**

1. **Start a background session:**
```bash
screen -S training
```

2. **Launch the training script:**
```bash
python3 master_train.py
```

3. **Detach (Safely leave it running):**
   - Press `Ctrl + A` then press **`D`**
   - You can now close your terminal

4. **Re-attach (Check progress):**
```bash
screen -r training
```

---

## 📈 5. Final Hardware Optimization

For **NVIDIA L4** nodes, the script must be configured to use **BFloat16** to prevent `dtype` mismatch errors:

* **`bf16 = True`**
* **`fp16 = False`**

### **Target Performance:**

* **Epochs:** 3
* **VRAM Utilization:** ~18.5 GB / 24 GB
* **Final Training Loss:** ~1.02

---

## 🛑 6. Cleanup & Safety

1. **Sync to GitHub:** Once training finishes, push the `final_fin_llama_3b` folder to your repository immediately
2. **Terminate Instance:** Go to the E2E MyAccount portal and **Terminate/Delete** the node to stop hourly GPU billing

---

## 📋 Bonus: Requirements File

For faster installation in future runs, create a `requirements.txt` file:

```txt
datasets==4.3.0
protobuf
tyro
peft
accelerate
bitsandbytes
wandb
```

**Install all at once with:**
```bash
pip install -r requirements.txt
```

---

**🎯 Quick Reference Command Chain:**

```bash
# Complete setup in one go
cd ~/llama_finetune_e2e_finance
python3 -m venv venv
source venv/bin/activate
pip install --no-deps "unsloth[colab-new] @ git+https://github.com/unslothai/unsloth.git"
pip install --upgrade "datasets==4.3.0" protobuf tyro
pip install --no-deps "xformers<0.0.29" "trl<0.9.0" peft accelerate bitsandbytes unsloth_zoo wandb
screen -S training
python3 master_train.py
# Ctrl+A then D to detach
```
