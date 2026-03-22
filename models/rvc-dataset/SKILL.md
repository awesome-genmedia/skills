---
name: rvc-dataset
description: "Rvc Dataset. Create RVC v2 datasets from audio files for voice model training. Triggers: rvc, dataset, voice, training data, voice cloning"
allowed-tools: Bash(curl *), WebFetch
---

# Rvc Dataset

Create RVC v2 datasets from audio files. Outputs a zip file containing processed audio data ready for voice model training.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "rvc-dataset",
    "version": "0.0.1",
    "input": {
      "audio_name": "my-voice-dataset",
      "voice_url": "https://example.com/voice-sample.mp3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_name | string | false | Name of the dataset. Output will be a zip containing a folder named `dataset/{audio_name}`. |
| voice_url | string | | Voice URL to create your RVC v2 dataset from. Supports .mp3, .wav. |

## Examples

**Create dataset from MP3:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "rvc-dataset",
    "version": "0.0.1",
    "input": {
      "audio_name": "singer-voice",
      "voice_url": "https://example.com/singing-sample.mp3"
    }
  }'
```

**Create dataset from WAV:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "rvc-dataset",
    "version": "0.0.1",
    "input": {
      "audio_name": "narrator-voice",
      "voice_url": "https://example.com/narration.wav"
    }
  }'
```

## Related Models

- [mureka-upload-file](../mureka-upload-file/) - Upload audio files for processing
- [mureka-create-speech](../mureka-create-speech/) - Speech generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
