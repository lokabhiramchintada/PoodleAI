# Changelog

All notable changes to PoodleAI will be documented in this file.

## [1.0.0] - 2026-02-12

### Added
- 🎉 Initial release of PoodleAI
- ✨ On-device LLM inference using MediaPipe
- 💬 Chat interface with message history
- 🔧 Model configuration dialog
- 📱 Support for multiple SLM models:
  - Google Gemma (2B, 7B)
  - Mistral 7B
  - Qwen 2B
  - Custom models
- 🎨 Material Design UI with dark/light theme support
- ⚡ Coroutine-based async operations
- 🔒 Complete privacy - all processing on-device
- 📊 Real-time model status indicators
- ⚙️ Configurable inference parameters
- 🛡️ Model file validation
- 📝 Comprehensive documentation

### Features
- **LLM Inference Engine**
  - MediaPipe Tasks GenAI integration
  - ONNX Runtime support for alternative models
  - Streaming response capability
  - Error handling and recovery
  
- **Chat UI**
  - Clean message bubbles (user vs assistant)
  - Auto-scroll to latest message
  - Loading indicators
  - Error notifications
  
- **Model Management**
  - Dynamic model loading
  - Model type selection (Gemma/Mistral/Qwen/Custom)
  - Path validation and file checking
  - Model size display
  - Suggested model paths
  
- **Configuration**
  - Adjustable max tokens
  - Temperature control
  - Top-K and Top-P sampling
  - Random seed setting

### Technical Details
- **Architecture**
  - MVVM pattern with ViewModels
  - Kotlin Coroutines for async operations
  - Flow-based state management
  - RecyclerView with ListAdapter
  - ViewBinding for type-safe UI access
  
- **Dependencies**
  - MediaPipe Tasks GenAI 0.10.9
  - ONNX Runtime 1.16.3
  - Kotlin 1.9.22
  - AndroidX libraries
  - Material Components 1.11.0

### Documentation
- README with comprehensive setup guide
- Model download guide with multiple sources
- Quick setup guide for beginners
- Troubleshooting documentation
- Code comments and KDoc

### Known Limitations
- Models must be downloaded separately (not bundled)
- First model load can be slow (30-60 seconds)
- Large models (7B+) require 8GB+ RAM
- No automatic model download yet
- No conversation export feature yet

### Notes
- Minimum Android version: 7.0 (API 24)
- Target Android version: 14 (API 36)
- Tested on devices with 4GB-12GB RAM
- Optimal with quantized INT4/INT8 models

---

## [Future Releases]

### Planned for v1.1.0
- [ ] Voice input support
- [ ] Streaming response display
- [ ] Conversation history persistence
- [ ] Model download manager
- [ ] Performance benchmarking

### Planned for v1.2.0
- [ ] Multi-language support
- [ ] Custom system prompts
- [ ] Conversation export (JSON/TXT)
- [ ] Theme customization
- [ ] Widget support

### Planned for v2.0.0
- [ ] RAG (Retrieval Augmented Generation)
- [ ] Multi-modal support (images)
- [ ] Model fine-tuning interface
- [ ] Cloud sync (optional)
- [ ] Voice output (TTS)

---

## Version Format

This project follows [Semantic Versioning](https://semver.org/):
- MAJOR version for incompatible API changes
- MINOR version for new functionality
- PATCH version for bug fixes

## Release Notes Template

```
## [X.Y.Z] - YYYY-MM-DD

### Added
- New features

### Changed
- Changes to existing functionality

### Deprecated
- Soon-to-be removed features

### Removed
- Removed features

### Fixed
- Bug fixes

### Security
- Security improvements
```
