# OpenAlgo Setup on Termux

This guide explains how to set up and run **OpenAlgo** on Termux for Android, including optional Debian installation for full Linux compatibility, Python virtual environment usage.

---

## 1️⃣ Update Termux & Packages

```bash
pkg update && pkg upgrade -y
pkg install proot-distro
````

---

## 2️⃣ Setup Termux Storage

```bash
termux-setup-storage
```

* Grants access to `/sdcard` and `~/storage` directories.
* Useful for saving logs, datasets, or outputs outside the chroot environment.


---

## 3️⃣ (Optional) Install Debian for Full Linux Compatibility

```bash
proot-distro install debian
proot-distro login debian
```

> You are now inside a Debian shell.

---

## 4️⃣ Update Debian Packages

```bash
apt update && apt upgrade -y
apt install git clang rust cargo openssl python3 python3-pip -y
```

---

## 5️⃣ Clone OpenAlgo Repository

```bash
git clone https://github.com/marketcalls/openalgo.git
cd openalgo/
```

---

## 6️⃣ Create & Activate Python Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

* Your prompt will show `(.venv)` indicating the virtual environment is active.

---

## 7️⃣ Install Python Dependencies

```bash
python3 -m pip install --upgrade pip
python3 -m pip install -r requirements.txt
```

* Installs all required packages inside `.venv`.
* Make sure `clang`, `rust`, `cargo`, and `openssl` are installed on Termux for compiling dependencies.

---

## 8️⃣ Run OpenAlgo

```bash
# Example if the repo uses app.py
python app.py

# Or if using Flask/FastAPI
flask run
```

> Always run **inside the activated `.venv`** so dependencies are correctly loaded.

---

## 9️⃣ Deactivate Virtual Environment

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

1. Update Termux.
2. Setup Termux storage for file access.
3. (Optional) Debian → install dependencies.
4. Clone OpenAlgo repo.
5. Create virtual environment `.venv`.
6. Activate `.venv` and install Python requirements.
7. Run OpenAlgo inside `.venv`.
8. Deactivate when done.

You are now ready to use OpenAlgo on your Android device via Termux!

```
