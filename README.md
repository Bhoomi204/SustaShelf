# ♻️ SustaShelf — Smart Scrap Management Platform

> An AI-powered smart waste-management platform designed to automate **scrap identification, valuation, and collection**.

SustaShelf aims to simplify the process of recycling and scrap collection by combining **computer vision, real-time metal pricing, predictive analytics, and automated communication** into a single ecosystem.

The project is organized into multiple modules, each responsible for a specific part of the scrap-management workflow.

---

## 🚀 Project Overview

Traditional scrap collection often involves manual identification of recyclable materials, uncertain pricing, and fragmented communication between customers and scrap collectors.

**SustaShelf** addresses these challenges by exploring an automated workflow:

```text
                   ┌──────────────────────┐
                   │       User           │
                   │  Uploads Scrap Image │
                   └──────────┬───────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │    AI Detection      │
                   │      YOLOv8          │
                   └──────────┬───────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │   Material & Qty.    │
                   │      Detection       │
                   └──────────┬───────────┘
                              │
                ┌─────────────┴─────────────┐
                ▼                           ▼
      ┌──────────────────┐        ┌──────────────────┐
      │  Live Pricing    │        │ Pickup Request   │
      │ MetalPriceAPI    │        │     Twilio       │
      └────────┬─────────┘        └────────┬─────────┘
               │                           │
               └─────────────┬─────────────┘
                             ▼
                    ┌─────────────────┐
                    │ Estimated Scrap │
                    │      Value      │
                    └─────────────────┘
```

A separate **Predictive Metal Pricing** module extends the platform with future-oriented price analytics.

---

# 🧩 Project Modules

## 🤖 1. ScrapBot — AI Scrap Detection & Collection

ScrapBot is an intelligent chatbot designed to automate scrap identification, price estimation, and pickup requests.

### Key Features

* 📸 Upload scrap images through the chatbot
* 🧠 Detect recyclable materials using a custom-trained **YOLOv8 model**
* 🔢 Identify detected material types and quantities
* 💰 Fetch current metal prices using **MetalPriceAPI**
* 🧮 Calculate estimated scrap value
* 📍 Capture user pickup location
* 🕒 Capture preferred pickup time
* 📩 Send pickup requests through **Twilio SMS**

### Workflow

```text
User
 │
 │ Upload Image
 ▼
Node.js / Express
 │
 │ Image
 ▼
Flask ML API
 │
 │ YOLOv8 Inference
 ▼
Detected Materials
 │
 │ Material + Quantity
 ▼
MetalPriceAPI
 │
 ▼
Price Calculation
 │
 ▼
User Confirmation
 │
 ▼
Twilio SMS
 │
 ▼
Scrap Collector
```

### Example

```text
Detected Scrap:

metal: 2 × ₹58.10 = ₹116.20
tin:   1 × ₹70.42 = ₹70.42

Total Estimated Value: ₹186.62
```

### Technology

| Component        | Technology            |
| ---------------- | --------------------- |
| Frontend         | HTML, CSS, JavaScript |
| Backend          | Node.js, Express      |
| ML API           | Python, Flask         |
| Object Detection | YOLOv8 / Ultralytics  |
| Pricing          | MetalPriceAPI         |
| Communication    | Twilio SMS            |

### Repository

👉 **[View ScrapBot Repository](https://github.com/Bhoomi204/smart-recycle-chatbot)**

---

# 📈 2. Predictive Metal Pricing

The predictive analytics module focuses on forecasting future prices of major industrial metals.

### Supported Metals

* Lithium
* Copper
* Nickel
* Aluminum
* Cobalt

### Key Features

* 📊 Time-series forecasting using **Prophet**
* 🔮 Six-month future price forecasting
* 📈 Interactive Streamlit dashboard
* ⚖️ Multi-metal comparison
* 🏆 Identification of the highest-value projected metal
* 🧩 Modular design for future integration with real datasets

### Forecasting Workflow

```text
Historical / Synthetic Data
            │
            ▼
     Data Preparation
            │
            ▼
      Prophet Model
            │
            ▼
    Future Date Generation
            │
            ▼
     6-Month Forecast
            │
            ▼
   Streamlit Visualization
            │
            ▼
   Metal Comparison & Ranking
```

### Technology

| Component       | Technology       |
| --------------- | ---------------- |
| Language        | Python           |
| Forecasting     | Facebook Prophet |
| Data Processing | Pandas           |
| Visualization   | Matplotlib       |
| Dashboard       | Streamlit        |

### Repository

👉 **[View Predictive Metal Pricing Repository](https://github.com/Bhoomi204/predictive-demand-analysis)**

> **Note:** The current forecasting implementation uses synthetic data for demonstration. It is structured to support replacement with real historical or database-backed pricing data.

---

# 🏗️ Overall Architecture

SustaShelf is designed as a modular ecosystem where individual services can be independently developed and integrated.

```text
                         SUSTASHELF
                             │
              ┌──────────────┴──────────────┐
              │                             │
              ▼                             ▼
        ┌───────────┐              ┌──────────────────┐
        │ ScrapBot  │              │ Predictive       │
        │           │              │ Metal Pricing    │
        └─────┬─────┘              └────────┬─────────┘
              │                             │
       ┌──────┼───────┐                     │
       │      │       │                     │
       ▼      ▼       ▼                     ▼
    YOLOv8  Pricing  Twilio              Prophet
       │      API      │                     │
       └──────┴────────┘                     │
              │                              │
              ▼                              ▼
       Scrap Valuation              Future Price Analytics
```

---

# 👩‍💻 Contributions

The following modules were independently developed as part of the SustaShelf project:

### ScrapBot

* Developed the AI-powered scrap detection workflow using a custom YOLOv8 model.
* Built the Flask-based ML inference API.
* Developed Node.js/Express backend integration.
* Integrated MetalPriceAPI for dynamic metal pricing.
* Implemented scrap-value calculation based on detected material and quantity.
* Integrated Twilio SMS for automated pickup notifications.
* Implemented collection of pickup location and preferred pickup time.

### Predictive Metal Pricing

* Developed the Prophet-based time-series forecasting module.
* Implemented six-month future price prediction for multiple metals.
* Built the Streamlit dashboard for forecast visualization and comparison.
* Implemented future-value ranking across supported metals.
* Designed the module for future integration with real historical pricing sources.

---

# 🛠️ Technology Stack

### AI / Machine Learning

* Python
* YOLOv8
* Ultralytics
* Prophet

### Backend

* Node.js
* Express.js
* Flask
* REST APIs

### Frontend

* HTML
* CSS
* JavaScript
* Streamlit

### External Services

* MetalPriceAPI
* Twilio
* OpenAI API *(optional)*

### Development Tools

* Git
* GitHub
* VS Code

---

# 📂 Repository Structure

The SustaShelf repository acts as the central project repository and provides links to the independently maintained modules.

```text
SustaShelf/
│
├── README.md
│
├── ScrapBot
│   └── External Repository
│
└── Predictive-Metal-Pricing
    └── External Repository
```

---

# 🔮 Future Improvements

The platform can be extended with:

* 🔗 Integration of ScrapBot and predictive pricing into a unified application
* 🗄️ Real-time database for scrap transactions and pricing history
* 📊 Historical metal-price data pipeline
* 📉 Forecast evaluation using MAE, RMSE, and MAPE
* ☁️ Cloud deployment of ML and backend services
* 🔐 User authentication and secure pickup management
* 🗺️ Map-based scrap collector assignment
* 📱 Dedicated mobile application
* 🔔 Automated notifications for pickup status
* 📈 Historical analytics for scrap prices and collection trends

---

# ⚙️ Running the Modules

Each module currently has its own setup and deployment instructions.

### ScrapBot

See the dedicated repository:

👉 **[ScrapBot Setup & Documentation](https://github.com/Bhoomi204/smart-recycle-chatbot)**

### Predictive Metal Pricing

See the dedicated repository:

👉 **[Predictive Pricing Setup & Documentation](https://github.com/Bhoomi204/predictive-demand-analysis)**

---

# 📌 Project Status

| Module                           | Status         |
| -------------------------------- | -------------- |
| AI Scrap Detection               | ✅ Developed    |
| ScrapBot                         | ✅ Developed    |
| Dynamic Metal Pricing            | ✅ Developed    |
| SMS Pickup Requests              | ✅ Developed    |
| Predictive Metal Pricing         | ✅ Developed    |
| Unified Platform Integration     | 🔄 Future Work |
| Real Historical Pricing Pipeline | 🔄 Future Work |
| Cloud Deployment                 | 🔄 Future Work |

---

# 📄 License

This project is intended for academic and educational purposes.

---

## 👥 Contributors

**SustaShelf Project Team**

Developed as a collaborative project exploring AI-assisted smart waste management.

---

⭐ If you find this project interesting, consider giving the repository a star!
