---
name: mmaudio
description: "MM Audio. Generate synchronized audio from video content using MM Audio. Triggers: mmaudio, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# MM Audio

Generate synchronized audio from video content using MM Audio. Supports configurable duration, negative prompt support, reproducible results via seed.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mmaudio",
    "version": "0.0.1",
    "input": {
      "video": "https://example.com/video.mp4",
      "prompt": "Birds chirping in a forest with a gentle stream"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `cfg_strength` | number | 4.5 | Guidance strength (CFG) |
| `duration` | number | 8 | Duration of output in seconds |
| `negative_prompt` | string | music | Negative prompt to avoid certain sounds |
| `num_steps` | integer | 25 | Number of inference steps |
| `prompt` | string |  | Text prompt for generated audio |
| `seed` | integer |  | Seed |
| `video` | string |  | Optional video file for video-to-audio generation |

## Examples

**Generate audio for video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mmaudio",
    "version": "0.0.1",
    "input": {
      "video": "https://example.com/video.mp4",
      "prompt": "Birds chirping in a forest with a gentle stream"
    }
  }'
```

**Urban soundscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mmaudio",
    "version": "0.0.1",
    "input": {
      "video": "https://example.com/city-video.mp4",
      "prompt": "Busy city traffic sounds with honking and people talking",
      "seed": 42,
      "duration": 10
    }
  }'
```

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
