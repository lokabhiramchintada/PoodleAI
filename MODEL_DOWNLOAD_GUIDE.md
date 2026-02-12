# Model Download Guide

## Quick Start - Download Gemma 2B

The easiest way to get started is with the Gemma 2B model.

### Method 1: Using Kaggle (Recommended)

1. **Install kagglehub**:
   ```bash
   pip install kagglehub
   ```

2. **Download Gemma 2B**:
   ```python
   import kagglehub
   
   # Download latest version
   path = kagglehub.model_download("google/gemma/keras/gemma_2b_en")
   print("Model downloaded to:", path)
   ```

3. **Transfer to Android Device**:
   ```bash
   # Find the .bin file in the downloaded directory
   # Transfer using ADB
   adb push /path/to/gemma-2b-it-gpu-int4.bin /sdcard/Download/
   ```

### Method 2: Using Hugging Face

1. Visit: https://huggingface.co/google/gemma-2b
2. Click "Files and versions"
3. Download the quantized .bin file (look for `int4` or `int8` versions)
4. Transfer to your Android device

### Method 3: Using Android Browser

1. Navigate to a model hosting site on your Android device
2. Download directly to your device (easiest method!)
3. Note the download location (usually `/sdcard/Download/`)

## Model Recommendations by Device

### Budget Devices (4GB RAM)
- **Gemma 2B INT4** (~1.2 GB)
  - Path: `gemma-2b-it-cpu-int4.bin`
  - Best balance of speed and quality

### Mid-Range Devices (6-8GB RAM)
- **Gemma 2B INT8** (~2.5 GB)
  - More accurate than INT4
  - Still fast enough
  
- **Qwen 2.5B** (~2 GB)
  - Good multilingual support
  - Efficient performance

### High-End Devices (8GB+ RAM)
- **Gemma 7B INT4** (~4 GB)
  - Much more capable
  - Slower but better responses
  
- **Mistral 7B INT4** (~3.8 GB)
  - Excellent reasoning
  - Good for complex tasks

## Model Formats

### .bin (MediaPipe Format)
- ✅ Fully supported
- ✅ GPU accelerated
- ✅ Optimized for mobile
- Recommended for best performance

### .gguf (llama.cpp Format)
- ⚠️ Partial support
- Requires conversion
- Good for custom models

### .onnx (ONNX Format)
- ✅ Supported via ONNX Runtime
- Cross-platform
- Good compatibility

## Where to Place Models

The app can read models from these locations:

1. **Download Folder** (Easiest):
   ```
   /storage/emulated/0/Download/model.bin
   /sdcard/Download/model.bin
   ```

2. **App-Specific Directory**:
   ```
   /storage/emulated/0/Android/data/com.example.poodleai/files/models/
   ```

3. **Custom Location**:
   - Any location with read permissions
   - Use a file manager to navigate

## Converting Models

If you have a model in a different format:

### Convert GGUF to MediaPipe BIN:
```bash
# Install MediaPipe Model Maker
pip install mediapipe-model-maker

# Convert model (example)
python convert_to_mediapipe.py --input model.gguf --output model.bin
```

### Quantize Models:
```bash
# INT4 quantization (smallest, fastest)
python quantize.py --input model.bin --output model_int4.bin --bits 4

# INT8 quantization (balanced)
python quantize.py --input model.bin --output model_int8.bin --bits 8
```

## Troubleshooting

### Download Failed
- Check internet connection
- Verify enough storage space
- Try a different download source

### Transfer Failed
- Ensure USB debugging is enabled
- Check ADB connection: `adb devices`
- Try manual file transfer via USB

### Model Not Loading
- Verify file integrity (re-download if needed)
- Check file isn't corrupted (compare file sizes)
- Ensure correct format (.bin for MediaPipe)

## Additional Resources

- [Kaggle Models](https://www.kaggle.com/models)
- [Hugging Face Models](https://huggingface.co/models)
- [MediaPipe LLM Guide](https://developers.google.com/mediapipe/solutions/genai/llm_inference)
- [Model Quantization Guide](https://www.tensorflow.org/lite/performance/post_training_quantization)
