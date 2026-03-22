---
name: mureka-recognize-song
description: "Mureka | Recognize Song. Identify and analyze songs from uploaded audio. Triggers: recognize, identify, song, mureka, music, shazam"
allowed-tools: Bash(curl *), WebFetch
---

# Mureka | Recognize Song

Identify and analyze songs from uploaded audio files. Returns information about the recognized song.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-recognize-song",
    "version": "0.0.1",
    "input": {
      "upload_audio_id": "uploaded-audio-id-from-upload-api"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| upload_audio_id | string | false | Upload ID of the song to recognize (from files/upload API, purpose: audio). |

## Examples

**Recognize a song:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-recognize-song",
    "version": "0.0.1",
    "input": {
      "upload_audio_id": "audio-upload-id-789"
    }
  }'
```

## Related Models

- [mureka-stem-song](../mureka-stem-song/) - Separate song into stems
- [mureka-upload-file](../mureka-upload-file/) - Upload audio files
- [mureka-extend-song](../mureka-extend-song/) - Extend a song

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
