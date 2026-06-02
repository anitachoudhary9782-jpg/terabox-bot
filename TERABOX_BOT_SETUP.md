# Terabox Telegram Bot Setup Guide

## Step 1: Bot Token Lena (BotFather se)

1. Telegram app open karo
2. Search karo: **@BotFather**
3. Chat start karo aur ye command bhejo:
```
/newbot
```
4. Bot ka naam puche (kuch bhi de sakto ho, jaise: "TeraDownloaderBot")
5. Username puche (unique hona chahiye, jaise: "teradownload_bot")
6. **Bot Token** milega - isko copy kar lo (ye important h!)

Token kuch aisi dikhegi:
```
123456789:ABCDefGhIjKlMnOpQrStUvWxYz1234567890
```

---

## Step 2: Code Download Karo

Python 3.7+ hona chahiye. Check karo:
```bash
python --version
```

---

## Step 3: Required Libraries Install Karo

```bash
pip install python-telegram-bot requests
```

---

## Step 4: Bot Code (save karo `terabox_bot.py` ke naam)

```python
import logging
from telegram import Update
from telegram.ext import Application, CommandHandler, MessageHandler, filters, ContextTypes
import requests
import re

# Logging setup
logging.basicConfig(
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
    level=logging.INFO
)
logger = logging.getLogger(__name__)

# Apna TOKEN yahan paste karo (Step 1 se jo mila)
BOT_TOKEN = "YOUR_BOT_TOKEN_HERE"

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE) -> None:
    """Bot start hone par welcome message"""
    welcome_text = """
╔════════════════════════════════╗
║  🎥 TERABOX DOWNLOADER BOT 🎥  ║
╚════════════════════════════════╝

📌 Kaise use karo:
1. Terabox link copy karo
2. Mujhe link bhejo
3. Main video/image download kar dunga!

📝 Example:
https://terabox.com/s/1xxxxxxxxx

⚠️ Note: Link public hona chahiye!
    """
    await update.message.reply_text(welcome_text)

async def help_command(update: Update, context: ContextTypes.DEFAULT_TYPE) -> None:
    """Help command"""
    help_text = """
📚 HELP MENU:

/start - Bot start karo
/help - Ye help menu
/info - Bot ki info

👉 Simply koi bhi Terabox link bhejo!
    """
    await update.message.reply_text(help_text)

async def info_command(update: Update, context: ContextTypes.DEFAULT_TYPE) -> None:
    """Bot info"""
    info_text = "🤖 Terabox Downloader Bot v1.0\n\n📝 Direct link bhejo, download pao!"
    await update.message.reply_text(info_text)

def extract_terabox_link(text):
    """Terabox link extract karo"""
    pattern = r'https://terabox\.com/s/[a-zA-Z0-9_-]+'
    match = re.search(pattern, text)
    return match.group(0) if match else None

async def download_terabox(update: Update, context: ContextTypes.DEFAULT_TYPE) -> None:
    """Terabox link process karo aur download karo"""
    user_text = update.message.text
    
    # Link extract karo
    terabox_link = extract_terabox_link(user_text)
    
    if not terabox_link:
        await update.message.reply_text("❌ Valid Terabox link nahi mila!\n\nExample: https://terabox.com/s/...")
        return
    
    # Loading message
    loading_msg = await update.message.reply_text("⏳ Processing... Thoda intezaar karo...")
    
    try:
        # Downloader API use karo
        api_url = f"https://teraboxdownloader.pro/api/download?link={terabox_link}"
        
        response = requests.get(api_url, timeout=10)
        
        if response.status_code == 200:
            data = response.json()
            
            if data.get('success'):
                # Download link milgaya
                download_link = data.get('download_url')
                filename = data.get('filename', 'File')
                
                result_text = f"""
✅ SUCCESS! Download ready:

📁 File: {filename}
📥 Size: {data.get('size', 'N/A')}

🔗 Download Link:
{download_link}

⏱️ Link valid h: 24 hours ke liye
                """
                await loading_msg.edit_text(result_text)
            else:
                await loading_msg.edit_text("❌ Link invalid h ya file delete ho gai!")
        else:
            await loading_msg.edit_text("❌ Processing error! Dobara try karo.")
            
    except Exception as e:
        logger.error(f"Error: {e}")
        await loading_msg.edit_text(f"❌ Error: {str(e)}\n\nDobara try karo!")

async def handle_message(update: Update, context: ContextTypes.DEFAULT_TYPE) -> None:
    """Saare messages handle karo"""
    await download_terabox(update, context)

def main() -> None:
    """Bot start karo"""
    # Application create karo
    application = Application.builder().token(BOT_TOKEN).build()

    # Commands
    application.add_handler(CommandHandler("start", start))
    application.add_handler(CommandHandler("help", help_command))
    application.add_handler(CommandHandler("info", info_command))

    # Messages
    application.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, handle_message))

    # Bot start karo
    application.run_polling(allowed_updates=Update.ALL_TYPES)

if __name__ == '__main__':
    main()
```

---

## Step 5: Token Add Karo

Bot code mein yeh line find karo:
```python
BOT_TOKEN = "YOUR_BOT_TOKEN_HERE"
```

Aur apna token yahan paste karo (Step 1 se).

Example:
```python
BOT_TOKEN = "123456789:ABCDefGhIjKlMnOpQrStUvWxYz1234567890"
```

---

## Step 6: Bot Run Karo

Command line mein:
```bash
python terabox_bot.py
```

Success! ✅

---

## Step 7: Bot Use Karo

Telegram mein apna bot search karo (jo username diya tha) aur:
1. `/start` command bhejo
2. Terabox link paste karo
3. Download link mil jayega!

---

## Agar Local nahi rakhna to VPS par deploy karo:

Popular options:
- **Railway.app** (free tier available)
- **Render** 
- **Heroku** (ab free nahi h)
- **PythonAnywhere**

---

## Troubleshooting:

❓ **"ModuleNotFoundError"** →
```bash
pip install python-telegram-bot requests
```

❓ **"ConnectionError"** → Internet check karo

❓ **Token kaam nahi kar raha** → Token copy-paste sahi se karo

---

## Bot Features:

✅ Direct Terabox links download  
✅ Image support  
✅ Video support  
✅ Fast processing  
✅ Error handling  

---

**Questions? Mujhe poocho!** 😊
