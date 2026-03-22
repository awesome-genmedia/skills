---
name: kling-voice-create
description: "Kling | Voice Create. Create a custom voice from an audio or video file for Kling models. Triggers: voice create, voice clone, custom voice, kling voice"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | Voice Create

Create a custom voice profile from an audio or video file for use with Kling models. Supports mp3, wav audio and mp4, mov video formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-voice-create",
    "version": "0.0.1",
    "input": {
      "voice_url": "https://example.com/voice-sample.mp3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| voice_url | string | - | URL of the voice audio file. Supports .mp3/.wav audio or .mp4/.mov video. |

## Examples

**Create voice from audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-voice-create",
    "version": "0.0.1",
    "input": {
      "voice_url": "https://example.com/speaker-recording.wav"
    }
  }'
```

**Create voice from video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-voice-create",
    "version": "0.0.1",
    "input": {
      "voice_url": "https://example.com/interview-clip.mp4"
    }
  }'
```

## Related Models

- [Kling | v2.6 | Pro | Motion Control](../kling-v2-6-pro-motion-control/) - Use custom voices with Kling Pro video
- [Kling | v1 | TTS](../kling-v1-tts/) - Kling text-to-speech
- [ElevenLabs | Voice Clone](../elevenlabs-voice-clone/) - ElevenLabs voice cloning

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
