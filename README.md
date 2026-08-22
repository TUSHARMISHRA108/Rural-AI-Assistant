# Rural-AI-Assistant
AI-powered multilingual agricultural assistant for farmers using Telegram, Gemini, Whisper and crop image analysis.
# 🌾 Rural AI Assistant

## 📌 Overview

An AI-powered multilingual agricultural assistant designed to help
farmers get practical information through a simple Telegram interface.

The prototype supports text, voice, and crop-image based interaction.

## 🎯 Problem Statement

Many farmers may have limited access to agricultural experts or may
find dedicated digital applications difficult to use.

The project explores whether a conversational AI assistant can provide
an easier interface for basic agricultural questions and crop-related
assistance.

## 💡 Solution

Rural AI Assistant allows a farmer to communicate through Telegram
using:

- Text questions
- Voice messages
- Crop photographs

The system processes the input using AI and returns an understandable
response.

## ✨ Key Features

- 💬 Agricultural question answering
- 🎤 Voice input
- 🗣️ Voice responses
- 📷 Crop image analysis
- 🌐 Multilingual interaction
- 🌱 Crop problem analysis
- 📱 Telegram-based interface

## 🏗️ System Architecture

```text
Farmer
   │
   ▼
Telegram Bot
   │
   ├── Text ──────────────┐
   │                      │
   ├── Voice → Whisper ───┤
   │                      ▼
   └── Image ────────→ Gemini AI
                          │
                          ▼
                    AI Response
                          │
                    ┌─────┴─────┐
                    ▼           ▼
                  Text        Edge-TTS
                    │           │
                    └─────┬─────┘
                          ▼
                        Farmer
🛠️ Technologies
Python
Google Gemini
Faster-Whisper
Edge-TTS
python-telegram-bot
Pillow
PyTorch
Google Colab for prototype development
📱 Interaction
Text
Farmer → "My rice leaves are turning yellow"
       → AI agricultural response
Voice
Farmer → Voice message
       → Whisper transcription
       → Gemini
       → Text + voice response
Image
Farmer → Crop photograph
       → Gemini vision analysis
       → Crop problem assessment
🔐 Security

API keys and Telegram bot tokens are stored as environment variables
and should never be committed to the repository.

🚧 Current Status

Working Prototype

The current prototype is implemented as a Telegram bot and is being
tested with text, voice, and crop-image interactions.

🔮 Future Roadmap
WhatsApp integration
More Indian regional languages
Weather-aware recommendations
Improved crop disease detection
Regional agricultural information
Larger-scale real-world testing
Production deployment
⚠️ Disclaimer

This project is an AI prototype and should not replace qualified
agricultural experts.

Chemical, pesticide, and fertilizer decisions should be verified
using official product labels and trusted agricultural guidance.

📦 Installation
pip install -r requirements.txt
🔑 Environment Variables

Create environment variables for:

GEMINI_API_KEY
TELEGRAM_BOT_TOKEN


👨‍💻 Author

Mohit Sharma, Tushar Kumar Mishra
