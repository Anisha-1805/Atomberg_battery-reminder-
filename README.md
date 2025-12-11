Battery Reminder Notification System
A fully local Battery Reminder Notification System that sends alerts through Firebase Cloud Messaging (FCM), tracks user interactions (open/click events), and generates campaign analytics — all without using AWS or any cloud backend.
This project is built for learning notification flow, analytics, and Python modular structure.

📌 Features
✔️ Send battery reminder notifications using FCM
✔️ 100% local — no AWS / no cloud services
✔️ Track user clicks using a custom analytics module
✔️ Automatic campaign ID creation
✔️ Simple CLI-based testing
✔️ Clean modular architecture
✔️ Easily extendable

Requirements
Python 3.8+

📝 Future Enhancements
1.Dashboard for analytics
2.SQLite storage
3.Auto reminder scheduling

How to Run
1️⃣ Send a notification
python main.py

2️⃣ Log a notification click
python -m analytics click L001 <campaign-id>

3️⃣ View analytics summary
python -m analytics summary <campaign-id>

Output Example
Campaign Summary: Sent=2, Clicks=1, CTR=50%
