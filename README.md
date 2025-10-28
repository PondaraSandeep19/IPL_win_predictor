# 🏏 IPL Win Predictor

A lightweight Streamlit web app that predicts the winning probability of an IPL team based on the current match state.

---

## 📁 Repository Structure

- **`app.py`** — Streamlit application for match prediction  
- **`pipe.pkl`** — Trained scikit-learn pipeline used for predictions  
- **`requirements.txt`** — Required Python dependencies  
- **`matches.csv`**, **`deliveries.csv`** — Dataset files (used for retraining the model)

---

## ⚡ Quick Start (Windows / PowerShell)

### 1️⃣ Navigate to the project directory

```powershell
cd E:\Projects\IPL-Win-Predictor-main
2️⃣ (Optional) Create and activate a virtual environment
powershell
Copy code
python -m venv .venv
& .\.venv\Scripts\Activate.ps1
3️⃣ Install dependencies
powershell
Copy code
python -m pip install -r requirements.txt
4️⃣ Run the Streamlit app
powershell
Copy code
& '.\\.venv\\Scripts\\python.exe' -m streamlit run 'yourpath\app.py'
After execution, open the Local URL displayed in your terminal — usually:
👉 http://localhost:8501

🛑 Stopping the App
Press Ctrl + C in the same PowerShell window.

If port 8501 remains busy, stop the process manually:

powershell
Copy code
if (Get-NetTCPConnection -LocalPort 8501 -ErrorAction SilentlyContinue) {
    Get-NetTCPConnection -LocalPort 8501 |
    Select-Object -ExpandProperty OwningProcess |
    ForEach-Object { Stop-Process -Id $_ -Force }
}
🧠 Notes & Fixes
Runtime pip installation:
app.py may install scikit-learn at runtime.
Once dependencies are installed using requirements.txt, you can remove that section safely.

ZeroDivisionError (Overs = 0):
To avoid errors when overs completed is 0, use this code:

python
Copy code
if overs == 0:
    crr = 0
else:
    crr = score / overs
🔁 Model Retraining
You can retrain the model using matches.csv and deliveries.csv, then overwrite pipe.pkl.
Ensure your retrained pipeline matches the input features expected by app.py.

