---
name: youtube-transcriptor
description: "Youtube Transcriptor | Video Transcription. Transcribe YouTube videos to text from a URL. Triggers: youtube transcriptor, youtube transcript, video transcription, youtube to text, transcribe youtube"
allowed-tools: Bash(curl *), WebFetch
---

# Youtube Transcriptor

Transcribe YouTube videos to text by providing a video URL. Extract spoken content from any YouTube video for subtitles, notes, or content analysis.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "youtube-transcriptor",
    "version": "0.0.1",
    "input": {
      "url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| url | string | - | YouTube video URL to transcribe |

## Examples

**Transcribe a tutorial video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "youtube-transcriptor",
    "version": "0.0.1",
    "input": {
      "url": "https://www.youtube.com/watch?v=abc123def456"
    }
  }'
```

**Transcribe a podcast episode:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "youtube-transcriptor",
    "version": "0.0.1",
    "input": {
      "url": "https://www.youtube.com/watch?v=xyz789ghi012"
    }
  }'
```

## Related Models

- [incredibly-fast-whisper](../incredibly-fast-whisper/) - Audio transcription with Whisper
- [xtts-v2](../xtts-v2/) - Text-to-speech generation
- [openvoice](../openvoice/) - Voice cloning and speech synthesis

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
