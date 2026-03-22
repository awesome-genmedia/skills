---
name: elevenlabs-text-to-speech-with-timestamp
description: "ElevenLabs | Text to Speech with Timestamp. Convert text to speech with word-level timestamps using ElevenLabs voices. Triggers: text to speech, tts, elevenlabs, voice synthesis, timestamps"
allowed-tools: Bash(curl *), WebFetch
---

# ElevenLabs | Text to Speech with Timestamp

Convert text to speech using ElevenLabs' high-quality voices with word-level timestamp data. Supports multiple voices, models, languages, and fine-grained voice settings for stability, similarity, and speed.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-text-to-speech-with-timestamp",
    "version": "0.0.1",
    "input": {
      "text": "Welcome to our product demo. Today we will walk you through the key features.",
      "voice_id": "9BWtsMINqrJLrRacOk9x",
      "model_id": "eleven_multilingual_v2",
      "stability": 0.5,
      "similarity_boost": 0.7
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| apply_language_text_normalization | boolean | false | Apply language-specific text normalization. |
| apply_text_normalization | string | auto | Text normalization mode. Options: `auto`, `on`, `off` |
| language_code | string | - | Language code (ISO 639-1) for language enforcement and text normalization. |
| model_id | string | eleven_multilingual_v2 | ElevenLabs model. Options: `eleven_multilingual_v2`, `eleven_flash_v2_5`, `eleven_turbo_v2_5`, `eleven_turbo_v2`, `eleven_flash_v2`, `eleven_monolingual_v1`, `eleven_multilingual_v1`, `eleven_v3` |
| next_text | string | - | Text that comes after the current text for context. |
| previous_text | string | - | Text that comes before the current text for context. |
| seed | integer | - | Seed for reproducibility. |
| similarity_boost | number | 0.7 | Voice similarity boost (0-1). |
| speed | number | - | Speech speed multiplier. |
| stability | number | 0.5 | Voice stability (0-1). Lower values are more expressive. |
| style | number | - | Style exaggeration (0-1). |
| text | string | - | The text to convert to speech. |
| use_speaker_boost | boolean | false | Enable speaker boost for clearer voice. |
| voice_id | string | - | ElevenLabs voice ID. Built-in voices include: Aria, Roger, Sarah, Laura, Charlie, George, Callum, River, Liam, Charlotte, Alice, Matilda, Will, Jessica, Eric, Chris, Brian, Daniel, Lily, Bill. |

## Examples

**Simple text-to-speech:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-text-to-speech-with-timestamp",
    "version": "0.0.1",
    "input": {
      "text": "Hello, this is a test of the text to speech system.",
      "voice_id": "EXAVITQu4vr4xnSDxMaL"
    }
  }'
```

**High-quality multilingual with custom settings:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-text-to-speech-with-timestamp",
    "version": "0.0.1",
    "input": {
      "text": "Bienvenue dans notre demonstration. Nous allons explorer les fonctionnalites principales.",
      "voice_id": "FGY2WhTYpPnrIDTdsKH5",
      "model_id": "eleven_multilingual_v2",
      "language_code": "fr",
      "stability": 0.6,
      "similarity_boost": 0.8,
      "use_speaker_boost": true,
      "speed": 0.9
    }
  }'
```

## Related Models

- [ElevenLabs | Text to Speech](../elevenlabs-text-to-speech/) - Standard text to speech without timestamps
- [ElevenLabs | Voice Clone](../elevenlabs-voice-clone/) - Clone a voice from audio
- [ElevenLabs | Voice Design v3](../elevenlabs-voice-design-v3/) - Design custom voices

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
