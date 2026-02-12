# Quick Setup Guide - PoodleAI

Get your on-device AI assistant running in 5 minutes!

## Prerequisites

- ✅ Android device (Android 7.0+, 4GB+ RAM)
- ✅ At least 5GB free storage
- ✅ USB cable for model transfer (if downloading on PC)

## Step 1: Install the App

### Option A: Build from Source
```bash
# Clone repository
git clone <repository-url>
cd PoodleAI

# Open Android Studio
# Build & Run or use command line:
./gradlew installDebug
```

### Option B: Install APK
```bash
# Transfer and install APK
adb install PoodleAI.apk
```

## Step 2: Download a Model

### Recommended: Gemma 2B (Beginner-Friendly)

**Option 1: Direct Download on Android**
1. Open browser on your Android device
2. Go to: https://huggingface.co/google/gemma-2b
3. Download `gemma-2b-it-gpu-int4.bin`
4. Wait for download (file is ~1.2GB)
5. Note location: `/sdcard/Download/`

**Option 2: Download on PC, Transfer to Phone**
```bash
# Download using kagglehub (Python)
pip install kagglehub
python -c "import kagglehub; print(kagglehub.model_download('google/gemma/keras/gemma_2b_en'))"

# Transfer to Android
adb push gemma-2b-it-gpu-int4.bin /sdcard/Download/
```

**Option 3: Use ADB to check existing models**
```bash
# Check if you already have models on device
adb shell ls -lh /sdcard/Download/*.bin
```

## Step 3: Configure the App

1. **Open PoodleAI** - Settings dialog appears automatically
2. **Enter model path**:
   ```
   /storage/emulated/0/Download/gemma-2b-it-gpu-int4.bin
   ```
   Or browse using the file picker (if available)
3. **Select model type**: Choose "Gemma" from dropdown
4. **Tap "Load Model"** - Wait 30-60 seconds
5. **Success!** You'll see "Model loaded successfully"

## Step 4: Start Chatting

1. Type your message: "Hello!"
2. Press send ➤
3. Wait for response (first one takes longer)
4. Continue conversation naturally

### Example Prompts
- "Tell me a joke"
- "Explain quantum computing simply"
- "Write a haiku about cats"
- "What's 15% of 250?"

## Common Issues & Quick Fixes

### "Model file not found"
```bash
# Check actual path
adb shell ls -la /sdcard/Download/

# Or try alternative paths:
/storage/emulated/0/Download/gemma-2b-it-gpu-int4.bin
/sdcard/Download/gemma-2b-it-gpu-int4.bin
```

### "Model loading failed"
- ✅ Check file size (should be ~1-3GB)
- ✅ Re-download if file seems corrupted
- ✅ Verify .bin extension
- ✅ Restart app and try again

### "Storage permission denied"
1. Go to Settings > Apps > PoodleAI
2. Permissions > Files and media > Allow
3. Restart app

### App crashes on load
- Device may have insufficient RAM
- Try smaller model (Gemma 2B INT4)
- Close other apps before loading

## Performance Tips

### For Best Experience:
1. **First load**: Be patient (30-60 seconds normal)
2. **First response**: Takes longer (~10-30 seconds)
3. **Subsequent responses**: Much faster (~2-5 seconds)
4. **Close background apps**: Free up RAM
5. **Keep phone plugged in**: Model loading uses battery

### Optimize Settings:
In model settings, you can adjust:
- **maxTokens**: Lower = faster, shorter responses
- **temperature**: Lower = more focused responses

## Device Recommendations

| Device RAM | Recommended Model | Performance |
|------------|------------------|-------------|
| 4GB        | Gemma 2B INT4    | Good        |
| 6GB        | Gemma 2B INT8    | Better      |
| 8GB+       | Gemma 7B INT4    | Best        |

## Next Steps

Once you're comfortable:
1. ✅ Try different models (Mistral, Qwen)
2. ✅ Experiment with longer conversations
3. ✅ Test complex prompts
4. ✅ Share feedback!

## Getting Help

### Resources
- 📖 Full README: [README.md](README.md)
- 📥 Model Guide: [MODEL_DOWNLOAD_GUIDE.md](MODEL_DOWNLOAD_GUIDE.md)
- 🐛 Report issues: Create GitHub issue

### Quick Debug Commands
```bash
# Check app logs
adb logcat | grep PoodleAI

# Check storage space
adb shell df -h

# Check app info
adb shell dumpsys package com.example.poodleai
```

---

🎉 **Congrats! You're running AI entirely on your device!** 🎉

No internet required • Complete privacy • Lightning fast
