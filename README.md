# 🔧 CalibrationAI

An AI-powered calibration and anomaly detection platform for sensor data.  
This project has two main parts:

1. **Backend (FastAPI + Python)** → handles dataset upload, processing, report generation, and charts.  
2. **Frontend (React + Tailwind + Recharts)** → provides a modern UI for file upload, live monitoring, drift prediction, and report downloads.

---

## 📂 Project Structure

```

calibration\_platform/
├─ app.py                  # FastAPI backend entrypoint
├─ pipeline/
│   └─ computation\_engine.py   # Core pipeline logic (processing, ML, etc.)
├─ templates/
│   └─ index.html          # Legacy HTML frontend (can be replaced by React)
├─ static/
│   ├─ charts/             # Generated chart PNGs
│   └─ reports/            # Generated reports (CSV, Excel, PDF)
├─ models/                 # (Optional) Model storage
├─ database/               # SQLite DB files
├─ uploads/                # Uploaded datasets
└─ frontend/               # React + Tailwind frontend

````

---

## ⚙️ Backend Setup (FastAPI)

### 1. Install Python & dependencies
Make sure you have **Python 3.10+** installed. Then:

```bash
cd calibration_platform
pip install -r requirements.txt
````

If you don’t have `requirements.txt`, create one with:

```txt
fastapi
uvicorn
pandas
matplotlib
reportlab
openpyxl
```

### 2. Run the backend server

```bash
cd calibration_platform
python app.py
```

The backend will start at:

```
http://127.0.0.1:8000
```

---

## 🎨 Frontend Setup (React + Tailwind)

### 1. Create the React app

If not already done:

```bash
cd ..
npx create-react-app frontend
```

Move your custom React component `CalibrationPlatform.tsx` into:

```
frontend/src/
```

### 2. Install Tailwind & dependencies

```bash
cd frontend
npm install -D tailwindcss postcss autoprefixer recharts lucide-react
npx tailwindcss init -p
```

Update `tailwind.config.js`:

```js
module.exports = {
  content: ["./src/**/*.{js,jsx,ts,tsx}"],
  theme: { extend: {} },
  plugins: [],
};
```

Update `src/index.css`:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 3. Start the frontend

```bash
npm start
```

Frontend will start at:

```
http://localhost:3000
```

---

## 🔗 Connecting Frontend & Backend

* The **React frontend** uploads CSV files to the backend endpoint:

  ```
  POST http://127.0.0.1:8000/upload_csv/
  ```
* The backend processes the file and returns:

  * Alerts (measured, anomaly, alert, maintenance)
  * Chart URLs
  * Report download links (CSV, Excel, PDF)

These are displayed inside the React dashboard:

* **Live Feed** → maps to `measured`
* **Anomalies Detected** → maps to `anomaly`
* **Alert** → maps to `alert`
* **Drift Over Time** & **RUL/Health** → charts

---

## 📊 Features

✅ Upload CSV sensor datasets
✅ Automated preprocessing & anomaly detection
✅ Predictive drift modeling
✅ Auto-generated reports (CSV, Excel, PDF)
✅ Interactive React dashboard (Tailwind + Recharts)
✅ Downloadable PDF report

---

## 🚀 Usage

1. Start the **backend** (`python app.py`).
2. Start the **frontend** (`npm start`).
3. Open `http://localhost:3000` in your browser.
4. Upload a dataset (`.csv` / `.xlsx` / `.json`).
5. View live metrics, drift predictions, and download reports.

---

## 📌 Future Improvements

* Multi-sensor support (humidity, vibration, etc.)
* User authentication
* Real-time streaming from IoT devices
* Cloud deployment (AWS/GCP)

---

## 📝 License

MIT License © 2025

---

Do you want me to also generate the `requirements.txt` and `package.json` ready-to-use files so you can directly copy them?
```
