---
name: xtts-v2
description: "XTTS | Text-to-Speech with Voice Cloning. Generate speech from text with voice cloning in 16 languages. Triggers: xtts, text to speech, tts, voice cloning, speech synthesis"
allowed-tools: Bash(curl *), WebFetch
---

# XTTS

Generate speech from text with voice cloning using XTTS v2. Supports 16 languages and custom speaker voices for natural-sounding text-to-speech synthesis.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xtts-v2",
    "version": "0.0.1",
    "input": {
      "text": "Welcome to our platform. We are excited to have you here today.",
      "language": "en",
      "cleanup_voice": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| cleanup_voice | boolean | true | Refine and improve the quality of generated speech |
| language | string | en | Language for synthesis. enum: en, es, fr, de, it, pt, pl, tr, ru, nl, cs, ar, zh, hu, ko, hi |
| speaker | string | - | Specific voice/persona to speak the text |
| text | string | Hello, you are now at Eachlabs AI... | Written input to convert into spoken words |

## Examples

**Spanish voice synthesis:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xtts-v2",
    "version": "0.0.1",
    "input": {
      "text": "Bienvenidos a nuestra plataforma de inteligencia artificial. Estamos encantados de tenerte aqui.",
      "language": "es",
      "cleanup_voice": true
    }
  }'
```

**Custom speaker voice cloning:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xtts-v2",
    "version": "0.0.1",
    "input": {
      "text": "This is a demonstration of voice cloning technology with natural-sounding speech output.",
      "speaker": "https://example.com/voice-sample.wav",
      "language": "en",
      "cleanup_voice": true
    }
  }'
```

## Related Models

- [openvoice](../openvoice/) - Voice cloning with style control
- [realistic-voice-cloning](../realistic-voice-cloning/) - RVC-based voice changer
- [incredibly-fast-whisper](../incredibly-fast-whisper/) - Audio transcription

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
