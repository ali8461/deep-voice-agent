# 💊 Voice-Enabled Assistant

A conversational voice agent for a pharmacy business built using **Twilio**, **Deepgram**, **OpenAI GPT-4o**, and **ngrok**. It answers phone calls, processes speech in real time, and handles tasks such as checking drug info, placing orders, and looking up order status.

---

## 📦 Features

- 📞 Receive and handle voice calls via Twilio
- 🗣 Real-time transcription and speech via Deepgram
- 🧠 Intelligent responses and reasoning using OpenAI GPT-4o-mini
- 💊 Three core pharmacy functions:
  - `get_drug_info`
  - `place_order`
  - `lookup_order`
- 🔐 In-memory database (for prototyping)
- 🌐 Local tunneling with ngrok for development

---

## 🏗 Architecture Overview

```
Caller → Twilio → WebSocket → Your App
                        ↓
                  Deepgram STT
                        ↓
                    GPT-4o-mini
                        ↓
              [Function Call (if needed)]
                        ↓
                  Deepgram TTS → Caller
```

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/pharmacy-voice-agent.git
cd pharmacy-voice-agent
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Set Up Environment Variables

Create a `.env` file in the root directory:

```
DEEPGRAM_API_KEY=your_deepgram_api_key_here
```

### 5. Run ngrok (for Twilio webhook)

```bash
ngrok http 5000
```

Copy the forwarded HTTPS URL — you'll use it to configure Twilio.

---

## 🛠 Project Structure

```
.
├── main.py # Main server handling Twilio + Deepgram integration
├── pharmacy_functions.py # Functions for drug info, orders, and lookups
├── config.json # Agent configuration (Deepgram, OpenAI, etc.)
├── .env # Your Deepgram API key (not committed to repo)
├── pyproject.toml # Python project metadata and dependencies
├── logs-and-audios/ # Folder containing audio samples and server logs
│ ├── sample-conversation.m4a
│ └── sample-server-logs.txt
└── README.md # Project documentation

```

---

## 📁 Example Functions

The following functions are defined and callable by the agent:

### 🔍 get_drug_info

Fetch details about a drug (description, price, quantity).

### 🛒 place_order

Place an order for a given customer and drug.

### 📦 lookup_order

Check the status of an existing order using its ID.

---

## 📞 Twilio Setup

1. Buy a number in your [Twilio console](https://console.twilio.com).
2. Set its **Voice webhook URL** to your ngrok HTTPS URL (e.g. `https://abc123.ngrok.io`).
3. Ensure Twilio sends calls to your server via WebSocket or TwiML.

---

## 🧪 Run the Server

```bash
python main.py
```

You should see:

```
Started server.
```

Now your voice agent is live and ready to answer calls.

---

## 📚 Technologies Used

- [Twilio](https://www.twilio.com/) – Telephony
- [Deepgram](https://www.deepgram.com/) – Real-time STT/TTS
- [OpenAI GPT-4o](https://openai.com) – AI agent intelligence
- [ngrok](https://ngrok.com) – Local server tunneling
- Python 3.8+

---

## ✅ To-Do / Enhancements

- [ ] Add persistent database (SQLite/PostgreSQL)
- [ ] Add SMS order confirmation via Twilio
- [ ] Add retry & clarification loops in agent logic
- [ ] Dockerize for deployment

---

