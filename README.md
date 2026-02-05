# Chatterbox Turbo TTS

High-quality text-to-speech app with voice cloning, multilingual support, and voice conversion. Supports 23 languages.

## Features

- **Turbo TTS** – Fast synthesis with paralinguistic tags (e.g. `[laugh]`, `[sigh]`)
- **TTS Main** – English TTS with full controls
- **Multilingual TTS** – 20+ languages (Arabic, Danish, German, Greek, English, Spanish, Finnish, French, Hebrew, Hindi, Italian, Japanese, Korean, Malay, Dutch, Norwegian, Polish, Portuguese, Russian, Swedish, Swahili, Turkish, Chinese)
- **Voice Conversion** – Convert existing audio to another voice
- **Clone Voice** – Create custom voices from your own audio samples

## Requirements

- **OS**: Windows 10/11 (64-bit), or Linux/macOS with Python
- **Python**: 3.8+
- **RAM**: 8 GB minimum (16 GB recommended)
- **Storage**: ~10 GB free (for models and cache)
- **GPU**: Optional; NVIDIA GPU with ≥5 GB VRAM recommended. Runs on CPU if no suitable GPU.

## Setup

### 1. Clone or download this project

Ensure you have the project folder with `app.py`, `modules/`, `src/`, and `requirements.txt`.

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

If you see **`torchvision::nms does not exist`**:

```bash
pip install torchvision==0.22.1
```

For **CPU-only** (no CUDA):

```bash
pip install torch==2.7.1 torchvision==0.22.1 torchaudio==2.7.1 --index-url https://download.pytorch.org/whl/cpu
```

### 3. (Windows) Optional one-click run

If you use the bundled Python in the `python/` folder:

- Double-click **`Run Chatterbox TTS.bat`**

Otherwise run the app with your own Python (see below).

## Run

**With your own Python:**

```bash
python app.py
```

The Gradio UI opens in your browser (default: `http://127.0.0.1:7860`).  
On first run, models are downloaded from Hugging Face (~5–15 minutes); they are cached for later runs.

**Custom port or network access:**

Edit the last line in `app.py` (e.g. around line 405):

```python
demo.queue().launch(server_name="0.0.0.0", server_port=8080, inbrowser=True)
```

Use `server_name="0.0.0.0"` to allow access from other devices on your network.

## Use

1. **Turbo TTS** – Enter text, choose a voice, use emotion buttons to insert tags, click **Generate Speech**.
2. **TTS Main** – English only. Set exaggeration, temperature, CFG, and seed; then generate.
3. **Multilingual TTS** – Pick language, enter text in that language, select voice, generate.
4. **Voice Conversion** – Upload audio (WAV recommended), choose target voice, click **Convert Voice**.
5. **Clone Voice** – Upload a clear reference clip (5+ seconds), name the voice, set language/gender, click **Clone Voice**. The new voice appears in all voice dropdowns.

Cloned voices are stored in `voice_samples/` (created automatically).  
Models are cached under `~/.cache/huggingface/` (or `C:\Users\<username>\.cache\huggingface\` on Windows).

## Troubleshooting

| Issue | What to do |
|-------|------------|
| Out of memory | Close other GPU apps; app may fall back to CPU if VRAM is low. |
| Models won’t download | Check internet and firewall; ensure write access to the Hugging Face cache directory. |
| App won’t start | Use Python 3.8+, run `pip install -r requirements.txt`, ensure port 7860 is free. |
| `torchvision::nms` error | Run `pip install torchvision==0.22.1`. |
| Slow generation | Normal on CPU (e.g. 10–30 s per sentence). Use GPU or Turbo TTS for speed. |
| Browser doesn’t open | Open `http://127.0.0.1:7860` manually, or set `inbrowser=False` in `app.py`. |

## Project structure

```
├── app.py                 # Entry point
├── requirements.txt      # Dependencies
├── Run Chatterbox TTS.bat # Windows launcher (uses python/ if present)
├── modules/
│   ├── config.py         # Language/config
│   ├── model_manager.py # Model load/unload
│   ├── generation_functions.py
│   ├── ui_components.py  # Gradio UI
│   └── voice_manager.py
├── src/chatterbox/       # TTS and voice conversion core
└── voice_samples/       # Cloned voices (created at runtime)
```

## Notes

- First run downloads models (~5–8 GB); internet required once.
- GPU with ≥5 GB VRAM is used when available; otherwise CPU.
- For Colab or cloud, run `app.py` and use Gradio’s share link or deploy behind a reverse proxy.

---

For issues, check the console output and the troubleshooting section above.
