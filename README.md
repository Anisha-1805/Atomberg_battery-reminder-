# Battery Health Reminder System

A local, end-to-end system that detects locks with outdated battery checks (>30 days), sends push reminders using Firebase Cloud Messaging (FCM), and tracks user interactions to measure campaign performance.

## 📌 Table of Contents

✨ Project Overview

⚙️ Features
🧰 Tech Stack
🏗️ System Architecture
🚀 Quick Start
🗂️ Configuration & Data Files
🧪 Run & Testing Guide
📁 Project Structure
📊 Findings & Recommendations
🤝 Contributing
📄 License

---

## ✨ Project Overview

The Battery Health Reminder System periodically scans all lock devices, identifies those whose battery hasn’t been checked for more than 30 days, and sends FCM notifications to the assigned users.

It also tracks:

Notification clicks
Campaign opens
Weekly CTR reports
Everything runs locally, using:
SQLite for user & lock mapping
JSON files for lock/battery state
FCM for notifications

---

## ⚙️ Features

✅ Identify stale locks (>30 days old battery check)
✅ Send push reminders via Firebase Cloud Messaging
✅ Track click & open events
✅ Generate weekly CTR reports
✅ Easy to configure, modify, and schedule (Cron / Task Scheduler)
✅ Lightweight + suitable for offline/local simulation

---

## 🧰 Tech Stack
Component	Technology
Language	Python 3.10
Data Store	SQLite (users.db)
Lock Store	JSON (locks.json)
Notifications	Firebase Cloud Messaging (FCM)
Scheduling	OS Scheduler / Cron
Analytics	Local JSON logs

---

## 🏗️ System Architecture
🧩 Components

locks.json → Simulates DynamoDB lock database
users.db (SQLite) → Stores user + lock mapping
main.py → Weekly job to send reminders
firebase_service.py → Wrapper for FCM API
analytics.py → Logs interactions + generates reports
Communication Flow:
main.py reads locks
Checks battery last-update date
Sends FCM notification
User interacts → analytics logged
Weekly report generated

---

## 🚀 Quick Start

1️⃣ Clone the Repository
git clone https://github.com/your-repo/battery-reminder.git
cd battery-reminder

2️⃣ Create Virtual Environment
python3 -m venv .venv
source .venv/bin/activate   # macOS/Linux
# .venv\Scripts\activate     # Windows
pip install -r requirements.txt

3️⃣ Configure Firebase

Create firebase_config.json:
{
  "server_key": "YOUR_FCM_SERVER_KEY",
  "project_id": "your-project-id"
}

4️⃣ Run the weekly reminder job
python main.py

5️⃣ Generate analytics summary
python analytics.py --report weekly

---

## 🗂️ Configuration & Data Files
🔧 Example locks.json
[
  {
    "lock_id": "L001",
    "last_battery_check": "2025-10-01T12:00:00"
  }
]

---

🧾 SQLite Schema (users.db)
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  user_id TEXT NOT NULL,
  fcm_token TEXT NOT NULL
);

CREATE TABLE lock_user_map (
  lock_id TEXT PRIMARY KEY,
  user_id TEXT NOT NULL
);

📡 Firebase Config
{
  "project_id": "your-project-id",
  "server_key": "your-server-key"
}

---

## 🧪 Run & Testing Guide

▶️ Send a Test Notification
python main.py

▶️ Log a user click manually
python analytics.py log-click L001 CAMPAIGN_ID

▶️ View campaign summary
python analytics.py summary CAMPAIGN_ID

---

## 📁 Project Structure

📦 battery-reminder
├── main.py
├── analytics.py
├── firebase_service.py
├── locks.json
├── users.db
├── firebase_config.json
├── requirements.txt
└── README.md

---

## 📊 Findings & Recommendations

✔️ Findings

The system successfully identifies stale locks.
FCM notifications sent reliably.
Click/open analytics functioning correctly.
JSON/SQLite simulation works well for local testing.

---

## 💡 Recommendations

Add a Web Dashboard (Flask/FastAPI)
Move analytics to SQLite for better querying
Add real device battery telemetry
Add scheduling automation script
Provide admin UI for campaign monitoring

---

## 🤝 Contributing

Contributions are welcome!
You can submit:

---

##🌐 GitHub Repository

https://github.com/Anisha-1805/Atomberg_battery-reminder
