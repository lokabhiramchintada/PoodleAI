# Contributing to PoodleAI

Thank you for considering contributing to PoodleAI! This document provides guidelines and instructions for contributing.

## How Can I Contribute?

### 1. Reporting Bugs

**Before Submitting:**
- Check existing issues to avoid duplicates
- Collect relevant information (device, Android version, model used)
- Try to reproduce the issue

**When Submitting:**
```markdown
**Device Information:**
- Device model: (e.g., Pixel 6)
- Android version: (e.g., Android 13)
- RAM: (e.g., 8GB)

**Model Information:**
- Model: (e.g., Gemma 2B INT4)
- Model size: (e.g., 1.2 GB)
- Model path: (e.g., /sdcard/Download/model.bin)

**Bug Description:**
Clear description of the issue

**Steps to Reproduce:**
1. Step one
2. Step two
3. ...

**Expected Behavior:**
What should happen

**Actual Behavior:**
What actually happens

**Logs:**
```
adb logcat | grep PoodleAI
```
(paste relevant logs here)

**Screenshots:**
If applicable
```

### 2. Suggesting Features

We welcome feature suggestions! Please:
- Check if feature already requested
- Explain the use case
- Describe expected behavior
- Consider implementation complexity

**Template:**
```markdown
**Feature Description:**
Clear, concise description

**Use Case:**
Why is this useful?

**Proposed Solution:**
How might this work?

**Alternatives:**
Other ways to achieve this?
```

### 3. Code Contributions

#### Getting Started

1. **Fork the repository**
2. **Clone your fork**
   ```bash
   git clone https://github.com/yourusername/PoodleAI.git
   cd PoodleAI
   ```
3. **Create a branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

#### Development Setup

1. **Open in Android Studio**
   - Android Studio Hedgehog (2023.1.1) or newer
   - Kotlin plugin enabled

2. **Install dependencies**
   - Sync Gradle files
   - Wait for dependency download

3. **Run the app**
   - Connect device or start emulator
   - Click Run or use `./gradlew installDebug`

#### Code Style

**Kotlin Style Guide:**
- Follow [Kotlin coding conventions](https://kotlinlang.org/docs/coding-conventions.html)
- Use meaningful variable names
- Add KDoc comments for public APIs
- Keep functions focused and small

**Example:**
```kotlin
/**
 * Load and initialize the language model
 * 
 * @param modelConfig Configuration for model loading
 * @return Result indicating success or failure
 */
suspend fun loadModel(modelConfig: ModelConfig): Result<Unit> {
    // Implementation
}
```

**Android Specific:**
- Use ViewBinding instead of findViewById
- Prefer Coroutines over callbacks
- Use ViewModel for UI state
- Follow MVVM architecture

#### Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
type(scope): subject

body (optional)

footer (optional)
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding tests
- `chore`: Maintenance tasks

**Examples:**
```bash
feat(inference): add streaming response support

Add ability to stream model responses token-by-token
for better user experience with long responses.

Closes #123

fix(ui): prevent crash on empty message send

Added validation to check message is not empty
before sending to prevent IndexOutOfBoundsException.

Fixes #456
```

#### Pull Request Process

1. **Update documentation**
   - Update README if needed
   - Add/update KDoc comments
   - Update CHANGELOG.md

2. **Test your changes**
   - Test on physical device
   - Test with different models
   - Verify no regressions

3. **Create Pull Request**
   - Use clear title
   - Reference issues
   - Describe changes
   - Add screenshots if UI changes

**PR Template:**
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
How was this tested?

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Comments added for complex code
- [ ] Documentation updated
- [ ] No new warnings generated
- [ ] Tests added/updated
- [ ] Tested on device

## Screenshots (if applicable)

## Related Issues
Closes #xxx
```

### 4. Model Support

**Adding New Model Support:**

1. **Add to ModelType enum**
   ```kotlin
   enum class ModelType {
       GEMMA,
       MISTRAL,
       QWEN,
       YOUR_MODEL,
       CUSTOM
   }
   ```

2. **Update inference engine**
   - Add model-specific initialization
   - Handle any special preprocessing
   - Add model validation

3. **Update documentation**
   - Add to supported models list
   - Include download instructions
   - Note any special requirements

4. **Test thoroughly**
   - Test model loading
   - Test inference
   - Check performance
   - Verify on multiple devices

## Code Review Process

1. **Automated Checks**
   - Build must succeed
   - Lint checks must pass
   - No new warnings

2. **Human Review**
   - Code quality assessment
   - Architecture alignment
   - Performance considerations
   - Security review

3. **Feedback**
   - Address review comments
   - Make requested changes
   - Re-request review

## Community Guidelines

### Be Respectful
- Treat everyone with respect
- Welcome newcomers
- Be constructive in feedback
- Assume good intentions

### Be Collaborative
- Share knowledge
- Help others
- Learn from feedback
- Celebrate successes

### Be Professional
- Keep discussions on-topic
- Avoid offensive language
- Respect different viewpoints
- Follow code of conduct

## Recognition

Contributors will be:
- Listed in CONTRIBUTORS.md
- Credited in release notes
- Acknowledged in commits

Thank you for contributing to PoodleAI! 🎉
