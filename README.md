<h1 align= center>Telegram Bot Status Repo</h1>
<h3 align = center>A telegram bot that monitors the uptime and CPU usage of your bots, ensuring they're always up and running. It refreshes automatically and runs 24/7 for your convenience. </h3>
<p align="center">
<a href="https://python.org"><img src="http://forthebadge.com/images/badges/made-with-python.svg" alt="made-with-python"></a>
<br>
    <img src="https://img.shields.io/github/stars/itzshukla/STRANGER-BOT-STATUS?style=for-the-badge" alt="Stars">
    <img src="https://img.shields.io/github/forks/itzshukla/STRANGER-BOT-STATUS?style=for-the-badge" alt="Forks">
    <img src="https://img.shields.io/github/watchers/itzshukla/STRANGER-BOT-STATUS?style=for-the-badge" alt="Watchers"> 
<br>
    <img src="https://img.shields.io/github/repo-size/itzshukla/STRANGER-BOT-STATUS?style=for-the-badge" alt="Repository Size">
    <img src="https://img.shields.io/github/contributors/itzshukla/STRANGER-BOT-STATUS?style=for-the-badge" alt="Contributors">
    <img src="https://img.shields.io/github/issues/itzshukla/STRANGER-BOT-STATUS?style=for-the-badge" alt="Issues">
</p>  

## Config Vars
1. `API_ID` : Telegram API_ID, get it from my.telegram.org/apps
2. `API_HASH` : Telegram API_ID, get it from my.telegram.org/apps
3. `SESSION_STRING` : A valid Pyrogram session string, get it from [@StringSesssionGeneratorRobot](https://t.me/StringSesssionGeneratorRobot)
4. `BOT_TOKEN` : A valid bot token, get it from [@BotFather](https://t.me/BotFather)
5. `BOT_LIST` : Your bot username list without '@' (Example: StringSesssionGeneratorRobot StrangerSuperbot)
6. `CHANNEL_OR_GROUP_ID` : Your channel's or group's Telegram id (Example: -1002018556839)
7. `MESSAGE_ID` : Telegram id of message from your channel or group (Example: 10)
8. `OWNER_ID` : Owner id (Example: 6919199044 6762113050)
9. `TIME_ZONE`: Your time zone (Example: Asia/Kolkata)

## Example
![image](https://graph.org/file/932074b8030bf0f5c5506.jpg)

## Tutorial 

### Method 1 (Easy)
1. Install this using pip3 in whichever bot(pyrogram or telethon) you want to know the status

**If Pyrogram**
```
pip3 install git+https://github.com/itzshukla/STRANGER-BOT-STATUS.git@pyro
```

**If Telethon**
```
pip3 install git+https://github.com/itzshukla/STRANGER-BOT-STATUS.git@tele
```

2. Import the Client Class with

**If Pyrogram**
```python
from PyroStatus import PyroClient
```

**If Telethon**
```python
from TeleStatus import TeleClient
```

3. Just replace the normal Client with this client. For eg:

**If Pyrogram**
```python
app = PyroClient(
    name="bot",
    api_id=69696,
    api_hash="",
    bot_token=""
)
```

**If Telethon**
```python
app = TeleClient(
    "bot",
    api_id,
    api_hash,
).start(bot_token="")
```
4. Thats it now just deploy this repo!

### Method 2 (Manual)

1. Add the following code snippet at the beginning of your `__init__.py` file to define the `start_time` variable:
```python
import time

start_time = time.time()

```

2. Now Copy the following code and add it into your repository ( In plugins directory or wherever your plugins exists):
```python
import psutil
import time
from _ import start_time, Client # replace _ where you declare the start_time, Client
from pyrogram import filters 
from pyrogram.types import Message

# TeamUltroid/Ultroid
def time_formatter(milliseconds):
    minutes, seconds = divmod(int(milliseconds / 1000), 60)
    hours, minutes = divmod(minutes, 60)
    days, hours = divmod(hours, 24)
    weeks, days = divmod(days, 7)
    tmp = (((str(weeks) + "w:") if weeks else "") +
           ((str(days) + "d:") if days else "") +
           ((str(hours) + "h:") if hours else "") +
           ((str(minutes) + "m:") if minutes else "") +
           ((str(seconds) + "s") if seconds else ""))
    if not tmp:
        return "0s"
    if tmp.endswith(":"):
        return tmp[:-1]
    return tmp


@Client.on_message(filters.command('statusbot') & filters.private)
async def activevc(_, message: Message):
    uptime = time_formatter((time.time() - start_time) * 1000)
    cpu = psutil.cpu_percent()
    TEXT = f"UPTIME: {uptime} | CPU: {cpu}%"
    await message.reply(TEXT)
```
3. Now add the bot to your channel and make him admin.

## Deployment Methods

### Heroku

To deploy on a Heroku, follow these steps:

1. Fork this repository

2. Click the Deploy button below 
    
[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/itzshukla/STRANGER-BOT-STATUS)

### Vps

To deploy on a VPS, follow these steps

1. Update and upgrade your system packages:
```
sudo apt-get update && sudo apt-get upgrade -y
```

2. Clone the repository and navigate to the project directory:
```
git clone https://github.com/itzshukla/STRANGER-BOT-STATUS && cd Bot-Status
```

3. Install the required packages:
```
pip3 install -U -r requirements.txt
```
4. Create .env using example.env
```
cp example.env .env
```
5. Now open the .env file using **vi .env**
6. Edit the vars, by pressing **I**  on the keyboard
7. After editing save the file using **ctrl + c** then **:wq**
8. Run the script using Python 3:
```
python3 main.py
```

## Support
- [Channel](https://t.me/ABOUT_SHIVANSHOP)
- [Group](https://t.me/mastiwithfriendsx)

## Credits
- [TeLe TiPs](https://github.com/teletips/Powerful_BotStatus-TeLeTiPs)
- [Pyrogram](https://github.com/pyrogram/pyrogram)