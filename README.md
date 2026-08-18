# 🍽️ Food Chatbot — AI-Powered Food Ordering Assistant

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/Dialogflow-FF9800?style=for-the-badge&logo=dialogflow&logoColor=white" alt="Dialogflow">
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL">
</p>

## 📌 Overview

**Food Chatbot** is a conversational food-ordering application that connects a web frontend, a **FastAPI backend**, **Dialogflow intent handling**, and a **MySQL database**.

The chatbot is designed to understand food-ordering requests and maintain an order during a conversation. Users can add items, remove items, complete an order, and track an existing order through conversational intents.

## ✨ Key Features

- 💬 Conversational food ordering through Dialogflow.
- ➕ Add one or more food items with quantities.
- ➖ Remove items from an in-progress order.
- 🧾 Complete an order and generate an order ID.
- 💰 Calculate the order total from the database.
- 📦 Track an order using its order ID.
- 🔌 FastAPI webhook for Dialogflow integration.
- 🗄️ MySQL persistence for order data and tracking status.
- 🖥️ Frontend served alongside the backend.

## 🏗️ Architecture

```text
User
  │
  ▼
Frontend / Chat Interface
  │
  ▼
Dialogflow
  │  Webhook request
  ▼
FastAPI Backend
  │
  ├── Intent Handlers
  │     ├── Add Item
  │     ├── Remove Item
  │     ├── Complete Order
  │     └── Track Order
  │
  ▼
MySQL Database
  └── Orders / Items / Tracking
```

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Python, FastAPI |
| Conversational AI | Dialogflow |
| Database | MySQL |
| API Server | Uvicorn |
| Frontend | HTML / CSS / JavaScript |
| Tunneling | ngrok for local webhook testing |

## 📁 Project Structure

```text
Food_chatbot/
│
├── backend/
│   ├── main.py
│   ├── db_helper.py
│   └── generic_helper.py
│
├── database/
├── frontend/
├── requirements.txt
└── README.md
```

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/ajithram2003/Food_chatbot.git
cd Food_chatbot
```

### 2. Create a virtual environment

**Windows:**

```bash
python -m venv .venv
.venv\Scripts\activate
```

**Linux/macOS:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

The current dependency file includes `fastapi[all]` and `mysql-connector-python`.

## 🗄️ Database Setup

The application requires a MySQL database containing the tables expected by `db_helper.py`.

1. Create/configure the MySQL database.
2. Import the database schema/data provided in the `database/` directory.
3. Configure the database connection used by the backend.
4. **Do not commit database passwords or other secrets to GitHub.** Use environment variables for local/production credentials.

## ▶️ Run the Backend

From the `backend` directory:

```bash
cd backend
uvicorn main:app --reload
```

The FastAPI server will normally be available at:

```text
http://127.0.0.1:8000
```

FastAPI's interactive API documentation is available at `/docs` when the server is running.

## 🌐 Dialogflow Webhook Testing

For local Dialogflow integration, the backend needs a publicly reachable HTTPS endpoint. A tunneling tool such as **ngrok** can be used during development.

```bash
ngrok http 8000
```

Use the generated HTTPS forwarding URL as the Dialogflow fulfillment/webhook endpoint.

> ngrok is intended here for local development/testing. Production deployments should use a proper HTTPS endpoint.

## 🔄 Supported Conversation Flow

```text
Start conversation
      ↓
Add food items
      ↓
Review current order
      ↓
Add / remove items
      ↓
Complete order
      ↓
Generate order ID
      ↓
Track order status
```

## 🔐 Security Notes

This repository is intended as a learning/project demonstration. Before production use:

- Move database credentials to environment variables or a secrets manager.
- Avoid hard-coded local file paths.
- Add authentication/authorization where required.
- Validate and sanitize external webhook input.
- Add structured error handling and monitoring.
- Use a production ASGI deployment configuration.

## 🚀 Future Improvements

- Add Docker support for the complete application.
- Add automated API tests with Pytest/Postman.
- Add authentication and customer order history.
- Improve conversational intent coverage.
- Add restaurant/menu management APIs.
- Deploy the application using a cloud platform.
- Add CI/CD and automated quality checks.

## 👨‍💻 Author

**Ajithram A S**  
MSc Data Science | Python | AI/ML | Software & Platform Engineering

- GitHub: https://github.com/ajithram2003
- Portfolio: https://ajithram2003.github.io/

---

⭐ If you find this project useful, consider giving the repository a star.
