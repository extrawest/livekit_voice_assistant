# 🎙️ Voice-to-Voice Communication Assistant

[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)]()
[![Maintainer](https://img.shields.io/static/v1?label=Yevhen%20Ruban&message=Maintainer&color=red)](mailto:oleksandr.samoilenko@extrawest.com)
[![Ask Me Anything !](https://img.shields.io/badge/Ask%20me-anything-1abc9c.svg)]()
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
![Version](https://img.shields.io/badge/version-1.0.0-blue)

A production-ready voice assistant built with LiveKit for real-time communication and Flutter integration. Features custom Speech-to-Text (STT) and Text-to-Speech (TTS) implementations using local APIs for enhanced privacy and performance.




https://github.com/user-attachments/assets/6a3274ae-b697-41ca-a0a0-80386a75824b



## ✨ Features

Uploading Overview of ExtraWest Company (1).mp4…



-   **🗣️ Real-time Voice Communication**: Seamless voice interaction with AI assistant
-   **🏠 Local API Architecture**: Privacy-focused local processing
    -   Custom STT via Speeches AI API
    -   Custom TTS via Kokoro AI API
    -   Groq LLM integration for intelligent responses
-   **🛠️ Extended Capabilities**:
    -   🔍 Web search using Tavily API
    -   🌤️ Weather information retrieval
-   **⚡ Performance Optimized**:
    -   LiveKit real-time communication framework
    -   Silero VAD for precise voice activity detection
    -   Integrated noise cancellation

## 🔧 Prerequisites

-   Python 3.10 or higher
-   LiveKit server (local or cloud deployment)
-   Local STT API (Speeches AI)
-   Local TTS API (Kokoro AI)
-   Ollama running locally
-   Flutter SDK (for mobile app)

## 🚀 Quick Start

### 1. Backend Setup

Clone and configure the voice assistant backend:

```bash
git clone https://github.com/extrawest/livekit_voice_assistant.git
cd livekit_voice_assistant

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure environment
cp .env.example .env
```

### 2. Environment Configuration

Edit `.env` with your settings:

```env
# LiveKit Configuration
LIVEKIT_URL=ws://localhost:7880
LIVEKIT_API_KEY=devkey
LIVEKIT_API_SECRET=secret

# STT Configuration
STT_API_URL=your_stt_url

# LLM Configuration
GROQ_API_KEY=your-groq-api-key

# TTS Configuration
TTS_API_URL=your_tts_url
TTS_API_KEY=your-tts-api-key

# Optional Features
WEATHER_API_KEY=your-weather-api-key
TAVILY_API_KEY=your-tavily-api-key
```

### 3. Start the Backend

```bash
python main.py dev
```

### 4. Flutter Frontend Setup

Set up the mobile application:

1. Navigate to flutter/application folder
2. Create .env file, add your LIVEKIT_SANDBOX_ID=<your-sandbox-id>

```bash
# Clone Flutter frontend
git clone https://github.com/livekit-examples/voice-assistant-flutter
cd voice-assistant-flutter

# Install Flutter dependencies
flutter pub get

# Run the application
flutter run
```

### 5. LiveKit Cloud Setup

1. Create account at [LiveKit Cloud](https://cloud.livekit.io/)
2. Register your server
3. Update environment variables with your LiveKit credentials

## 🏗️ System Architecture

The application follows a modular architecture:

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│  Flutter App    │◄──►│   LiveKit        │◄──►│  Voice Assistant│
│  (Frontend)     │    │   (Real-time     │    │  (Backend)      │
└─────────────────┘    │   Communication) │    └─────────────────┘
                       └──────────────────┘
                                │
                    ┌───────────▼──────────┐
                    │   Local APIs         │
                    │ ┌─────────────────┐  │
                    │ │ STT (Speeches)  │  │
                    │ │ TTS (Kokoro)    │  │
                    │ │ LLM (Groq)      │  │
                    │ └─────────────────┘  │
                    └──────────────────────┘
```

### Core Components

-   **LiveKit Integration**: Manages real-time audio streaming and room connections
-   **Custom STT Module**: Converts speech to text using local Speeches AI API
-   **Custom TTS Module**: Generates natural speech from text via Kokoro AI API
-   **Groq LLM Processing**: Handles conversation logic and response generation
-   **Agent Controller**: Orchestrates conversation flow and tool integrations

## 🔍 Advanced Features

### Voice Activity Detection

Utilizes Silero VAD for accurate speech detection, reducing false triggers and improving conversation flow.

### Noise Cancellation

Built-in audio processing for cleaner voice interactions in various environments.

### Tool Integration

Extensible architecture supporting additional tools like Tavily web search and OpenWeather APIs.
