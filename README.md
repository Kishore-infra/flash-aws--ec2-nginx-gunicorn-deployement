# Flask App Deployment — AWS EC2 Production Setup

A simple Flask web app that I deployed end-to-end on AWS EC2 — from a blank Linux server to a live HTTPS URL. This was my 3rd project, and the first time I added SSL and Gunicorn to a production setup.

The app returns a response from the server — small output, but the real learning was everything around it: configuring the server, debugging errors, and getting HTTPS to work.

---

## What I built and configured

- Launched an AWS EC2 instance (Ubuntu Linux) from scratch
- Configured Nginx as a reverse proxy to route traffic to the app
- Set up Gunicorn as the WSGI server to serve Flask in production
- Secured the site with HTTPS using Let's Encrypt + Certbot
- Configured DNS and domain routing
- Debugged real production errors: 502 Bad Gateway, 500 Internal Server Error

---

## Architecture

Browser → DNS → EC2 Public IP → Nginx (port 80/443) → Gunicorn → Flask App

---

## Errors I actually faced (and fixed)

**502 Bad Gateway**
Nginx was running but couldn't reach Gunicorn. Root cause: Gunicorn wasn't started yet. Fix: started Gunicorn and confirmed the socket path matched the Nginx config.

**500 Internal Server Error**
The app itself was throwing an error. Checked the Gunicorn logs, found the issue in the Flask code, fixed and restarted.

Total debugging time: ~5–6 hours across the full deployment.

---

## How I debugged

A mix of reading error logs manually, searching specific error messages, and using AI tools to understand what the logs meant. The actual fixes were applied and tested by me.

---

## What I learned from this vs my previous projects

- My 2nd project didn't have HTTPS or Gunicorn — this one does
- Each project taught me one more layer of how production servers actually work
- Next goal: automate this setup with a shell script or Ansible

---

## Why it's not live

Deployed and tested successfully. EC2 instance stopped to avoid ongoing AWS charges — a deliberate cost management decision.

---

## Stack

Python · Flask · AWS EC2 · Ubuntu Linux · Nginx · Gunicorn · SSL/TLS · Let's Encrypt · Certbot · DNS · Git

---

## Run locally

```bash
git clone https://github.com/Kishore-infra/flash-aws--ec2-nginx-gunicorn-deployement.git
cd your-repo-name
pip install -r requirements.txt
python app.py
```
