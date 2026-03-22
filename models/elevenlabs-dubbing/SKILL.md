---
name: elevenlabs-dubbing
description: "ElevenLabs | Dubbing. Dub videos and audio into different languages using ElevenLabs AI. Automatic translation and voice dubbing. Triggers: dubbing, translate video, dub video, language dubbing, elevenlabs dubbing, voice dubbing, translate audio, multilingual dub"
allowed-tools: Bash(curl *), WebFetch
---

# ElevenLabs | Dubbing

Dub videos and audio into different languages using ElevenLabs AI. Automatically translates and re-voices content from a source language to a target language while preserving the original speaker's tone and style.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-dubbing",
    "version": "0.0.1",
    "input": {
      "source_url": "https://example.com/english-video.mp4",
      "source_lang": "en",
      "target_lang": "es"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| source_lang | string | - | Source language code (e.g., `en`, `es`, `fr`, `de`, `ja`) |
| source_url | string | - | URL of the source video or audio file |
| target_lang | string | - | Target language code (e.g., `en`, `es`, `fr`, `de`, `ja`) |

## Examples

**Dub English video to Spanish:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-dubbing",
    "version": "0.0.1",
    "input": {
      "source_url": "https://example.com/product-demo.mp4",
      "source_lang": "en",
      "target_lang": "es"
    }
  }'
```

**Dub Japanese audio to English:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-dubbing",
    "version": "0.0.1",
    "input": {
      "source_url": "https://example.com/japanese-podcast.mp3",
      "source_lang": "ja",
      "target_lang": "en"
    }
  }'
```

## Related Models

- [ElevenLabs | Text to Speech](../elevenlabs-text-to-speech/) - Generate speech from text
- [ElevenLabs | Speech to Text](../elevenlabs-speech-to-text/) - Transcribe audio to text
- [ElevenLabs | Voice Changer](../elevenlabs-voice-changer/) - Change voices in audio

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
