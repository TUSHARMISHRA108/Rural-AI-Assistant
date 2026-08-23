# 🌾 Rural AI Assistant

**AI-powered agricultural assistant for farmers using text, voice, crop images, and multilingual support.**

## 🚜 Problem

Many farmers and rural users face difficulties getting quick and understandable agricultural guidance. Technical information can be difficult to access, especially for users who prefer speaking in their local language.

Rural AI Assistant provides a simple conversational interface where farmers can ask questions through **text, voice, or crop photographs** and receive practical AI-generated guidance.

## 💡 Solution

Rural AI Assistant combines:

* 🤖 **Google Gemini** for agricultural question answering and image analysis

* 🎤 **Faster-Whisper** for converting voice questions into text

* 🔊 **Edge-TTS** for generating spoken responses

* 📷 **Gemini Vision** for analyzing crop images

* 🌐 **Multilingual support** for Indian languages

* 📱 **Telegram** as the farmer-facing interface

The assistant is designed to use simple language and provide practical next steps rather than complicated technical explanations.

## ✨ Core Features

### 💬 Text-based farming assistance

Farmers can send agricultural questions through Telegram and receive AI-generated responses.

### 📷 Crop image analysis

Farmers can send a photograph of a crop.

The system attempts to:

1. Identify the crop

2. Describe visible symptoms

3. Identify possible disease, pest, nutrient deficiency, or other problems when visual evidence is sufficient

4. Provide a confidence level

5. Suggest practical next steps

6. Explain what should be avoided

The system is instructed not to claim a definite diagnosis when the image does not provide enough evidence.

### 🎤 Voice-based questions

Farmers can send voice messages.

The system:


Voice Message

&#x20;     ↓

Faster-Whisper

&#x20;     ↓

Text Transcription

&#x20;     ↓

Gemini

&#x20;     ↓

Agricultural Response

&#x20;     ↓

Text + Voice Response

### 🔊 Voice responses

The generated answer can also be converted into speech using Edge-TTS.

### 🌐 Multilingual support

The prototype supports:

* English

* Hindi

* Maithili

* Bengali

* Marathi

* Tamil

* Telugu

* Kannada

* Gujarati

* Punjabi

* Odia

* Malayalam

Users can select their preferred language using the /language command.

## 🧠 AI Workflow


&#x20;                        ┌─────────────────┐

&#x20;                        │     Farmer      │

&#x20;                        └────────┬────────┘

&#x20;                                 │

&#x20;                  ┌──────────────┼──────────────┐

&#x20;                  ↓              ↓              ↓

&#x20;               Text           Voice          Image

&#x20;                  │              │              │

&#x20;                  │        Whisper STT          │

&#x20;                  │              ↓              │

&#x20;                  │            Text             │

&#x20;                  └──────────────┼──────────────┘

&#x20;                                 ↓

&#x20;                        ┌─────────────────┐

&#x20;                        │ Google Gemini   │

&#x20;                        │       AI        │

&#x20;                        └────────┬────────┘

&#x20;                                 ↓

&#x20;                      Agricultural Guidance

&#x20;                                 │

&#x20;                         ┌───────┴───────┐

&#x20;                         ↓               ↓

&#x20;                      Text           Edge-TTS

&#x20;                                         ↓

&#x20;                                  Voice Response

## 🛠️ Technology Stack

| Technology | Purpose |

| ------------------- | ------------------------------------ |

| Python | Core application |

| Google Gemini | AI reasoning and crop image analysis |

| Faster-Whisper | Speech-to-text |

| Edge-TTS | Text-to-speech |

| Pillow | Image processing |

| python-telegram-bot | Telegram interface |

| PyTorch | Whisper model execution |

| Nest AsyncIO | Async execution support |

## 📁 Project Structure


rural-ai-assistant/

│

├── rural-ai-assistant.py

├── requirements.txt

├── .gitignore

└── README.md

## ⚙️ Installation

### 1. Clone the repository

git clone https://github.com/Mohit-analytics/rural-ai-assistant.git

cd rural-ai-assistant
### 2. Create a virtual environment

Windows:

python -m venv venv
Activate it:

venv\\Scripts\\activate
### 3. Install dependencies

pip install -r requirements.txt
## 🔑 API Keys

The application requires:

* Google Gemini API key

* Telegram Bot token

The application asks for these credentials at runtime instead of storing them directly in the source code.

GEMINI\_API\_KEY = getpass("Enter GEMINI\_API\_KEY: ")

TELEGRAM\_BOT\_TOKEN = getpass("Enter TELEGRAM\_BOT\_TOKEN: ")
**Never commit API keys, bot tokens, passwords, or other secrets to GitHub.**

## ▶️ Run the Application

Run:

python rural-ai-assistant.py
The application will ask for:


Enter GEMINI\_API\_KEY:

Enter TELEGRAM\_BOT\_TOKEN:

After successful initialization, the Telegram bot starts polling for messages.

Open Telegram and send:


/start

## 📱 Telegram Commands

### /start

Displays the welcome message and explains the available features.

### /language

Opens the language selection menu.

## 🌾 Example Usage

### Text


Farmer:

My wheat leaves are turning yellow. What should I do?

The assistant analyzes the question and provides possible causes and practical next steps.

### Image


Farmer → Crop photograph

&#x20;             ↓

&#x20;       Gemini Vision

&#x20;             ↓

&#x20;    Visible symptom analysis

&#x20;             ↓

&#x20;    Possible causes + guidance

### Voice


Farmer → Voice message

&#x20;             ↓

&#x20;       Faster-Whisper

&#x20;             ↓

&#x20;         Transcription

&#x20;             ↓

&#x20;          Gemini

&#x20;             ↓

&#x20;      AI response

&#x20;             ↓

&#x20;        Edge-TTS

&#x20;             ↓

&#x20;     Voice response

## 🛡️ Responsible AI Approach

The system is designed with several safety principles:

* It should not invent pesticide or fertilizer dosages.

* It should not claim certainty when an image is unclear.

* It provides a confidence level for image-based analysis.

* Chemical recommendations should follow verified agricultural guidance and product labels.

* It should acknowledge uncertainty when reliable information cannot be determined.

* It uses simple language suitable for rural users.

## 🚀 Scalability

The prototype can be extended beyond Telegram into:

* 🌐 Web applications

* 📱 Mobile applications

* 💬 WhatsApp-based interfaces

* ☎️ Voice-based agricultural helplines

* 🏪 Farmer support centers

* 🌾 Regional agricultural advisory systems

Future versions could integrate verified agricultural databases, weather information, mandi prices, government schemes, and localized crop advisory systems.

## 🔮 Future Improvements

Potential improvements include:

1. Integration with verified agricultural knowledge bases

2. Weather-aware spraying recommendations

3. Mandi price information

4. Government scheme information

5. More regional languages and dialects

6. Better crop disease detection using specialized agricultural models

7. Farmer-specific crop history

8. Offline or low-connectivity support

9. WhatsApp integration

10. Web/mobile farmer dashboard

## ⚠️ Current Limitations

This is a prototype. AI-generated agricultural guidance should not replace advice from qualified agricultural experts.

Image-based crop diagnosis can be affected by:

* Poor image quality

* Poor lighting

* Multiple symptoms

* Similar-looking diseases

* Missing context about crop age, soil, weather, and farming practices

The current prototype also depends on external AI and speech services.

## 🎥 Demo Video

**Demo:** *Add your final demo video link here*

The demonstration will show:

* Text-based agricultural assistance

* Crop image analysis

* Voice questions

* Voice responses

* Language selection

* End-to-end Telegram interaction

## 🏆 Hackathon Submission

### Prototype

**Live Prototype:** https://web.telegram.org/k/#@rural_ai_assistant_bot

### GitHub

https://github.com/Mohit-analytics/rural-ai-assistant

### Demo Video

**Demo Video:** *Add link here*

## 👨‍💻 Built For

Developed as an AI-for-agriculture prototype focused on making agricultural assistance more accessible to rural users through conversational AI, voice, images, and regional languages.

---

**🌾 Rural AI Assistant: Making AI-powered agricultural guidance simpler and more accessible.**
