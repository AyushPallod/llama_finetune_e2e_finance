# 🔑 SSH Key & Cloud Connection Guide

This guide explains how to generate a secure SSH key pair on Windows and correctly associate it with an **E2E Networks** GPU node to avoid "Permission Denied" errors.

---

## 🛠️ 1. Generate SSH Keys (Local Machine)

We use the **ED25519** algorithm because it is more secure and faster than the older RSA standard.

1. Open your **Command Prompt (CMD)** or **PowerShell**.
2. Run the following command:
```bash
ssh-keygen -t ed25519 -C "your_email@gmail.com"

```
3. **Save Location:** Press `Enter` to save it in the default folder (`C:\Users\YourName\.ssh\id_ed25519`).
4. **Passphrase:** Press `Enter` twice to leave it empty (recommended for beginners).

---

## 🛰️ 2. Transfer the "Lock" to E2E Portal

You must give E2E your **Public Key** so the server knows your laptop is allowed to enter.

1. **Copy your Public Key:** In CMD, run:
```bash
type C:\Users\YourName\.ssh\id_ed25519.pub

```
2. Copy the entire line that starts with `ssh-ed25519`.
3. **Upload to E2E:**
* Go to **Products > SSH Keys** in the E2E MyAccount portal.
* Click **Add New SSH Key**.
* Paste your key and name it `My-L4-Key`.

---

## 🚀 3. Connect to the Server (CMD to E2E)
Once your node is "Running," use your Private Key to unlock the connection.
### **The Standard Command:**

```bash
ssh -i "C:\Users\YourName\.ssh\id_ed25519" root@<YOUR_PUBLIC_IP>

```

