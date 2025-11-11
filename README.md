# 💧 WiFi Pump Relay v2

WiFi Pump Relay v2 is an **ESP8266-based automation system** that allows you to control a **water pump** (or any relay-driven device) via **Telegram commands** and **scheduled automation**.  
It can turn the pump **ON/OFF remotely** through Telegram messages and also **run automatically** at set times — no manual intervention needed.

---

## ⚙️ Features

- 🛰️ **WiFi + Telegram Control** – Operate the pump directly from Telegram.
- ⏰ **Automatic Scheduling** – Runs the pump automatically at specific times.
- 💡 **Manual Override** – Send Telegram commands to instantly toggle the relay.
- 🔁 **Auto Turn-Off Timer** – Automatically turns off the pump after a set runtime (e.g., 1 hour).
- 📡 **Status Updates** – Get feedback in Telegram (e.g., when the pump starts or stops).
- 🔒 **Simple & Secure** – Works over HTTPS using Telegram’s API.

---

## 🧰 Hardware Requirements

| Component | Description |
|------------|--------------|
| **ESP8266** | NodeMCU / Wemos D1 Mini (tested) |
| **Relay Module** | 1-channel or 2-channel relay board (5V or 3.3V logic compatible) |
| **Water Pump** | Any AC/DC pump within relay rating |
| **Power Supply** | 5V micro-USB or regulated 5V adapter |

---

## 🔌 Wiring

| ESP8266 Pin | Relay Module | Description |
|--------------|---------------|-------------|
| D1 (GPIO5)   | IN1           | Pump control signal |
| 3V3 / 5V     | VCC           | Power supply for relay |
| GND          | GND           | Common ground |

*(Modify the GPIO pin in the code if you use a different setup.)*

---

## 📦 Software Requirements

### Arduino IDE Setup
1. Install [Arduino IDE](https://www.arduino.cc/en/software).
2. Add **ESP8266 board support** via:

File → Preferences → Additional Board Manager URLs:
http://arduino.esp8266.com/stable/package_esp8266com_index.json

markdown
Copy code
3. Open **Board Manager** → install **ESP8266 by ESP8266 Community**.
4. Select your board:  
`Tools → Board → NodeMCU 1.0 (ESP-12E Module)`

---

## 🧩 Required Libraries

Install the following libraries via **Library Manager**:

- `ESP8266WiFi`
- `WiFiClientSecure`
- `UniversalTelegramBot`
- `NTPClient`
- `WiFiUdp`
- `TimeLib`

---

## 🔧 Configuration

Before uploading the sketch:

1. Open `wifi_pump_relay_v2.ino`
2. Edit these lines with your credentials:

```cpp
const char* ssid = "YOUR_WIFI_NAME";
const char* password = "YOUR_WIFI_PASSWORD";
String botToken = "YOUR_TELEGRAM_BOT_TOKEN";
String chat_id = "YOUR_TELEGRAM_CHAT_ID";
