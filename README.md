# 🩺 Intelligent Healthcare Assistant
### Multimodal AI for Early Symptom Analysis — Text, Voice & Image, All in One Conversation

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python&logoColor=white)
![Gradio](https://img.shields.io/badge/UI-Gradio-orange?logo=gradio&logoColor=white)
![Groq API](https://img.shields.io/badge/AI-Groq%20API-purple)
![ElevenLabs](https://img.shields.io/badge/Voice-ElevenLabs-black)
![Status](https://img.shields.io/badge/Status-Prototype-yellow)

> Talk to it, show it a photo, or type your symptoms — and get an AI-generated clinical-style response back, spoken out loud. Built to explore how far multimodal LLMs can go in making healthcare guidance more accessible.

---

## 💡 Why This Project Exists

Most people don't type their symptoms into a search bar and get a clear answer back — they get ten conflicting WebMD tabs. This project asks: **what if a patient could just *talk* to an AI, or send it a photo of a rash, and get a doctor-style response instantly, spoken back to them?**

That's exactly what this assistant does — it fuses **speech recognition, computer vision, and large language models** into a single conversational pipeline that feels less like a chatbot and more like a consultation.

---

## ✨ What It Can Do

| Capability | Description |
|---|---|
| 🗣️ **Voice Input** | Patient records a voice note describing symptoms — automatically transcribed to text via Groq's STT model |
| 📸 **Image Understanding** | Upload a photo (e.g. a skin condition) and Groq's vision model analyzes it alongside the transcribed query |
| 🧠 **AI Medical Reasoning** | The combined text + image input is interpreted by Groq's LLM, generating a structured, doctor-style response |
| 🔊 **Voice Output** | The response is converted back to natural, human-like speech using ElevenLabs, so the interaction feels like a real conversation |
| 🖥️ **Interactive UI** | Everything is wrapped in a clean Gradio web app — no setup needed for the end user beyond opening a browser |

---

## 🏗️ How It Works

The assistant takes **voice + image input from the patient** and turns it into a **spoken AI response**, powered by Groq's low-latency models on the reasoning side and ElevenLabs on the voice side — all orchestrated through a Gradio interface.

```
🎙️ Audio Recorder ──▶ 🧠 Speech-to-Text (Groq STT)
                                    │
                                    ▼
                        📝 Transcribed Text / User Query
                                    │
🖼️ Upload Image ───────────────────▶│
                                    ▼
                          👁️ Vision Model (Groq)
                                    │
                                    ▼
                            💬 LLM Response
                                    │
                                    ▼
                     🗣️ Text-to-Speech (ElevenLabs)
                                    │
                                    ▼
                          🔊 Audio Output File
```

**Flow, step by step:**
1. **Capture input** — the patient records their symptoms via the Audio Recorder and/or uploads an image (e.g. a photo of a visible symptom).
2. **Speech-to-Text** — Groq's STT model transcribes the audio into a text query.
3. **Vision + Reasoning** — the transcribed text and the uploaded image are passed together into Groq's Vision Model, which generates a doctor-style LLM response.
4. **Text-to-Speech** — the LLM response is converted into natural spoken audio using ElevenLabs' TTS model.
5. **Delivery** — the final audio output file is played back to the patient inside the Gradio web interface.

This maps directly to the codebase's four phases (`voice_of_the_patient.py` → `brain_of_the_doctor.py` → `voice_of_the_doctor.py` → `gradio_app.py`), each owning one stage of the pipeline — classic separation of concerns.

---

## 🛠️ Tech Stack

- **Language:** Python 3.11
- **Speech-to-Text:** [Groq API](https://groq.com/) STT model (transcribes patient audio to text)
- **Vision + LLM Reasoning:** Groq API vision-capable model (interprets transcribed text + uploaded image, generates the response)
- **Text-to-Speech:** [ElevenLabs](https://elevenlabs.io/) TTS model (natural, realistic voice output) — with gTTS supported as a lighter-weight alternative
- **Audio Tooling:** PortAudio (recording) + FFmpeg (processing)
- **UI / Deployment:** Gradio
- **Environment Management:** Pipenv / venv / Conda supported

---

## 🚀 Getting Started

### 1. Set up your environment
```bash
# Using venv
python -m venv venv
venv\Scripts\activate        # Windows
pip install -r requirements.txt
```
*(Pipenv and Conda instructions also available in the project guide — see `READme.txt`.)*

### 2. Install system dependencies
- **FFmpeg** — required for audio processing
- **PortAudio** — required for microphone input

### 3. Run the pipeline phase by phase
```bash
python voice_of_the_patient.py    # Phase 1: capture & transcribe speech (Groq STT)
python brain_of_the_doctor.py     # Phase 2: vision + LLM reasoning (Groq)
python voice_of_the_doctor.py     # Phase 3: text-to-speech (ElevenLabs)
python gradio_app.py              # Phase 4: launch the full web app
```

Once `gradio_app.py` is running, open the local URL in your browser, record your symptoms (or type them), optionally attach an image, and get a spoken AI response back.

---

## 📂 Project Structure

```
Intelligent-Healthcare-Assistant/
├── Source Code/                  # Core application code
├── intelligent healthcare assistant/
├── A13-FINAL-REPORT_.docx        # Full academic project report
├── Abstract.docx                 # Project abstract
├── Paper.docx                    # Research paper write-up
├── A13 PROJECT PPT.pptx          # Project presentation deck
├── Screen Recording.mp4          # Live demo walkthrough
└── READme.txt                    # Detailed setup guide
```

📹 **[Watch the demo](Screen%20Recording.mp4)** to see the assistant in action without setting anything up locally.

---

## 🎯 What This Project Demonstrates

For anyone reviewing this repo — here's the skill set behind it:

- Designing and integrating **multimodal AI pipelines** (text + speech + vision in one flow)
- Working with **LLM APIs** (Groq) for real-time inference beyond simple text completion
- Building **end-to-end audio pipelines** — capture, transcription, synthesis, playback
- Shipping a **usable interactive product** (Gradio) rather than just a notebook experiment
- Structuring a project into clean, testable, single-responsibility modules
- Documenting and presenting technical work formally (research paper, report, and presentation included)

---

## ⚠️ Disclaimer

This is an academic/portfolio project built to explore multimodal AI in healthcare contexts. It is **not a certified medical device** and its output should never be treated as professional medical advice or a diagnosis. Always consult a licensed healthcare provider for real medical concerns.

---

## 📬 Let's Connect

If you're a recruiter, hiring manager, or fellow builder and this caught your eye — I'd love to talk about the design decisions behind it, what I'd do differently at scale, or where I'm headed next.

**Asma Fariha** — [GitHub](https://github.com/asma-fariha1)
