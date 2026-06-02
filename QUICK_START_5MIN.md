# ⚡ 5 MINUTE QUICK START - Terabox Bot

## Step 1: Bot Token Lena (2 Minutes)

**Telegram mein:**
```
Search karo: @BotFather
/newbot command bhejo
Bot name: TeraDownloadBot (ya koi aur)
Username: teradownload_bot (unique banana)
Token copy karo!
```

Token milega aisi:
```
123456789:ABCDefGhIjKlMnOpQrStUvWxYz1234567890
```

---

## Step 2: Code Setup (2 Minutes)

### Windows:
```bash
# Python install karo: python.org se

# Terminal/CMD mein:
pip install python-telegram-bot requests
```

### Linux/Mac:
```bash
python3 -m pip install python-telegram-bot requests
```

---

## Step 3: Bot Code Modify Karo (1 Minute)

**File: `terabox_bot_advanced.py`**

Yeh line find karo:
```python
BOT_TOKEN = "YOUR_BOT_TOKEN_HERE"
```

Replace karo apna token:
```python
BOT_TOKEN = "123456789:ABCDefGhIjKlMnOpQrStUvWxYz1234567890"
```

Save karo (Ctrl+S)

---

## Step 4: Bot Chalao! 🚀

Terminal/CMD mein:
```bash
python terabox_bot_advanced.py
```

Ya:
```bash
python3 terabox_bot_advanced.py
```

Success! ✅ Ye message aayega:
```
🤖 Bot starting... @TeraBoxDownloadBot
```

---

## Step 5: Bot Test Karo! 

Telegram mein apna bot search karo:
1. `/start` bhejo
2. Terabox link paste karo
3. Download link mil jayega!

---

## 🎉 Done! Bot Ready!

---

## ⚠️ Common Issues:

### "No module named telegram"
```bash
pip install python-telegram-bot
```

### "Invalid token"
Token sahi se copy-paste karo, spaces na hoon

### "Connection timeout"
- Internet check karo
- VPN off karo
- Terabox server check karo

### Bot nahi chalra
```bash
# Debug mode mein chalao:
python -u terabox_bot_advanced.py
```

---

## 🌐 Production mein Chalane ke liye:

### Option 1: Railway.app (Easy & Free)
1. railway.app par sign up karo
2. New Project → GitHub repo connect karo
3. requirements.txt banao (upload below)
4. Bot auto-deploy hoga

### requirements.txt:
```
python-telegram-bot==20.3
requests==2.31.0
```

### Option 2: PythonAnywhere
1. pythonanywhere.com par account banao
2. Code upload karo
3. Always-on setting enable karo
4. 24/7 chalega

### Option 3: AWS EC2 (Advanced)
Linux instance banao aur bot chalao

---

## 📱 Bot Use Karte Waqt:

✅ Terabox link public share karna padta h  
✅ Link ko pura copy karo (chota mat karo)  
✅ Ek time ek link bhejo  
✅ Bot ko time do process karne ke liye  

---

## 🔧 Bot Customize Karo:

### Bot ka greeting change karo:
Search: `╔═════════════════════════════════════╗`
Edit welcome message

### New command add karo:
```python
async def new_command(update: Update, context: ContextTypes.DEFAULT_TYPE) -> None:
    await update.message.reply_text("Your message")

# Phir add karo:
application.add_handler(CommandHandler("command_name", new_command))
```

### API change karo (agar koi downloader fail ho):
```python
DOWNLOADER_APIS = [
    "https://teraboxdownloader.pro",
    "https://teradownloadr.com",
    "https://www.teraboxfast.com"
]
```

---

## 📊 Bot Stats Track Karo:

File add karo: `config.json`
```json
{
    "total_downloads": 0,
    "total_users": 0,
    "uptime": "24/7"
}
```

---

## 🛡️ Security Tips:

1. Token kisi ko mat batao!
2. Token file mein store karo (safe)
3. Git push karte waqt token exclude karo
4. Regularly token rotate karo

---

## 📞 Support:

❓ Kuch problem h?
1. Error message copy karo
2. Google par search karo
3. Stack Overflow check karo
4. Bot developer se poocho

---

## 🎓 Learn More:

- Official Docs: https://python-telegram-bot.readthedocs.io
- GitHub: https://github.com/python-telegram-bot/python-telegram-bot
- Terabox API: https://terabox.com (developer docs)

---

## Next Steps:

✅ Basic Bot - Complete ✓  
⬜ Add Database (users track karne ke liye)  
⬜ Add Admin Panel  
⬜ Add Payment (Premium features)  
⬜ Add Ads  

---

**Aur koi help chahiye? Poocho!** 😊

```
Happy Coding! 🚀
```
