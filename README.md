# smart-lecture-summarizer
Smart Lecture Summarizer is a Python + AI/NLP web app that converts long lecture materials into concise notes and downloadable PDFs.

It supports:

Text and markdown lecture notes
PDF handouts
Image-based slides (OCR)
Audio lectures (speech-to-text)
Video lectures (audio transcription + keyframe OCR)
Tech Stack
Flask for the website
transformers (Hugging Face) for abstractive AI summarization
Extractive NLP fallback summarizer for offline robustness
openai-whisper for audio/video transcription
pypdf for PDF text extraction
Pillow + pytesseract for OCR
opencv-python + moviepy for video processing
reportlab for downloadable PDF notes
Project Structure
.
|-- app.py
|-- requirements.txt
|-- smart_lecture_summarizer
|   |-- config.py
|   |-- extractors.py
|   |-- nlp_engine.py
|   |-- pdf_exporter.py
|   `-- pipeline.py
|-- static
|   `-- styles.css
`-- templates
    |-- base.html
    |-- index.html
    `-- result.html
Setup
Create virtual environment and activate it.
Install Python dependencies:
pip install -r requirements.txt
Install system tools used by OCR/transcription:
Tesseract OCR (pytesseract depends on this binary)
FFmpeg (used by moviepy and whisper)
Run
python app.py
Then open: http://127.0.0.1:5000

How It Works
Upload lecture file from the website.
Pipeline auto-detects source type (text, PDF, image, audio, video).
Content extraction is applied:
PDF text extraction
OCR for images/slides
Audio transcription
Video audio + keyframe OCR
AI/NLP summarization generates concise notes and key points.
Summary is exported as a downloadable PDF.
Notes
If transformer model loading fails, the app automatically uses extractive NLP summarization.
If Whisper or OCR dependencies are missing, the app still runs and shows warnings in the result page.
