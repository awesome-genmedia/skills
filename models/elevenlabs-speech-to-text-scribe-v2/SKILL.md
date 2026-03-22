---
name: elevenlabs-speech-to-text-scribe-v2
description: "ElevenLabs | Speech to Text Scribe V2. Advanced transcription with diarization, audio event tagging, and character-level timestamps. Triggers: transcribe, speech to text, stt, elevenlabs, scribe"
allowed-tools: Bash(curl *), WebFetch
---

# ElevenLabs | Speech to Text Scribe V2

Advanced speech-to-text transcription using ElevenLabs Scribe V2 with speaker diarization, audio event tagging, multi-channel support, and character-level timestamps.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-speech-to-text-scribe-v2",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/podcast-episode.mp3",
      "diarize": true,
      "timestamps_granularity": "word"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| diarization_threshold | number | false | Diarization threshold. Higher = more conservative speaker splitting. |
| diarize | boolean | false | Annotate which speaker is talking in the uploaded file. |
| language_code | string | false | ISO-639-1 or ISO-639-3 language code for the audio. |
| media_url | string | false | URL of the audio file to transcribe. |
| num_speakers | integer | false | Maximum number of speakers. Helps with speaker prediction. |
| seed | integer | false | Random seed for reproducibility. |
| tag_audio_events | boolean | false | Tag audio events like (laughter), (footsteps), etc. |
| temperature | number | false | Controls randomness of transcription output (0.0 to 1.0). |
| timestamps_granularity | string | word | Timestamp granularity. enum: none, word, character |
| use_multi_channel | boolean | false | Process multiple audio channels independently. |

## Examples

**Podcast transcription with diarization:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-speech-to-text-scribe-v2",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/interview.mp3",
      "diarize": true,
      "num_speakers": 2,
      "timestamps_granularity": "word",
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
    "model": "elevenlabs-speech-to-text-scribe-v2",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/spanish-audio.wav",
      "language_code": "es",
      "timestamps_granularity": "word"
    }
  }'
```

**Character-level timestamps for subtitles:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-speech-to-text-scribe-v2",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/video-audio.mp3",
      "timestamps_granularity": "character",
      "tag_audio_events": true,
      "seed": 42
    }
  }'
```

## Related Models

- [deepgram-nova-3-speech-to-text](../deepgram-nova-3-speech-to-text/) - Deepgram Nova-3 transcription
- [deepgram-nova-3-speech-to-text-pro](../deepgram-nova-3-speech-to-text-pro/) - Deepgram Nova-3 Pro with sentiment and entities

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
