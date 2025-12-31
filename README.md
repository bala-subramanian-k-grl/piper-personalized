# Piper TTS – Personalized Speech Learning System

This repository extends **Piper TTS** by adding:
- User-specific voice learning  
- Speaking pattern modeling  
- Stress and pitch modeling  
- Emotion-aware TTS modification  
- Personalized voice profiles (JSON/YAML)  
- A full CLI for training and synthesis  

### 📁 Documentation  
All detailed docs are inside the `docs/` folder:
- DATASET_ANALYSIS.md  
- ARCHITECTURE.md  
- DIAGRAMS.md  
- LOGS.md  
- CHANGELOG.md  

### 🚀 Quick Start

#### 1. Train personalized profile

🚀 Setup & Execution Guide

Follow the steps below to install dependencies, train a personalized voice profile, and generate personalized speech.

 1. Clone the Repository
git clone https://github.com/Prakashm28/piper-personalized.git
cd piper-personalized

 2. Create Virtual Environment
Windows (PowerShell):
python -m venv .venv
.venv\Scripts\Activate.ps1

 3. Install Dependencies
pip install -r requirements.txt

 4. Download a Piper Model

Choose a voice model (example: Amy – US English).

Download both files:

1️⃣ Model (.onnx)
2️⃣ Config (.json)

From:
https://huggingface.co/rhasspy/piper-voices/tree/main/en/en_US/amy/medium

Place them inside:

piper_base/
    en_US-amy-medium.onnx
    en_US-amy-medium.onnx.json

🎤 5. Add User Training Audio

Place your WAV file inside:

samples/user_audio/

Example:

samples/user_audio/testaudio1.wav

 6. Train a Personalized Voice Profile
python main.py train --user_audio samples/user_audio/testaudio1.wav --user_id prakash


This will:

✔️ Preprocess audio
✔️ Extract prosody & emotion features
✔️ Learn patterns
✔️ Create a profile JSON

Result saved in:

profiles/prakash_profile_YYYYMMDD.json

7. Generate Personalized Speech
python main.py synthesize --text "Hello, this is my personalized voice." --profile profiles/prakash_profile_xxx.json


Result saved as:

output.wav
