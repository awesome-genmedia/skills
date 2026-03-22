---
name: infinitalk-video-to-video
description: "Infinitalk | Video to Video. Animate video with audio-driven lip sync and motion. Triggers: talking head, lip sync, video animation, audio to video, infinitalk"
allowed-tools: Bash(curl *), WebFetch
---

# Infinitalk | Video to Video

Animate a video by syncing it with audio input, enabling lip sync and facial animation. Supports optional mask images for specifying which person to animate, and configurable resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "infinitalk-video-to-video",
    "version": "0.0.1",
    "input": {
      "video": "https://example.com/person-talking.mp4",
      "audio": "https://example.com/speech.mp3",
      "prompt": "A person speaking naturally with clear lip movements",
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio | string | - | The URL of the audio file. |
| mask_image | string | - | Optional mask image to specify the person in the video to animate. |
| prompt | string | - | The positive prompt for the generation. |
| resolution | string | 720p | Resolution of the video to generate. Options: `480p`, `720p` |
| seed | integer | -1 | The random seed to use for the generation. -1 means a random seed will be used. |
| video | string | - | The video for generating the output. |

## Examples

**Basic video lip sync:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "infinitalk-video-to-video",
    "version": "0.0.1",
    "input": {
      "video": "https://example.com/speaker.mp4",
      "audio": "https://example.com/voiceover.mp3"
    }
  }'
```

**With mask and specific seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "infinitalk-video-to-video",
    "version": "0.0.1",
    "input": {
      "video": "https://example.com/group-scene.mp4",
      "audio": "https://example.com/dialogue.wav",
      "mask_image": "https://example.com/person-mask.png",
      "prompt": "Natural conversation with expressive facial movements",
      "resolution": "720p",
      "seed": 42
    }
  }'
```

## Related Models

- [Infinitalk | Image to Video](../infinitalk-image-to-video/) - Animate a static image with audio
- [Sync | Lipsync | v2 | Pro](../sync-lipsync-v2-pro/) - Professional lip sync solution
- [Bytedance | Omnihuman v1.5](../bytedance-omnihuman-v1-5/) - Full body animation from audio

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
