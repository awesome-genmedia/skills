---
name: "ElevenLabs Voice Clone"
description: "Clone voices using ElevenLabs from audio samples. Trigger: Use when the user wants to clone a voice, or requests 'elevenlabs voice clone', 'clone my voice', 'create custom voice', or 'voice cloning'."
allowed-tools: ["Bash"]
---

# Elevenlabs Voice Clone

Clone a voice from audio samples. Upload audio files to create a custom voice profile with defined tone, style, and personality.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-voice-clone",
    "version": "0.0.1",
    "input": {
      "name": "My Custom Voice",
      "description": "A warm, professional male voice with a slight British accent",
      "files": ["https://example.com/voice-sample-1.mp3", "https://example.com/voice-sample-2.mp3"],
      "remove_background_noise": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `description` | string | `false` | Defines the tone, style, and personality of the generated voice |
| `files` | array | `false` | Upload your audio files for voice cloning |
| `name` | string | `false` | Enter voice name |
| `remove_background_noise` | boolean | `false` | Whether to remove background noise from the samples |

## Output

- **Type:** text

## Examples

### Professional Narrator Clone
```json
{
  "model": "elevenlabs-voice-clone",
  "version": "0.0.1",
  "input": {
    "name": "Corporate Narrator",
    "description": "A clear, authoritative male voice suitable for corporate narrations and presentations",
    "files": ["https://example.com/narration-sample.mp3"],
    "remove_background_noise": true
  }
}
```

### Character Voice Clone
```json
{
  "model": "elevenlabs-voice-clone",
  "version": "0.0.1",
  "input": {
    "name": "Story Character",
    "description": "An expressive, youthful female voice with playful energy for character work",
    "files": ["https://example.com/character-voice-1.wav", "https://example.com/character-voice-2.wav"],
    "remove_background_noise": false
  }
}
```

## Related Models

- [Kling V1 Text to Speech](../kling-v1-tts/SKILL.md) - Text-to-speech with preset voices
- [Kling V1 Pro AI Avatar](../kling-v1-pro-ai-avatar/SKILL.md) - Combine cloned voice with avatar video

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
