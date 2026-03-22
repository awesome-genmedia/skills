---
name: whisper
description: "Whisper. Transcribe audio with support for 50+ languages, diarization, and word-level chunks. Triggers: transcription, speech to text, audio transcribe, whisper, subtitles"
allowed-tools: Bash(curl *), WebFetch
---

# Whisper

Transcribe audio files using the Whisper large model. Supports 50+ languages, optional speaker diarization, word/segment-level chunking, and translation to English. Built on the Whisper large v3 variant.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "whisper",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/podcast.mp3",
      "task": "transcribe",
      "language": "en",
      "chunk_level": "segment"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | - | URL of the audio file to transcribe. Supported formats: mp3, mp4, mpeg, mpga, m4a, wav, webm. |
| batch_size | integer | 64 | Batch size for processing. |
| chunk_level | string | segment | Level of chunks to return. Options: `none`, `segment`, `word` |
| diarize | boolean | false | Whether to diarize the audio file. Setting to true adds speaker labels. |
| language | string | - | Language of the audio file. Supports 50+ language codes (e.g., `en`, `es`, `fr`, `de`, `ja`, `zh`). |
| num_speakers | integer | - | Number of speakers in the audio file. If not provided, auto-detected. |
| prompt | string | - | Prompt to use for generation. |
| task | string | transcribe | Task to perform. Options: `transcribe`, `translate` |
| version | string | 3 | Version of the model to use. Options: `3` |

## Examples

**Basic transcription:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "whisper",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/meeting-recording.mp3"
    }
  }'
```

**Word-level transcription with diarization:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "whisper",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/interview.wav",
      "chunk_level": "word",
      "diarize": true,
      "num_speakers": 2,
      "language": "en"
    }
  }'
```

**Translate foreign audio to English:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "whisper",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/german-lecture.mp3",
      "task": "translate",
      "language": "de",
      "chunk_level": "segment"
    }
  }'
```

## Related Models

- [Whisper Diarization](../whisper-diarization/) - Dedicated speaker diarization model
- [Wizper with Timestamp](../wizper-with-timestamp/) - Transcription with detailed timestamps

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
