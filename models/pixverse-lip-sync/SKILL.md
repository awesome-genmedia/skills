---
name: pixverse-lip-sync
description: "PixVerse | Lip Sync. Sync lips in videos to audio or text using PixVerse AI. Create talking head videos with accurate lip synchronization. Triggers: lip sync, pixverse lip sync, talking head, sync lips, lip sync video, audio to lip sync, lip movement"
allowed-tools: Bash(curl *), WebFetch
---

# PixVerse | Lip Sync

Sync lips in videos to audio or text using PixVerse AI. Provide a video and either audio or text content to generate accurate lip synchronization, with a choice of built-in speaker voices.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-lip-sync",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/talking-head.mp4",
      "audio_url": "https://example.com/speech.mp3",
      "speaker": "auto"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | - | URL of the audio file (max 30 seconds) |
| speaker | string | - | Speaker voice. Options: `auto`, Emily (`1`), James (`2`), Isabella (`3`), Liam (`4`), Chloe (`5`), Adrian (`6`), Harper (`7`), Ava (`8`), Sophia (`9`), Julia (`10`), Mason (`11`), Jack (`12`), Oliver (`13`), Ethan (`14`) |
| speaker_content | string | - | Text content for the speaker to say |
| video_url | string | - | URL of the input video (max 30 seconds) |

## Examples

**Lip sync with audio file:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-lip-sync",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/person-speaking.mp4",
      "audio_url": "https://example.com/voiceover.wav",
      "speaker": "auto"
    }
  }'
```

**Lip sync with text and voice selection:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-lip-sync",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/presenter.mp4",
      "speaker_content": "Hello everyone, welcome to our product launch. Today we are excited to announce something amazing.",
      "speaker": "1"
    }
  }'
```

## Related Models

- [ElevenLabs | Text to Speech](../elevenlabs-text-to-speech/) - Generate speech audio for lip sync
- [Faceswap | Video](../faceswap-video/) - Swap faces in videos
- [ElevenLabs | Voice Changer](../elevenlabs-voice-changer/) - Transform voices in audio

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
