# ♻️ SustaShelf | Smart Scrap Management & AI Valuation Platform

**SustaShelf** is an end-to-end AI-powered circular economy ecosystem designed to digitize scrap waste identification, valuation, collection, and commodity price forecasting. By combining computer vision, real-time metal spot rates, automated SMS logistics, and time-series market forecasting, SustaShelf bridges the gap between individual recyclers, local scrap collectors (*Kabadiwalas*), and industrial buyers.

---

## 🏗️ Unified Ecosystem Architecture

SustaShelf operates across two core micro-systems: an **Operational Collection Engine (ScrapBot)** for real-time transactions, and a **Strategic Market Engine (Predictive Analytics)** for long-term commodity price intelligence.

```
                                  ┌──────────────────────────────┐
                                  │      SUSTASHELF PLATFORM     │
                                  └──────────────┬───────────────┘
                                                 │
                  ┌──────────────────────────────┴──────────────────────────────┐
                  ▼                                                             ▼
┌──────────────────────────────────────────┐               ┌──────────────────────────────────────────┐
│  MODULE 1: ScrapBot (Operational Engine) │               │ MODULE 2: Strategic Pricing Intelligence │
├──────────────────────────────────────────┤               ├──────────────────────────────────────────┤
│ • Custom YOLOv8 Waste Vision Detection   │               │ • Prophet Time-Series Forecasting        │
│ • Live Spot Pricing via MetalPriceAPI    │               │ • 6-Month Industrial Metal Projections   │
│ • Automated Dispatch via Twilio SMS      │               │ • Interactive Streamlit Analytics UI     │
└──────────────────────────────────────────┘               └──────────────────────────────────────────┘
```

### Complete End-to-End Workflow

```
[ User Uploads Scrap Photo ]
            │
            ▼
┌───────────────────────┐       ┌───────────────────────┐
│ Flask CV Inference    ├──────►│ YOLOv8 Model          │ (17-Class Waste Detection)
│ (custom_trained_api)  │       │ (best.pt)             │
└───────────┬───────────┘       └───────────────────────┘
            │
            ▼
┌───────────────────────┐       ┌───────────────────────┐
│ Dynamic Scrap         ├──────►│ MetalPriceAPI         │ (Real-Time Spot Rates)
│ Valuation Engine      │       │ (Live Market API)     │
└───────────┬───────────┘       └───────────────────────┘
            │
            ▼
┌───────────────────────┐       ┌───────────────────────┐
│ Node.js/Express       ├──────►│ Twilio SMS Dispatch   │ (Notifies Local Collector with
│ Dispatch Service      │       │ API                   │  Items, Location & Time)
└───────────────────────┘       └───────────────────────┘

───────────────────────────────────────────────────────────────────────────────────

┌───────────────────────┐       ┌───────────────────────┐       ┌───────────────────────┐
│ Prophet Time-Series   ├──────►│ 6-Month Trend         ├──────►│ Streamlit Dashboard   │
│ Predictive Engine     │       │ Forecasting ($Cu,Al$) │       │ Interactive Analytics │
└───────────────────────┘       └───────────────────────┘       └───────────────────────┘
```

---

## 🧩 Core Ecosystem Modules

### 🤖 1. ScrapBot — AI Scrap Detection & Automated Collection
ScrapBot is the front-line operational chatbot interface that enables users to turn household and industrial scrap into instant valuation and schedule automated pickups.

* **Computer Vision Pipeline:** Powered by a custom-trained **YOLOv8m** model trained on a 17-class waste dataset (*cardboard, tin cans, plastic, copper wires, stainless steel, car body, etc.*) achieving **$42.4\%$ mAP@50** at $\sim 10.5\text{ ms}$ inference speed.
* **Valuation Engine:** Pairs detected item counts directly with live metal market prices via **MetalPriceAPI** to yield itemized transparent estimates.
* **Logistics Dispatch:** Node.js backend formats pickup details (item list, estimated payout, pickup window, geolocation) and dispatches an automated SMS alert to registered scrap collectors using **Twilio Programmable SMS**.

👉 **[View ScrapBot Source Repository](https://github.com/Bhoomi204/smart-recycle-chatbot)**

---

### 📈 2. Predictive Metal Pricing & Market Analytics
The analytics engine empowers waste management businesses, recycling plants, and scrap aggregators with price trend intelligence to time bulk selling and optimize profit margins.

* **Supported Industrial Metals:** Lithium ($Li$), Copper ($Cu$), Nickel ($Ni$), Aluminum ($Al$), and Cobalt ($Co$).
* **Time-Series Forecasting:** Built using **Facebook Prophet** to forecast metal price trends over a 6-month horizon.
* **Interactive Intelligence Dashboard:** Built with **Streamlit** for multi-metal price comparisons, projection visualization, and identifying high-value metal trends.

👉 **[View ScrapBot Source Repository](https://github.com/Bhoomi204/predictive-demand-analysis)**

---

## 📊 AI Model Training & Performance

The vision model powering SustaShelf's core identification engine was fine-tuned on NVIDIA Tesla T4 GPUs using PyTorch and Ultralytics.

| Metric | Valuation / Result |
| :--- | :--- |
| **Model Architecture** | Fine-tuned YOLOv8 Medium (`yolov8m.pt`) |
| **Parameters / Complexity** | 25.8M parameters / 78.7 GFLOPs |
| **Classes Trained** | 17 Recyclable Classes |
| **Precision ($P$)** | $0.499$ |
| **Recall ($R$)** | $0.406$ |
| **mAP@50** | **$42.4\%$** |
| **mAP@50-95** | **$35.5\%$** |
| **Inference Speed** | $\sim 10.5\text{ ms / frame}$ |

### Key Class Accuracy Highlights ($mAP@50$)
* 📦 **Cardboard:** $83.1\%$
* 🔍 **Camera Lens:** $69.5\%$
* 🚗 **Car Body:** $66.6\%$
* 🥫 **Disposable Aluminium:** $63.5\%$
* 🛢️ **Tin Can:** $54.8\%$

---

## 🛠️ Complete Tech Stack

| Domain | Technologies Used |
| :--- | :--- |
| **Computer Vision & ML** | Python 3.11, Ultralytics YOLOv8, PyTorch, OpenCV, Roboflow |
| **Predictive Analytics** | Facebook Prophet, Pandas, NumPy, Matplotlib, Streamlit |
| **Backend Services** | Node.js, Express.js, Python Flask (REST APIs) |
| **Frontend Web** | HTML5, CSS3, JavaScript (Fetch API), Streamlit UI |
| **Cloud & APIs** | MetalPriceAPI, Twilio Programmable SMS, OpenAI API (Optional) |
| **DevOps & Tooling** | Git, GitHub, Dotenv |

---

## 📂 Ecosystem Directory Layout

```text
SustaShelf/
├── ScrapBot/                         # Module 1: Vision & Pickup Engine
│   ├── Detection model/
│   │   └── weights/
│   │       └── best.pt               # Trained YOLOv8 model weights
│   ├── bot.html                      # Interactive web interface
│   ├── custom_trained_api.py         # Flask ML & MetalPriceAPI server
│   ├── server.js                     # Express backend & Twilio dispatch
│   └── package.json
│
├── Predictive-Metal-Pricing/         # Module 2: Time-Series Market Engine
│   ├── app.py                        # Streamlit dashboard application
│   ├── forecasting.py                # Prophet model preparation & execution
│   └── requirements.txt
│
└── README.md                         # SustaShelf master documentation
```

---

## 🚀 Execution & Setup Guide

### 1. Prerequisites
* **Python:** Version 3.11 or higher
* **Node.js:** Version 18 or higher
* **Environment Configuration:** Create a `.env` file in the project root:

```env
PORT=3000
METAL_PRICE_API_KEY=your_metalprice_api_key
TWILIO_SID=your_twilio_account_sid
TWILIO_AUTH=your_twilio_auth_token
TWILIO_PHONE=your_twilio_virtual_phone
KABADIWALA_PHONE=collector_phone_number
```

### 2. Launching ScrapBot (Vision & Dispatch Services)

```bash
# Clone the main repository
git clone https://github.com/Bhoomi204/smart-recycle-chatbot.git
cd smart-recycle-chatbot

# Install Dependencies
npm install
pip install -r requirements.txt

# Start Flask ML Server (Port 5000)
python custom_trained_api.py

# In a new terminal, start Node Express Server (Port 3000)
node server.js
```
*Access ScrapBot at `http://localhost:3000/bot.html`*

### 3. Launching Predictive Metal Analytics Dashboard

```bash
# Navigate to Predictive Engine directory
cd Predictive-Metal-Pricing

# Install requirements
pip install -r requirements.txt

# Launch Streamlit App
streamlit run app.py
```
*Access Market Dashboard at `http://localhost:8501`*


---
*Developed as part of an end-to-end smart waste management and sustainability initiative.*
