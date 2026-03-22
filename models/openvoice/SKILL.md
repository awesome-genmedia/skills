---
name: openvoice
description: "Open Voice | Voice Cloning and Text-to-Speech. Clone voices from reference audio and generate speech in multiple languages. Triggers: openvoice, voice cloning, tts, text to speech, voice synthesis"
allowed-tools: Bash(curl *), WebFetch
---

# Open Voice

Clone voices from reference audio and generate speech in multiple languages using OpenVoice. Provide a reference audio file and text to synthesize speech that matches the voice characteristics.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openvoice",
    "version": "0.0.1",
    "input": {
      "text": "Did you ever hear a folk tale about a giant turtle?",
      "audio": "https://example.com/reference-voice.wav",
      "language": "EN_NEWEST",
      "speed": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio | string | - | Input reference audio for voice cloning |
| language | string | EN_NEWEST | Language for synthesis. enum: EN_NEWEST, EN, ES, FR, ZH, JP, KR |
| speed | number | 1 | Speed scale of the output audio |
| text | string | Did you ever hear a folk tale about a giant turtle? | Input text to synthesize |

## Examples

**Spanish voice clone:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openvoice",
    "version": "0.0.1",
    "input": {
      "text": "Hola, bienvenido a nuestra plataforma de inteligencia artificial.",
      "audio": "https://example.com/spanish-voice-sample.wav",
      "language": "ES",
      "speed": 1
    }
  }'
```

**Slow-paced narration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openvoice",
    "version": "0.0.1",
    "input": {
      "text": "In the quiet hours of the morning, the world seems to hold its breath, waiting for the sun to rise.",
      "audio": "https://example.com/narrator-voice.wav",
      "language": "EN_NEWEST",
      "speed": 0.8
    }
  }'
```

## Related Models

- [xtts-v2](../xtts-v2/) - XTTS text-to-speech with 16 languages
- [realistic-voice-cloning](../realistic-voice-cloning/) - RVC-based voice changer
- [incredibly-fast-whisper](../incredibly-fast-whisper/) - Audio transcription

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
