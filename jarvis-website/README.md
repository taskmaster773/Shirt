# JARVIS - AI Voice Assistant Website

A realistic, interactive JARVIS AI assistant website with real-time voice recognition and response capabilities.

## Features

✨ **Real-Time Voice Recognition**
- Uses Web Speech API for live voice input
- Continuous listening with interim results
- Support for 50+ languages

🎤 **Microphone Permission Handling**
- Requests microphone access on startup
- Graceful error handling
- Visual feedback for microphone status

🤖 **AI Responses**
- Free tier API integration (HuggingFace/Local fallback)
- Natural language understanding
- Context-aware responses

🔊 **Text-to-Speech (TTS)**
- Authentic JARVIS-like voice synthesis
- Adjustable speech speed and pitch
- Browser-native speech synthesis

📊 **Voice Visualizer**
- Real-time frequency visualization
- Animated waveforms
- Idle state patterns

🎨 **Premium UI Design**
- Neon JARVIS aesthetic
- Animated background grid
- Smooth transitions and effects
- Fully responsive design

## Technology Stack

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Voice Recognition**: Web Speech API
- **Text-to-Speech**: Web Speech Synthesis API
- **AI Backend**: 
  - Free tier: HuggingFace Inference API (with fallback)
  - Local response engine for offline functionality
- **HTTP Client**: Axios

## How to Use

1. **Open the Website**
   - Open `index.html` in a modern web browser

2. **Grant Microphone Permission**
   - Allow microphone access when prompted
   - The website cannot function without microphone access

3. **Start Listening**
   - Click the "Start Listening" button
   - Speak your question or command
   - The visualizer will show real-time audio input

4. **Get AI Response**
   - JARVIS will process your input
   - Response appears in the conversation box
   - Audio response plays automatically (if enabled)

5. **Configure Settings**
   - **Auto Speak Response**: Enable/disable automatic voice responses
   - **Voice Speed**: Adjust speech synthesis speed (0.5x to 2x)
   - **Clear History**: Remove conversation history

## Free AI APIs Used

### Primary: HuggingFace Free Inference API
- **Model**: Google FLAN-T5 Base
- **Endpoint**: https://api-inference.huggingface.co
- **Rate Limit**: Limited free tier (~150 calls/hour)
- **Setup**: Optional API key for higher limits
- **Docs**: https://huggingface.co/docs/api-inference

### Fallback: Local Response Engine
- Pre-defined responses for common queries
- Works completely offline if primary API fails
- Expandable keyword matching system

### Alternative Free Options

#### OpenAI API (with free trial)
```javascript
// Replace getAIResponse with:
const response = await axios.post('https://api.openai.com/v1/chat/completions', {
    model: 'gpt-3.5-turbo',
    messages: [{ role: 'user', content: userInput }]
}, {
    headers: { 'Authorization': 'Bearer YOUR_FREE_TRIAL_KEY' }
});
```

#### Cohere API
- Free tier: 100 API calls per month
- Endpoint: https://api.cohere.com/generate

#### Hugging Face Transformers.js (Local)
```javascript
// Run AI model directly in browser (no API needed)
import { pipeline } from '@xenova/transformers';
const generator = await pipeline('text-generation', 'Xenova/distilgpt2');
const result = await generator(userInput, { max_new_tokens: 100 });
```

## Browser Compatibility

| Browser | Support | Voice Recognition | TTS |
|---------|---------|------------------|-----|
| Chrome | ✅ Full | ✅ Yes | ✅ Yes |
| Edge | ✅ Full | ✅ Yes | ✅ Yes |
| Firefox | ⚠️ Limited | ✅ Yes | ✅ Yes |
| Safari | ⚠️ Limited | ⚠️ Webkit | ✅ Yes |
| Opera | ✅ Full | ✅ Yes | ✅ Yes |

**Note**: Voice recognition requires HTTPS in production environments.

## Configuration

Edit the `CONFIG` object in `jarvis.js`:

```javascript
const CONFIG = {
    apiKey: 'free-tier', // Set to your HuggingFace token if you have one
    voiceSpeed: 1, // Default speech speed
    autoSpeak: true, // Auto-play voice responses
    language: 'en-US' // Language code for speech recognition
};
```

## Customization

### Add Custom Commands

Edit the `getLocalResponse()` function:

```javascript
const responses = {
    'your command': 'Your custom response',
    'say hello': 'Hello there!',
    // ... add more commands
};
```

### Change Voice Settings

In `speakResponse()` function:
```javascript
utterance.pitch = 1.2; // Change pitch (0.1 to 2)
utterance.volume = 0.8; // Change volume (0 to 1)
```

### Modify UI Colors

Update CSS variables in `styles.css`:
```css
:root {
    --primary-color: #00d4ff; /* Change cyan color */
    --accent: #00ff88; /* Change accent color */
    --dark-bg: #0a0e27; /* Change background */
}
```

## Troubleshooting

### Microphone Not Working
- Ensure site is served over HTTPS in production
- Check browser microphone permissions
- Verify `getUserMedia` is supported

### Voice Recognition Not Starting
- Check browser console for errors
- Ensure microphone is functioning
- Try a different browser

### TTS Not Playing
- Check browser volume
- Verify `SpeechSynthesis` API is available
- Check for browser autoplay restrictions

### AI API Timeouts
- Switch to local response engine
- Use alternative free API
- Implement offline-first approach with Transformers.js

## Performance Tips

1. **Reduce API Calls**: Cache common responses
2. **Local Processing**: Use Transformers.js for offline AI
3. **Lazy Load**: Load AI libraries on demand
4. **Service Worker**: Add offline support

## Security Notes

⚠️ **Important**:
- Never hardcode API keys in client-side code
- Use CORS proxies for production
- Implement rate limiting on server-side
- Validate all user input
- Store API keys securely on backend

## Deployment

### Vercel (Recommended)
```bash
npm i -g vercel
vercel
```

### GitHub Pages
1. Push to GitHub
2. Enable GitHub Pages in settings
3. Access at `https://username.github.io/repo`

### Local Server
```bash
python -m http.server 8000
# or
npx http-server
```

## License

Free to use and modify for personal/commercial projects.

## Future Enhancements

- [ ] Multi-turn conversation memory
- [ ] Custom wake word detection
- [ ] Multiple voice profiles
- [ ] Integration with smart home devices
- [ ] Advanced NLU with entity recognition
- [ ] Conversation history persistence
- [ ] Real-time translation support
- [ ] Custom AI model fine-tuning

## Support

For issues, suggestions, or contributions, please open an issue on GitHub.

---

**Created with ❤️ for AI enthusiasts**
