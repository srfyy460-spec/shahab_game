
import os
import json
import urllib.request
import urllib.parse

TOKEN = os.environ["BOT_TOKEN"]
API = f"https://api.telegram.org/bot{TOKEN}/"

def request(method, data=None):
    url = API + method
    body = urllib.parse.urlencode(data or {}).encode()
    with urllib.request.urlopen(url, body, timeout=60) as response:
        return json.loads(response.read())

offset = 0

while True:
    updates = request("getUpdates", {
        "offset": offset,
        "timeout": 50
    })

    for update in updates.get("result", []):
        offset = update["update_id"] + 1
        message = update.get("message", {})
        text = message.get("text", "")

        if text.startswith("/start"):
            request("sendMessage", {
                "chat_id": message["chat"]["id"],
                "text": "سلام! 👋 خوش اومدی ❤️"
            })
