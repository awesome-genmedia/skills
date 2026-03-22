---
name: incredibly-fast-whisper
description: "Incredibly Fast Whisper | Audio Transcription. Transcribe audio files quickly with speaker diarization and multi-language support. Triggers: whisper, transcription, audio to text, speech to text, transcribe audio"
allowed-tools: Bash(curl *), WebFetch
---

# Incredibly Fast Whisper

Transcribe audio files with high speed using an optimized Whisper model. Supports multiple languages, speaker diarization, and word-level timestamps.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "incredibly-fast-whisper",
    "version": "0.0.1",
    "input": {
      "audio": "https://example.com/podcast-episode.wav",
      "language": "english",
      "task": "transcribe",
      "timestamp": "chunk"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio | string | - | Audio file to transcribe |
| batch_size | integer | 24 | Batch size for processing |
| diarise_audio | boolean | false | Split conversation into segments by speaker |
| hf_token | string | - | HuggingFace API token for accessing private resources |
| language | string | None | Input language. enum: None (auto-detect), afrikaans, amharic, arabic, azerbaijani, belarusian, bosnian, breton, bulgarian, cantonese, catalan, chinese, croatian, czech, danish, dutch, english, estonian, finnish, french, german, hebrew, hindi, hungarian, italian, japanese, korean, lithuanian, macedonian, mongolian, myanmar, nepali, norwegian, polish, portuguese, romanian, russian, serbian, slovak, slovenian, spanish, swahili, swedish, tatar, telugu, turkish, ukrainian, welsh |
| task | string | transcribe | Task to perform. enum: transcribe |
| timestamp | string | chunk | Timestamp granularity. enum: chunk, word |

## Examples

**Transcribe with speaker diarization:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "incredibly-fast-whisper",
    "version": "0.0.1",
    "input": {
      "audio": "https://example.com/interview.wav",
      "language": "english",
      "diarise_audio": true,
      "timestamp": "word",
      "batch_size": 24
    }
  }'
```

**Auto-detect language transcription:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "incredibly-fast-whisper",
    "version": "0.0.1",
    "input": {
      "audio": "https://example.com/foreign-audio.mp3",
      "language": "None",
      "task": "transcribe",
      "timestamp": "chunk"
    }
  }'
```

## Related Models

- [youtube-transcriptor](../youtube-transcriptor/) - YouTube video transcription
- [xtts-v2](../xtts-v2/) - Text-to-speech synthesis
- [openvoice](../openvoice/) - Voice cloning and speech

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
