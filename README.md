# 🎓 Smart Lecture Summarizer — AI-Powered Lecture to Notes


## 🧠 Overview

**Smart Lecture Summarizer** is an AI-powered web application that converts long lecture materials — text, PDFs, images, audio, and video — into concise structured notes and downloadable PDF summaries.

Built with a modular pipeline architecture using state-of-the-art NLP, OCR, and speech-to-text technologies.

---

## ✨ Features

| Input Type | Processing Method |
|---|---|
| 📄 Text / Markdown | Direct NLP summarization |
| 📑 PDF Handouts | PyPDF text extraction |
| 🖼️ Image Slides | OCR via PyTesseract + Pillow |
| 🎙️ Audio Lectures | Speech-to-text via OpenAI Whisper |
| 🎥 Video Lectures | Audio transcription + Keyframe OCR |

### Output
- ✅ Concise structured notes
- ✅ Key points extraction
- ✅ Downloadable PDF summary
- ✅ Graceful fallback if dependencies unavailable

---

## 🏗️ Architecture

```
User Upload (Web UI)
        │
        ▼
┌─────────────────────┐
│   Pipeline          │  ← Auto-detects input type
└────────┬────────────┘
         │
    ┌────┴────┐
    ▼         ▼
┌────────┐ ┌──────────────┐
│Extractor│ │ Input Types  │
│        │ │ • PDF        │
│        │ │ • Image/OCR  │
│        │ │ • Audio      │
│        │ │ • Video      │
└────┬───┘ └──────────────┘
     │
     ▼
┌─────────────────────┐
│   NLP Engine        │  ← HuggingFace Transformers
│   (Summarization)   │     Extractive fallback
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│   PDF Exporter      │  ← ReportLab
│   (Download Notes)  │
└─────────────────────┘
```

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.x |
| Web Framework | Flask |
| AI Summarization | HuggingFace Transformers (abstractive) |
| Fallback NLP | Extractive summarizer (offline) |
| Speech-to-Text | OpenAI Whisper |
| PDF Extraction | PyPDF |
| OCR | PyTesseract + Pillow |
| Video Processing | OpenCV + MoviePy |
| PDF Generation | ReportLab |
| Frontend | HTML, CSS |

---

## 📁 Project Structure

```
smart-lecture-summarizer/
│
├── app.py                  ← Flask entry point
├── requirements.txt        ← Python dependencies
├── style.css               ← Frontend styling
│
├── config/                 ← App configuration
├── extractor/              ← Input extraction modules
│   ├── pdf_extractor.py
│   ├── image_extractor.py
│   ├── audio_extractor.py
│   └── video_extractor.py
│
├── nlp_engine/             ← Summarization logic
│   ├── abstractive.py      ← HuggingFace transformer
│   └── extractive.py       ← Offline fallback
│
├── pipeline/               ← Auto-detection pipeline
│   └── pipeline.py
│
├── pdf_exporter/           ← PDF generation
│   └── exporter.py
│
└── templates/
    ├── base.html
    ├── index.html          ← Upload page
    └── result.html         ← Summary output page
```
## ⚙️ How It Works

```
Step 1 → Upload your lecture file via the web interface
Step 2 → Pipeline auto-detects the source type
Step 3 → Content extraction is applied:
          • PDF → text extraction
          • Image → OCR
          • Audio → Whisper transcription
          • Video → audio transcription + keyframe OCR
Step 4 → AI/NLP summarization generates concise notes
Step 5 → Download your summary as a PDF
```

---

## 🔬 Limitations & Future Work

### Current Limitations
- Transformer model loading requires internet on first run
- Large video files may take longer to process
- OCR accuracy depends on image/slide quality

### Future Work
- Add support for YouTube URL input
- Multilingual summarization
- Chapter-wise breakdown for long lectures
- Integration with LangChain for Q&A on lecture content

---



