
# Simple Web Tracker

A lightweight full-stack app that tracks a moving vehicle in real-time. It uses a high-speed Python backend and a clean HTML5 canvas frontend to stream data without slowing down your computer.

## 🎯 Project Purpose
When apps track moving items at high speeds, they usually crash because they try to save too many text files at once. This project solves that problem. It packs location data into tiny **binary packets** to save internet data and uses **background workers** on the server so the map never lags.

## 📊 Left Panel Readouts Explained

When looking at the dashboard screen, here is exactly what each number on the left means:

*   **Kinematic Vector [X, Y] (e.g., `438.01m, -303.76m`):** This is the exact map location of the vehicle in meters, measuring how far it has traveled from its starting point.
*   **Orientation Angle (𝜽) (e.g., `-12.3°`):** This is the steering angle of the car. It shows which direction the vehicle is facing as it turns.
*   **Ingestion Flux (Throughput) (e.g., `6.7 req/s`):** This shows how many data updates are being sent per second. `6.7 req/s` means the car is updating its position over 6 times every second.
*   **Network Packet Footprint (`20 bytes`):** This is the size of the data package. By compressing the location data into raw binary format instead of heavy text files, we squished the data down to a tiny 20 bytes, saving 75% of your internet bandwidth.
*   **Geofence Integrity Status (`🟢 BINARY LAYER SYNCED` / `⚠️ GEOFENCE BREACHED`):** This is the safety tracker. If the vehicle stays inside the safe boundary box, it lights up green. The exact millisecond the car drives outside the boundaries, it automatically flips to a red alert.

---

## 🛠️ Tools Used
*   **Python 3.14:** Runs the backend data server and uses "multi-threading" to process incoming points in the background.
*   **HTML5 Canvas & JavaScript:** Paints the moving red dot and blue path smoothly onto a clean grid layout.
*   **Tailwind CSS Styles:** Handles the dark-theme layout, sidebar panels, and alert banners.

---

## 🚀 How to Run It

1. Start your backend data server in your first window:
   ```bash
   python backend/main.py
   ```

2. Start your website map server in your second window:
   ```bash
   python -m http.server 8080 --directory frontend
   ```

3. Open your browser and go to:
   `http://localhost:8080`
