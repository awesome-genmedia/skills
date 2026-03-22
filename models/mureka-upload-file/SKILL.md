---
name: mureka-upload-file
description: "Mureka | Upload File. Upload audio files for use with Mureka models (voice cloning, reference, etc). Triggers: upload, file, mureka, audio, reference"
allowed-tools: Bash(curl *), WebFetch
---

# Mureka | Upload File

Upload audio files for use with other Mureka models. Files can be uploaded for various purposes including voice cloning, reference tracks, melody extraction, and more.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-upload-file",
    "version": "0.0.1",
    "input": {
      "file": "https://example.com/voice-sample.mp3",
      "purpose": "voice"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| file | string | false | URL of the file to upload. |
| purpose | string | false | Intended purpose of the uploaded file. enum: reference, vocal, melody, instrumental, voice, audio |

## Examples

**Upload for voice cloning:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-upload-file",
    "version": "0.0.1",
    "input": {
      "file": "https://example.com/my-voice.wav",
      "purpose": "voice"
    }
  }'
```

**Upload a reference track:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-upload-file",
    "version": "0.0.1",
    "input": {
      "file": "https://example.com/reference-song.mp3",
      "purpose": "reference"
    }
  }'
```

**Upload instrumental for processing:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-upload-file",
    "version": "0.0.1",
    "input": {
      "file": "https://example.com/beat.mp3",
      "purpose": "instrumental"
    }
  }'
```

## Related Models

- [mureka-create-speech](../mureka-create-speech/) - Speech generation with voice cloning
- [mureka-recognize-song](../mureka-recognize-song/) - Song recognition
- [mureka-extend-song](../mureka-extend-song/) - Song extension

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
