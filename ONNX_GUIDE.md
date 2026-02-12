# ONNX Model Integration Guide

## Current Status
Your GGUF model (qwen2-1_5b-instruct-q4_0.gguf) is **validated but not usable** for inference.
The app now supports ONNX models for **actual AI inference**.

## Quick Start: Use Pre-Converted ONNX Models

### Option 1: Download Small ONNX Models (Recommended)

Visit Hugging Face and search for pre-converted ONNX models:

**Recommended models for Android:**
- **TinyLlama-1.1B-Chat-v1.0-ONNX** (Small, fast)
- **microsoft/phi-2-onnx** (2.7B, high quality)  
- **Qwen/Qwen2-0.5B-Instruct-ONNX** (Very small)

**How to download:**
1. Go to https://huggingface.co/models
2. Search: "tinyllama onnx" or "phi onnx"
3. Download the `.onnx` file
4. Copy to your phone: `adb push model.onnx /sdcard/Download/`
5. Load in PoodleAI app

---

## Option 2: Convert Your GGUF Model to ONNX

### Prerequisites on PC:
```bash
pip install optimum[exporters] transformers torch onnx huggingface_hub
```

### Step 1: Download Original Model (Not GGUF)
```python
from huggingface_hub import snapshot_download

# Download the Qwen2 model (not quantized)
snapshot_download(
    "Qwen/Qwen2-1.5B-Instruct",
    local_dir="./qwen2-1.5b-original"
)
```

### Step 2: Convert to ONNX
```bash
# Convert using Optimum
optimum-cli export onnx \
    --model ./qwen2-1.5b-original \
    --task text-generation \
    --opset 14 \
    ./qwen2-onnx

# The output will be in ./qwen2-onnx/model.onnx
```

### Step 3: Optimize for Mobile (Optional but Recommended)
```python
from onnxruntime.quantization import quantize_dynamic, QuantType

# Quantize to INT8 for smaller size and faster inference
quantize_dynamic(
    "./qwen2-onnx/model.onnx",
    "./qwen2-onnx/model-int8.onnx",
    weight_type=QuantType.QUInt8
)
```

### Step 4: Transfer to Phone
```bash
adb push ./qwen2-onnx/model-int8.onnx /sdcard/Download/qwen2.onnx
```

### Step 5: Load in App
- Open PoodleAI
- Settings → Choose File
- Select the .onnx file
- Load Model

---

## What Works Now

### ✅ ONNX Models (.onnx)
- **Full ONNX Runtime integration**
- Real inference execution
- Input/output tensor processing
- Ready for AI responses (needs tokenizer)

### ⚠️ GGUF Models (.gguf)
- File validation only
- Shows guidance to convert
- No inference capability

---

## Next Steps for Full AI Responses

The ONNX inference is working, but needs these additions:

### 1. **Proper Tokenizer**
ONNX models need compatible tokenizers:
```kotlin
// Current: Simple word splitting
// Needed: BPE/WordPiece tokenizer matching the model

// Add to dependencies:
implementation("com.github.huggingface:tokenizers-android:0.13.4")
```

### 2. **Auto-regressive Generation**
Language models generate text token-by-token:
```kotlin
// Needed: Loop that:
// 1. Runs model with current tokens
// 2. Gets next token prediction  
// 3. Appends to sequence
// 4. Repeats until done
```

### 3. **Text Decoding**
Convert token IDs back to readable text using tokenizer vocabulary.

---

## Testing Your Setup

### With ONNX Model:
1. Load any .onnx file
2. Ask a question
3. Should see: "✅ ONNX Inference Successful!"
4. Shows tokens processed and model working

### With GGUF Model:
1. Load .gguf file  
2. Shows guidance message with conversion instructions
3. No inference runs

---

## Recommended Path Forward

**Easiest:** Download TinyLlama-ONNX from Hugging Face
- Pre-converted, tested, ready to use
- Small size (~600MB)
- Good quality responses

**Best Quality:** Convert your Qwen2 model
- Better aligned with your use case
- Instruction-tuned for conversations
- Requires conversion steps above

**Full Implementation:** Add tokenizer + decoder
- Enables real text generation
- Complete language model capabilities
- More development work needed

---

## Current App Capabilities

✅ **File picker** - Easy model selection  
✅ **ONNX Runtime** - Loads and runs models  
✅ **Inference execution** - Processes inputs  
✅ **Tensor operations** - Input/output handling  
⏳ **Tokenization** - Needs proper tokenizer  
⏳ **Text generation** - Needs decoder loop  

---

## Support

Check project files:
- `convert_model.py` - Conversion guidance
- `LLMInferenceEngine.kt` - Inference code
- Logs - Look for "LLMInferenceEngine" tags

The foundation is ready - just needs an ONNX model and tokenizer to deliver actual AI responses!
