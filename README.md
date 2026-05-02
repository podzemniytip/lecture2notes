# lecture2notes
Automatically generate structured notes and executable code snippets from long video lectures (30+ min) using multimodal MiMo-V2.5 and multi-agent orchestration.
# 📹 Lecture2Notes — AI Agent for Video Lectures

> Automatically generate structured notes and executable code snippets from long video lectures (30+ min) using multimodal MiMo-V2.5 and multi-agent orchestration.

## 🔥 Problem

Students and developers waste hours manually transcribing, summarizing, and extracting code examples from educational videos. Existing tools either:
- Only transcribe speech (miss visual code blocks)
- Can't handle long context (1M tokens needed for full lecture)
- Don't link theory to code examples

## 🧠 Solution

**Lecture2Notes** is an open‑source agent that transforms lecture videos into high‑quality Markdown notes with executable code snippets.

### Core Logic (Multi‑Agent + Long CoT)

| Agent | Task |
|-------|------|
| **SpeechTranscriber** | Extract audio → transcribe with Whisper (handles 1h+). |
| **CodeRecognizer** | Detect code blocks on screen via OCR (timestamped). |
| **Summarizer** | Chain‑of‑Thought (10+ steps): identify key concepts → link code to theory → generate final notes. |

**Multi‑agent workflow:**
1. Agent 1 prepares raw transcript + code timestamps.
2. Agent 2 (MiMo‑V2.5 multimodal) processes video frames to extract code even from slides.
3. Agent 3 runs long CoT (1M token context) to produce coherent Markdown.
4. Agent 4 (syntax checker) validates extracted code snippets.

All orchestrated via **OpenClaw** and compatible with **MiMo API**.

## 🎯 Why MiMo Orbit Credits?

- Need to process **100+ real lectures** (total ~20M tokens) to build a test dataset.
- Compare MiMo‑V2.5‑Pro vs DeepSeek‑V4 on **GDPVal‑AA** and **ClawEval**.
- Credits allow free development before open‑sourcing the full pipeline.

## 🛠️ Tech Stack

- **MiMo‑V2.5** (multimodal, 1M context, MIT license)
- **OpenClaw** / **Claude Code** (agent orchestration)
- **Whisper** (speech‑to‑text)
- **PaddleOCR** / **EasyOCR** (on‑screen code extraction)
- **Obsidian** (target output format)

## 📦 Current Status

- [x] Architecture design & multi‑agent flow  
- [x] Mock terminal logs (see `/demo`)  
- [ ] Integration with MiMo API (waiting for credits)  
- [ ] Full pipeline on 100 lectures  
- [ ] Obsidian plugin release

## 🚀 Getting Started (after credits approved)

```bash
git clone https://github.com/yourusername/lecture2notes.git
cd lecture2notes
pip install -r requirements.txt
python main.py --video lecture.mp4 --output notes.md
