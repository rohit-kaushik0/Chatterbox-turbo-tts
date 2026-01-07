# 🚀 Google Colab Setup Guide for Chatterbox TTS

This guide will help you run Chatterbox TTS on Google Colab for free!

## 📋 Prerequisites

- Google account (for Google Colab access)
- Your Chatterbox TTS project files

## 🎯 Quick Start

### Option 1: Using GitHub Repository (Recommended)

1. **Push your code to GitHub:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/chatterbox-tts.git
   git push -u origin main
   ```

2. **Upload the notebook to Google Colab:**
   - Go to [Google Colab](https://colab.research.google.com/)
   - Click `File` → `Upload notebook`
   - Upload `Chatterbox_TTS_Colab.ipynb`

3. **Update the repository URL:**
   - In the notebook, find Step 2 (Clone Repository)
   - Replace `YOUR_USERNAME` with your actual GitHub username

4. **Run all cells:**
   - Click `Runtime` → `Run all`
   - Wait for setup to complete (~5-10 minutes)
   - Click the public URL when it appears

### Option 2: Manual Upload (No GitHub Required)

1. **Prepare your project:**
   - Create a ZIP file of your entire project folder
   - Include: `app.py`, `modules/`, `src/`, `requirements.txt`

2. **Upload to Colab:**
   - Go to [Google Colab](https://colab.research.google.com/)
   - Upload `Chatterbox_TTS_Colab.ipynb`
   - In Step 2, uncomment the "Alternative: Upload Files Manually" cell
   - Run that cell and upload your ZIP file

3. **Run the notebook:**
   - Run all remaining cells
   - Wait for the Gradio interface to launch

## ⚙️ Configuration

### Enable GPU (Highly Recommended)

1. Click `Runtime` → `Change runtime type`
2. Select `T4 GPU` under Hardware accelerator
3. Click `Save`

This will significantly speed up model loading and inference!

### Adjust Settings

You can modify these in the notebook:

- **Model download location**: Models are cached in `/root/.cache/huggingface/`
- **Gradio share link**: Set `share=True` for public URL (default)
- **Queue settings**: Adjust `max_size` and `concurrency_limit` as needed

## 📦 What Gets Installed

The notebook automatically installs:

- PyTorch 2.7.1 with CUDA support
- Gradio 5.44.1
- All Chatterbox TTS dependencies
- System packages (ffmpeg)

Total installation time: ~3-5 minutes

## 🎮 Using the Application

Once launched, you'll see a public URL like:
```
Running on public URL: https://xxxxx.gradio.live
```

Click this URL to access your TTS application from anywhere!

### Features Available:

1. **⚡ Turbo TTS** - Fast synthesis with paralinguistic tags
2. **🎤 TTS Main** - Advanced English TTS
3. **🌍 Multilingual TTS** - Multiple language support
4. **🔄 Voice Conversion** - Convert voices
5. **🧬 Clone Voice** - Clone custom voices

## ⚠️ Important Notes

### Session Limits

- **Free Colab**: ~12 hours max session time
- **GPU usage**: Limited hours per week
- **Files are temporary**: Download outputs before session ends!

### Saving Your Work

To save generated audio:
1. Right-click on the audio player
2. Select "Download"
3. Or use the download button in Gradio

### Keeping Session Alive

Colab disconnects after inactivity. To prevent this:
- Install [Colab Keep Alive](https://chrome.google.com/webstore/detail/colab-alive/eookkckfbbgnhdgcbfbicoahejkdoele) extension
- Or periodically interact with the notebook

## 🐛 Troubleshooting

### "Out of Memory" Error

**Solution:**
```python
# Restart runtime
Runtime → Restart runtime

# Or upgrade to Colab Pro for more RAM
```

### "Module Not Found" Error

**Solution:**
```python
# Re-run Step 1 (Install Dependencies)
# Make sure all cells complete without errors
```

### Models Won't Download

**Solution:**
1. Check internet connection
2. Verify HuggingFace Hub is accessible
3. Try running Step 4 again
4. Check if `token=False` is set (no authentication required)

### Import Errors

**Solution:**
```python
# Make sure project structure is correct:
# ├── app.py
# ├── modules/
# │   ├── config.py
# │   ├── generation_functions.py
# │   ├── model_manager.py
# │   ├── ui_components.py
# │   └── voice_manager.py
# └── src/
#     └── chatterbox/
#         ├── tts.py
#         └── tts_turbo.py
```

### Gradio Won't Launch

**Solution:**
```python
# Check if port is already in use
# Restart runtime and try again
# Make sure all previous cells ran successfully
```

## 🚀 Performance Optimization

### For Faster Loading:

1. **Pre-download models** (Step 4)
   - Run this cell first
   - Models will be cached for future use

2. **Use GPU runtime**
   - T4 GPU is free and fast
   - Significantly faster than CPU

3. **Reduce queue size**
   ```python
   demo.queue(max_size=10)  # Lower = less memory
   ```

### For Better Quality:

1. **Adjust generation parameters**
   - Temperature: 0.7-0.9 for more natural speech
   - CFG weight: 0.3-0.7 for better control

2. **Use high-quality voice samples**
   - 5+ seconds of clear audio
   - Minimal background noise

## 📊 Resource Usage

Typical resource consumption:

| Component | RAM | GPU Memory | Time |
|-----------|-----|------------|------|
| Setup | 2 GB | 0 GB | 3-5 min |
| Model Load | 4 GB | 3-4 GB | 1-2 min |
| Inference | 6 GB | 4-5 GB | 5-15 sec |

**Recommended**: Colab Pro for heavy usage

## 🔗 Useful Links

- [Google Colab](https://colab.research.google.com/)
- [Colab FAQ](https://research.google.com/colaboratory/faq.html)
- [HuggingFace Hub](https://huggingface.co/)
- [Gradio Documentation](https://gradio.app/docs/)

## 💡 Pro Tips

1. **Save notebook to Google Drive**
   - File → Save a copy in Drive
   - Your changes will persist

2. **Mount Google Drive for persistent storage**
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

3. **Monitor GPU usage**
   ```python
   !nvidia-smi
   ```

4. **Clear outputs to save space**
   - Edit → Clear all outputs

5. **Use keyboard shortcuts**
   - `Ctrl+Enter`: Run cell
   - `Shift+Enter`: Run cell and select next
   - `Ctrl+M B`: Insert cell below

## 🎉 You're All Set!

Enjoy using Chatterbox TTS on Google Colab!

For issues or questions, please open an issue on GitHub.

---

**Happy Synthesizing! 🎙️**
