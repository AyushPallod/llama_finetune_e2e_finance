# 🛡️ E2E Networks: SSH Connection Guide

This guide explains how to connect to an E2E Networks GPU node (NVIDIA L4) and troubleshoot common connection errors.

## **1. Generate SSH Keys**
1. Open **Command Prompt (CMD)** or **PowerShell**.
2. Run: `ssh-keygen -t ed25519 -C "your_email@gmail.com"`
3. Press **Enter** for all prompts.
4. Your keys are saved in `C:\Users\YourName\.ssh\`:
   - `id_ed25519.pub`: **Public Key** (The lock for the portal).
   - `id_ed25519`: **Private Key** (Keep this secret!).

## **2. Add to E2E Portal**
1. Go to **Products > SSH Keys** in E2E MyAccount.
2. Click **Add New SSH Key**.
3. Paste the **entire content** of `id_ed25519.pub`.
4. Name it `Lenovo-Key`.

## **3. Connecting to the Node**
Once your node is "Running," use the following command:
```bash
ssh -i "C:\Users\YourName\.ssh\id_ed25519" root@<YOUR_PUBLIC_IP>
