# MigraCRM 🏢

![Private](https://img.shields.io/badge/Code-Private%20%C2%B7%20Client%20Work-red?style=flat)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Google Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat&logo=google&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)

> **Full-stack CRM platform for immigration law call centers — with AI-powered call transcription, sentiment analysis, and automation.**

> ⚠️ This is a **portfolio showcase** — source code is proprietary and not included. This README documents the architecture and capabilities of the system.

---

## 🧩 The Problem

Immigration law firms relying on call centers faced:

- **No automatic call logging** — agents manually wrote notes after each call, often losing details
- **No caller history at hand** — agents had to dig through spreadsheets to recognize returning callers
- **No AI summaries** — supervisors couldn't quickly review call quality or outcomes
- **No sentiment tracking** — no visibility into caller frustration or satisfaction trends
- **Disconnected telephony** — the PBX system (Grandstream UCM) had no integration with any CRM

---

## 💡 The Solution

MigraCRM is a purpose-built CRM that connects directly to the PBX, automatically transcribes every call, generates AI summaries, and gives agents a full 360° view of each caller — without any manual data entry.

---

## 🏗️ Architecture

```
Grandstream UCM6304 PBX
        │  CDR + Recording APIs
        ▼
  [MigraCRM Backend]  ────────────────────────────────────────────┐
  Python · FastAPI                                                  │
        │                                                           │
        ├── faster-whisper ──► local speech-to-text transcription  │
        │                                                           │
        ├── Google Gemini 2.5 Flash ──► AI summaries, sentiment    │
        │                                                           │
        ├── PostgreSQL ──► call records, caller history, CDR data  │
        │                                                           │
        └── Hermes (Telegram Bot) ──► Ollama llama3.2 AI assistant │
                                                                    │
  [MigraCRM Frontend]  ◄──────────────────────────────────────────┘
  React 18 · TypeScript · Vite · Tailwind CSS
        │
        └── Callio Wave Add-in ──► browser extension overlay
```

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 📞 **Auto Call Transcription** | Every call is automatically transcribed using faster-whisper (local inference — no external API) |
| 🧠 **AI Summaries** | Google Gemini 2.5 Flash generates concise summaries and action items for each call |
| 😊 **Sentiment Analysis** | Caller emotional tone is classified per call and tracked over time |
| 📋 **CDR Records** | Full call detail records pulled directly from the Grandstream UCM6304 PBX |
| 👤 **Caller History** | Complete interaction history per caller — previous calls, summaries, notes |
| ✍️ **Agent Notes** | Agents can add structured notes and follow-up tasks after each call |
| 🔴 **Live Transcriptor Status** | Real-time indicator showing when a call is actively being transcribed |
| 🤖 **Hermes Bot** | Telegram AI assistant (Ollama llama3.2) for quick queries on caller data and call history |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | Python 3.12 · FastAPI · SQLAlchemy · SQLModel |
| **AI / Speech** | Google Gemini 2.5 Flash · faster-whisper (local Whisper) |
| **Telephony** | Grandstream UCM6304 PBX · CDR API · Recording API |
| **Frontend** | React 18 · TypeScript · Vite · Tailwind CSS |
| **Database** | PostgreSQL |
| **Bot** | Telegram Bot API · Ollama · llama3.2 |
| **Deployment** | Bare-metal AlmaLinux VPS · PM2 · Nginx |

---

## 🚀 Deployment

MigraCRM runs on a **bare-metal AlmaLinux VPS** with:
- **PM2** managing the FastAPI backend and Telegram bot as persistent processes
- **Nginx** as reverse proxy serving the React frontend and proxying API requests
- **Callio Wave Add-in** installed in agents' browsers for real-time summary overlays

---

## 📬 Contact

Source code is proprietary. For enquiries about a similar system for your business, reach out:

📧 [pablozam1931@gmail.com](mailto:pablozam1931@gmail.com)

---

*Part of the [deadlyrat](https://github.com/deadlyrat) portfolio — see also [Callio Wave Add-in](https://github.com/deadlyrat/callio-wave-showcase).*
