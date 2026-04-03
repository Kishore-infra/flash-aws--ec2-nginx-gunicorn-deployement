 Flask App Deployment on AWS EC2 with Gunicorn, Nginx & HTTPS

📌 Project Overview

This project demonstrates how to deploy a Flask web application on an AWS EC2 instance using Gunicorn as the application server and Nginx as a reverse proxy. It also includes HTTPS setup using Let's Encrypt.

---

🛠️ Tech Stack

- Python (Flask)
- Gunicorn
- Nginx
- AWS EC2 (Ubuntu)
- DuckDNS (Free domain)
- Let's Encrypt (SSL)

---

⚙️ Steps Performed

1️⃣ Launch EC2 Instance

- Created Ubuntu EC2 instance
- Opened ports: 22 (SSH), 80 (HTTP), 443 (HTTPS)

---

2️⃣ Setup Project

- Connected to EC2 via SSH
- Created project folder
- Setup Python virtual environment
- Installed Flask and Gunicorn

---

3️⃣ Run Flask App

python app.py

---

4️⃣ Run with Gunicorn

gunicorn --bind 0.0.0.0:8000 app:app

---

5️⃣ Configure Nginx

- Installed Nginx
- Configured reverse proxy to Gunicorn
- Removed port usage (used domain instead)

---

6️⃣ Setup Domain (DuckDNS)

- Created free domain
- Pointed domain to EC2 public IP

---

7️⃣ Enable HTTPS

sudo certbot --nginx -d your-domain.duckdns.org

- SSL certificate installed
- HTTPS enabled successfully

---

🌐 Final Result

- App runs on:
  - HTTP → http://your-domain
  - HTTPS → https://your-domain

---

📂 Project Structure

myproject/
│── app.py
│── requirements.txt

---

📦 Requirements

Install dependencies using:

pip install -r requirements.txt

---

💡 Key Learnings

- Deploying Flask app on cloud
- Using Gunicorn as WSGI server
- Configuring Nginx as reverse proxy
- Setting up HTTPS with Let's Encrypt
- Debugging real-world deployment errors

---

🔥 Author

Kishore

---
