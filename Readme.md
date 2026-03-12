# 🎙️ Voice Cloning System
**Clone any voice using Coqui XTTS-v2 — runs free on Google Colab**

---

## What Does This Project Do?

This notebook lets you **clone a voice from a short audio clip** and make it say anything you type. You upload 6–30 seconds of someone speaking, type a sentence, and the AI produces a new audio file in that person's voice.

It supports **17 languages** and runs entirely in Google Colab — no setup on your own computer required.

---

## How It Works (Simple Version)

```
Your audio clip (6–30 sec)  ──┐
                               ├──▶  XTTS-v2 Model  ──▶  Cloned voice .wav
Your typed text             ──┘
```

Under the hood, the model does three things:
1. **Reads your voice** — extracts tone, pitch, and accent into a voice "fingerprint"
2. **Reads your text** — breaks it down into the sounds that make up speech
3. **Combines both** — generates brand-new audio that sounds like your speaker saying your words

---

## Requirements

| What you need | Details |
|---|---|
| Google account | To use Google Colab (free) |
| Reference audio | 6–30 seconds, one speaker, no background noise |
| Audio format | `.wav`, `.mp3`, `.flac`, or `.ogg` |
| Runtime type | **T4 GPU** (free tier in Colab) |

> ⚠️ **CPU mode works but is very slow.** Always switch to GPU: Runtime → Change runtime type → T4 GPU

---

## Quick Start

1. Open the notebook in Google Colab
2. Switch to **T4 GPU** runtime
3. Run **Step 1** — checks your environment
4. Run **Step 2** — installs packages *(runtime will restart automatically)*
5. After restart, **skip Steps 1 & 2** — start from **Step 3**
6. Follow each step in order

---

## Step-by-Step Overview

| Step | What it does |
|---|---|
| Step 1 | Checks GPU and Python version |
| Step 2 | Installs all required packages (then auto-restarts) |
| Step 3 | Creates the project folder structure |
| Step 4 | Upload your reference audio file |
| Step 5 | Cleans and preprocesses the audio |
| Step 6A | Downloads and loads the XTTS-v2 model (~1.8 GB) |
| Step 6B | Synthesizes your first cloned voice output |
| Step 7 | Plays reference and cloned audio side-by-side |
| Step 8 | Shows waveform and spectrogram visualizations |
| Step 9 | Downloads the output files to your computer |
| Step 10 | Repeat with different text (model stays loaded — fast!) |
| Bonus | Launches a full Gradio web UI with a shareable public link |

---

## Tips for Best Results

- **Use clean audio** — the single biggest factor in quality. No music, echo, or crowd noise.
- **6–30 seconds is the sweet spot** — shorter clips work but sound less accurate.
- **One speaker only** — mixing voices in the reference clip confuses the model.
- **Match the language** — set `LANGUAGE = 'en'` (or whichever language matches the reference audio).
- **Longer text = longer wait** — on a T4 GPU, expect 10–30 seconds per synthesis.

---

## Supported Languages

English · Spanish · French · German · Italian · Portuguese · Polish · Turkish · Russian · Dutch · Czech · Arabic · Chinese · Japanese · Korean · Hindi

---

## File Structure (Created Automatically)

```
voice-cloning/
├── data/
│   ├── raw_audio/          ← your uploaded audio goes here
│   └── processed/          ← cleaned audio saved here by Step 5
└── outputs/                ← all generated .wav files saved here
```

---

## Tech Stack

| Tool | Role | Cost |
|---|---|---|
| [Coqui XTTS-v2](https://github.com/coqui-ai/TTS) | Voice cloning model | Free / open source |
| Google Colab | Cloud GPU runtime | Free (T4 GPU) |
| Gradio | Web UI | Free |
| librosa | Audio processing | Free |
| matplotlib | Waveform visualization | Free |

---

## Common Issues

**"NO GPU DETECTED"** → Go to Runtime → Change runtime type → select T4 GPU → reconnect

**"BeamSearchScorer was removed"** → The notebook handles this automatically in Step 6A

**"Audio is very short (<3s)"** → Upload a longer clip; short clips produce robotic output

**Gradio link not working** → The link is only active while the cell is running — don't stop it

---

## License & Ethics

This notebook uses [Coqui TTS](https://github.com/coqui-ai/TTS) under its open-source license.

**Please use voice cloning responsibly.** Only clone voices with the speaker's explicit permission. Do not use this to impersonate, deceive, or create misleading content.
