# Speak-to-Claude

A lightweight, browser-based voice recording and transcription tool designed specifically for Claude AI users. Record your thoughts, have them automatically transcribed, and paste them directly into Claude - all without leaving your browser.

![Audio Transcription Assistant in action](screenshots/speak-to-claude-demo.gif)

## Why Speak-to-Claude?

Typing long thoughts into Claude can be tedious and interrupt your flow of thinking. This tool allows you to speak naturally while capturing your ideas, then seamlessly transfer them to Claude.

Built with simplicity in mind, Speak-to-Claude demonstrates how powerful productivity tools can be created by combining basic web technologies with AI services:
- **Frontend**: Pure HTML/JS that works directly in your browser
- **Backend**: Lightweight n8n workflow (just 4 nodes!) with OpenAI Whisper integration
- **No installation required** - open the HTML file and start speaking

## Features

- **One-Click Voice Recording**: Start and stop recording with a single button
- **Automatic Transcription**: Uses OpenAI's Whisper model for accurate speech-to-text conversion
- **Transcription History**: Keeps track of previous recordings with timestamps and file sizes
- **Quick Copy to Clipboard**: Copy transcriptions with one click to paste into Claude
- **Keyboard Shortcuts**: Use keyboard shortcuts for faster workflow
- **Offline Recording**: Records audio even with unstable internet connections
- **Visual Processing Status**: Clear feedback during transcription processing
- **Local Storage**: All history is stored locally in your browser

## How It Works

The tool uses a two-part architecture:

1. A frontend HTML/JS web interface for recording audio
2. An n8n workflow for processing and transcription via OpenAI's Whisper API

The user journey is simple:

1. The user clicks "Start Recording" and speaks their message
2. After clicking "Stop Recording", the audio is sent to an n8n workflow
3. The n8n workflow processes the audio using OpenAI's Whisper API
4. The transcription is returned and displayed in the interface
5. The user clicks "Copy Transcription" and pastes it into Claude

## Prerequisites

To use this tool, you'll need:

- An n8n instance (self-hosted or cloud)
- OpenAI API key (for Whisper transcription)
- Web server to host the HTML file (or simply open it locally)

## Setup Instructions

### 1. Set up the n8n workflow

1. Ensure you have an n8n instance running. You can [sign up for n8n Cloud](https://www.n8n.cloud/) or [self-host n8n](https://docs.n8n.io/hosting/).
2. Import the `n8n/audio-transcription-workflow.json` file into your n8n instance.
3. Add your OpenAI API credentials to the OpenAI node.
4. Activate the workflow and note the webhook URL.

### 2. Configure the web interface

1. Download the `audio-recorder.html` file from this repository
2. Open the file in a text editor
3. Update the `n8nWebhookUrl` variable with your actual n8n webhook URL:
   ```javascript
   const n8nWebhookUrl = 'https://your-n8n-instance.com/webhook/audio-transcription';
   ```
4. Save the file

### 3. Start using the tool

Either:
- Host the HTML file on a web server, or
- Simply open the file directly in your browser using `file://` protocol

## Coming Soon: Fully Local Version

I'm currently developing a version that works completely locally without requiring n8n or OpenAI API keys. This will make the tool even more accessible and privacy-focused.

## Why I Built This

Speak-to-Claude was created to enhance the Claude AI experience, allowing users to interact more naturally with Claude through voice. Many Claude users prefer its capabilities over other AI assistants, and this tool helps keep them in the Claude ecosystem by removing one of the friction points (typing long messages).

The project demonstrates how relatively simple technologies can be combined to create powerful productivity solutions that integrate with AI platforms. By leveraging n8n as middleware and OpenAI's Whisper for transcription, I created a flexible, lightweight solution that requires minimal setup and technical knowledge.

The entire backend was created with just four n8n nodes in a matter of minutes, showcasing how quickly useful tools can be developed with modern workflow automation platforms.

## Usage Guide

1. Open the HTML file in your browser
2. Click "Start Recording" and grant microphone permissions if prompted
3. Speak your message
4. Click "Stop Recording" when finished
5. Wait for transcription (processing time varies by recording length)
6. Click "Copy Transcription" to copy the text to your clipboard
7. Paste into Claude or any other application

### Keyboard Shortcuts

- `R` - Start/Stop Recording
- `C` - Copy Transcription
- `Esc` - Cancel Recording
- `1-5` - Load Previous Transcriptions (1=most recent)

## Technical Details

### Frontend Technology
- HTML5, CSS3, and JavaScript
- Web Audio API for recording
- Fetch API for communication with n8n
- LocalStorage for history persistence

### Backend Technology
- n8n workflow automation platform
- OpenAI Whisper API for transcription
- Webhook-based communication

## Lessons Learned

During development, I encountered and solved several interesting challenges:
- Working within browser security models for microphone access
- Handling asynchronous processing of audio transcription
- Creating clear visual feedback for better user experience
- Implementing clipboard operations across different browsers

## Future Enhancement Possibilities

1. **Additional Speech-to-Text Providers**: Support for alternative transcription services beyond OpenAI Whisper
2. **Enhanced Privacy Features**: Option to process audio locally for sensitive conversations
3. **Language Selection**: Support for multiple languages and accents
4. **Audio File Import**: Allow uploading existing audio files for transcription
5. **Real-time Transcription**: Live transcription as the user speaks

## Troubleshooting

- **Microphone access denied**: Make sure you've granted microphone permissions to your browser
- **Transcription fails**: Check your n8n workflow configuration and ensure your OpenAI API key is valid
- **Processing takes too long**: Large audio files require more processing time; try shorter recordings
- **Copy button doesn't work**: Some browsers restrict clipboard access; try using keyboard shortcuts

## Privacy Considerations

- Audio recordings are processed through your n8n instance and OpenAI's API
- No audio or transcriptions are permanently stored on external servers
- History is saved only in your local browser storage

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Acknowledgements

- [OpenAI Whisper](https://openai.com/research/whisper) for speech recognition
- [n8n](https://n8n.io/) for workflow automation
- [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API) for audio recording capabilities
- [Claude AI](https://claude.ai) for inspiring this project