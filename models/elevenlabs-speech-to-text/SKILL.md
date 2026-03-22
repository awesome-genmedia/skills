---
name: elevenlabs-speech-to-text
description: "ElevenLabs | Speech to Text. Transcribe audio to text using ElevenLabs Scribe AI. Accurate speech recognition with speaker diarization and timestamps. Triggers: speech to text, transcribe audio, audio transcription, elevenlabs stt, voice to text, transcription, scribe"
allowed-tools: Bash(curl *), WebFetch
---

# ElevenLabs | Speech to Text

Transcribe audio to text using ElevenLabs Scribe AI. Supports speaker diarization (identifying who is speaking), word-level timestamps, audio event tagging, and multiple languages.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-speech-to-text",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/meeting-recording.mp3",
      "model_id": "scribe_v1",
      "diarize": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | - | URL of the audio file to transcribe |
| diarization_threshold | number | 0.22 | Threshold for speaker diarization. Higher values mean fewer speaker changes |
| diarize | boolean | false | Whether to annotate which speaker is talking |
| language_code | string | - | ISO-639-1 or ISO-639-3 language code of the audio |
| model_id | string | scribe_v1 | Transcription model. Options: `scribe_v1`, `scribe_v1_experimental` |
| num_speakers | integer | - | Expected number of speakers in the audio |
| tag_audio_events | boolean | false | Whether to tag audio events (e.g., laughter, music) |
| timestamp_granularity | string | none | Timestamp detail level. Options: `none`, `word`, `character` |

## Examples

**Transcribe a podcast with speaker labels:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-speech-to-text",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/podcast-episode.mp3",
      "diarize": true,
      "num_speakers": 2,
      "timestamp_granularity": "word",
      "tag_audio_events": true
    }
  }'
```

**Simple transcription with language hint:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-speech-to-text",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/french-interview.wav",
      "language_code": "fr",
      "model_id": "scribe_v1"
    }
  }'
```

**Detailed transcription with character-level timestamps:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-speech-to-text",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/lecture.mp3",
      "timestamp_granularity": "character",
      "model_id": "scribe_v1_experimental"
    }
  }'
```

## Related Models

- [ElevenLabs | Text to Speech](../elevenlabs-text-to-speech/) - Generate speech from text
- [ElevenLabs | Dubbing](../elevenlabs-dubbing/) - Dub audio to other languages
- [ElevenLabs | Voice Changer](../elevenlabs-voice-changer/) - Change voices in audio

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
