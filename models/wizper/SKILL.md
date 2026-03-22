---
name: wizper
description: "Wizper. Transcribe and translate audio files using the Wizper speech recognition model. Triggers: wizper, transcribe, speech to text, audio transcription, translate audio, whisper"
allowed-tools: Bash(curl *), WebFetch
---

# Wizper

Transcribe and translate audio files using the Wizper speech recognition model (based on Whisper large variant). Supports 90+ languages, segment and word-level chunking, and audio translation to English.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wizper",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/interview.mp3",
      "task": "transcribe",
      "language": "en",
      "chunk_level": "segment",
      "version": "3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | | URL of the audio file to transcribe. Supported formats: mp3, mp4, mpeg, mpga, m4a, wav, webm |
| chunk_level | string | segment | Level of the chunks to return |
| language | string | | Language of the audio file (ISO 639-1 code). Supports 90+ languages including en, es, fr, de, ja, zh, ko, etc. |
| task | string | transcribe | Task to perform. enum: transcribe, translate |
| version | string | 3 | Version of the model to use. All models are the Whisper large variant |

## Examples

**Transcribe English audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wizper",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/podcast-episode.mp3",
      "task": "transcribe",
      "language": "en",
      "chunk_level": "segment"
    }
  }'
```

**Translate foreign audio to English:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wizper",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/japanese-meeting.m4a",
      "task": "translate",
      "language": "ja"
    }
  }'
```

**Auto-detect language transcription:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wizper",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/unknown-language-clip.wav",
      "task": "transcribe",
      "chunk_level": "segment"
    }
  }'
```

## Related Models

- [chatterbox-speech-to-speech](../chatterbox-speech-to-speech/) - Speech to speech conversion
- [elevenlabs-text-to-dialogue](../elevenlabs-text-to-dialogue/) - Text to speech dialogue

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
