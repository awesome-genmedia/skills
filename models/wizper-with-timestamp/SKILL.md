---
name: wizper-with-timestamp
description: "Wizper with Timestamp. Transcribe audio with word/segment-level timestamps. Triggers: transcription, speech to text, audio transcribe, timestamps, whisper"
allowed-tools: Bash(curl *), WebFetch
---

# Wizper with Timestamp

Transcribe audio files with detailed timestamps at segment or word level. Supports over 50 languages, translation to English, and configurable segment lengths. Built on the Whisper large model variants.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wizper-with-timestamp",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/interview.mp3",
      "chunk_level": "segment",
      "task": "transcribe",
      "language": "en"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | - | URL of the audio file to transcribe. Supported formats: mp3, mp4, mpeg, mpga, m4a, wav, webm. |
| chunk_level | string | segment | Level of the chunks to return. |
| language | string | - | Language of the audio file. Supports 50+ language codes (e.g., `en`, `es`, `fr`, `de`, `ja`, `zh`). |
| max_segment_len | integer | 29 | Maximum speech segment duration in seconds before splitting. |
| merge_chunks | boolean | true | Whether to merge consecutive chunks. |
| task | string | transcribe | Task to perform. Options: `transcribe`, `translate` |
| version | string | 3 | Version of the model to use. All models are the Whisper large variant. |

## Examples

**Basic transcription:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wizper-with-timestamp",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/podcast-episode.mp3"
    }
  }'
```

**Translate foreign audio to English with short segments:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wizper-with-timestamp",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/french-interview.mp3",
      "task": "translate",
      "language": "fr",
      "max_segment_len": 15,
      "merge_chunks": false
    }
  }'
```

**Japanese audio transcription:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wizper-with-timestamp",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/japanese-speech.wav",
      "language": "ja",
      "chunk_level": "segment",
      "max_segment_len": 20
    }
  }'
```

## Related Models

- [Whisper](../whisper/) - Standard Whisper transcription without timestamps
- [Whisper Diarization](../whisper-diarization/) - Transcription with speaker diarization

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
