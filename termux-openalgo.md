# OpenAlgo Setup on Termux

This guide explains how to set up and run **OpenAlgo** on Termux for Android, including optional Debian installation for full Linux compatibility and Python virtual environment usage.

---

## 1️⃣ Setup & Update Termux

```bash
termux-setup-storage
pkg update && pkg upgrade -y
```

---

## 2️⃣ Install Debian for Full Linux Compatibility

```bash
pkg install proot-distro -y
proot-distro install debian
proot-distro login debian
```

> You are now inside a Debian shell.

---

## 3️⃣ Update Debian Packages

```bash
apt update && apt upgrade -y
apt install git openssl python3 python3-pip python3-venv -y
```

---

## 4️⃣ Clone OpenAlgo Repository

```bash
git clone https://github.com/marketcalls/openalgo.git
cd openalgo/
```

---

## 5️⃣ Create & Activate Python Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

* Your prompt will show `(.venv)` indicating the virtual environment is active.

---

## 6️⃣ Install Python Dependencies

```bash
python3 -m pip install --upgrade pip
python3 -m pip install -r requirements.txt
```

* Installs all required packages inside `.venv`.

---

## 7️⃣ Run OpenAlgo

```bash
# Example if the repo uses app.py
python app.py

# Or if using Flask/FastAPI
flask run
```

> Always run **inside the activated `.venv`** so dependencies are correctly loaded.

---

## 8️⃣ Deactivate Virtual Environment

```bash
deactivate
```

* Returns you to system Python.
* `.venv` remains in the project folder for future use.

---

## 🔧 Optional Tips

* **Re-enter `.venv` later**:

```bash
cd ~/openalgo
source .venv/bin/activate
```

* **Access Termux storage from Debian**:

```bash
ls /data/data/com.termux/files/home/storage
```

* **Delete and recreate `.venv`** if needed without affecting system Python:

```bash
rm -rf .venv
python3 -m venv .venv
source .venv/bin/activate
```

* **Important Notes**:

  * Always install dependencies **inside `.venv`** to avoid conflicts with Termux system Python.

---

## ✅ Summary

1. Setup & update Termux.
2. Install Debian and dependencies.
3. Clone OpenAlgo repo.
4. Create virtual environment `.venv`.
5. Activate `.venv` and install Python requirements.
6. Run OpenAlgo inside `.venv`.
7. Deactivate when done.

You are now ready to use OpenAlgo on your Android device via Termux!

---

## 🚀 Quick Start (After First Setup)

For future runs, simply execute:

```bash
proot-distro login debian --shared-tmp --bind /sdcard
cd ~/openalgo
source .venv/bin/activate
python app.py   # or flask run
```
