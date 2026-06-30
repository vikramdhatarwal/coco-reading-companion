# 🐧 Coco — Audio-First Reading Companion for Children

> An intelligent AI-powered interactive storytelling and child learning assistant integrating OCR, Speech Recognition, Large Language Models, and Text-to-Speech on Raspberry Pi.

**📄 Patent Filed** — PDPM IIITDM Jabalpur (May 2026)  
**🎥 Demo Video** — https://drive.google.com/file/d/16WOyCq2WRZY4sbawVn-ueAsFg3jLp1Nj/view?usp=sharing
**🔒 Note:** Full source code is withheld pending IP inspection by the institute. This repository contains architecture documentation and system design.

---

## 📌 What is Coco?

Coco is a voice-first educational device built for children that can:

- **Read physical storybooks aloud** using a camera + OCR pipeline
- **Answer children's questions** in real time using conversational AI
- **Narrate stories in multiple languages** (English + Hindi demonstrated)
- **Switch between modes** (Storytelling / Narration / Bluetooth) via physical buttons
- **Filter unsafe content** through child-safe guardrails before responding
- Allow **parents to manage content** wirelessly via a companion app

It runs entirely on a **Raspberry Pi 4B** — no screen required for the child.

---

## 🎥 Demo

[![Coco Demo](https://img.shields.io/badge/Demo-Watch%20on%20YouTube-red?style=for-the-badge&logo=youtube)](#)  
*(replace `#` with your YouTube unlisted link)*

**Features demonstrated in the video:**
- Live conversational interaction ("Hello, how are you?")
- Physical storybook reading via OCR → TTS pipeline
- Hindi story narration in Bluetooth audio mode
- Physical button mode switching

---

## 🏗️ System Architecture

### End-to-End Pipeline

```
📷 Camera (Pi Camera v2)
        ↓
🔍 OCR Engine (Google Vision API / EasyOCR / Tesseract)
        ↓
🧹 AI Text Cleaning & Enhancement
        ↓
🤖 LLM Processing (Gemini 2.5 Flash Lite)
        ↓
🛡️ Child-Safe Guardrails (SHAP + TinyLlama Intent Classifier)
        ↓
🔊 Text-to-Speech (TTS) → Speaker Output
        ↑
🎙️ Microphone (INMP441) → Speech-to-Text (STT) → Child Voice Input
```

### 7-Stage Processing Pipeline

| Stage | Module | Function |
|---|---|---|
| 1 | Image Acquisition | Pi Camera captures storybook pages |
| 2 | OCR Processing | Extracts text from captured images |
| 3 | Text Enhancement | AI cleans and formats OCR output |
| 4 | Story Narration | TTS converts text to child-friendly audio |
| 5 | Voice Interaction | STT captures and processes child's voice |
| 6 | AI Response Generation | Gemini LLM generates contextual answers |
| 7 | Safety Filtering | Guardrails validate response before playback |

---

## 🔧 Hardware Components

| Component | Specification | Purpose |
|---|---|---|
| Central Processing Unit | Raspberry Pi 4B (4GB RAM) | AI orchestration and inference |
| Camera | Pi Camera Module v2 (8MP, IMX219) | Storybook image capture |
| Microphone | INMP441 MEMS (I2S interface) | Child voice input |
| Audio Amplifier | MAX98357 I2S Class-D | Audio output processing |
| Speakers | 40mm 4Ω 5W full-range | Story narration playback |
| Storage | 32GB microSD | OS, app, and story content |
| Power | 15000mAh rechargeable battery | Portable operation |
| Display | SPI Round Display Modules | Emotion animation |
| Controls | Physical push buttons | Mode switching |

---

## 🤖 Software & AI Stack

| Component | Technology |
|---|---|
| AI / LLM Framework | Google Gemini API (`google-generativeai` SDK) |
| Conversational Model | Gemini 2.5 Flash Lite |
| OCR Engine | Google Vision API / EasyOCR / Tesseract |
| Speech-to-Text | STT Processing Pipeline |
| Text-to-Speech | TTS Synthesis Engine |
| Safety Guardrails | SHAP + TinyLlama Intent Classifier |
| Camera Interface | OpenCV (`cv2`), Pi Camera Interface |
| Operating System | Raspberry Pi OS |
| Environment Config | `python-dotenv` |
| Display / Animation | SPI Display Interface |

---

## ✨ Key Features

### 🎙️ Voice-First Interaction
Children interact entirely through speech — no typing, no screen dependency. The STT module captures voice input and the TTS module responds in natural audio.

### 📖 Physical Book Reading
The Pi Camera captures real storybook pages. OCR extracts the text, AI enhances readability, and TTS narrates it aloud — making any physical book an audiobook instantly.

### 🛡️ Child-Safe Guardrails
Every AI-generated response passes through a two-layer safety system:
- **Rule-based keyword filtering** for instant unsafe content blocking
- **TinyLlama intent classifier** for contextual safety validation
- SHAP-based explainability for guardrail decisions

### 🌐 Multilingual Narration
Demonstrated with English storybooks and Hindi stories via Bluetooth audio mode.

### 📱 Parent Companion App
Parents can wirelessly manage story content, monitor usage, download new stories, and adjust interaction settings without touching the device.

### 🔄 Offline Capability
Core processing runs locally on Raspberry Pi — works without internet for basic narration.

---

## 🔌 Operating Modes

| Mode | Trigger | Function |
|---|---|---|
| Storytelling Mode | Physical button | OCR reads physical book aloud |
| Interactive Q&A Mode | Child voice input | Real-time question answering during narration |
| Bluetooth Mode | Physical button | Streams narration to Bluetooth audio device |

---

## 📊 IP & Research

- **Title:** An Audio-First Reading Companion For Children
- **Filing Status:** Patent Draft Filed — PDPM IIITDM Jabalpur (April 2026)
- **Technology Domain:** AI, Educational Technology, Speech Processing, Embedded Systems
- **CPC Classification:** G06F 40/00 | G10L 15/22 | G10L 13/00 | G06V 30/10
- **Inventors:** Dr. Tripti Singh, Vikram Dhatarwal, Ambuj Gupta, Akshat Neema, Jorige Sriprada, Tanvisha Reddy, Bhavesh Chawre
- **Assignee:** PDPM IIITDM Jabalpur

---

## ⚠️ Known Limitations

- OCR accuracy is sensitive to lighting conditions — performance improves significantly under controlled/bright lighting
- Child-safe guardrail live demo not included in public video as the device is currently under institutional IP inspection
- Response latency depends on Wi-Fi connectivity for Gemini API calls

> *Radical honesty about limitations is a core engineering value of this project.*

---

## 👨‍💻 Authors

**Vikram Dhatarwal** — B.Tech Smart Manufacturing, PDPM IIITDM Jabalpur  
[GitHub](https://github.com/vikramdhatarwal) · [LinkedIn](#) *(add your link)*

*Built as part of academic research at PDPM IIITDM Jabalpur under the guidance of Dr. Tripti Singh.*

---

## 📄 License

This project is protected under a pending patent filed at PDPM IIITDM Jabalpur. Source code is not publicly available during the IP review period.
