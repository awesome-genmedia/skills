---
name: faceswap-video
description: "Faceswap | Video. Swap faces in videos using AI. Replace a face in a target video with a face from a source image. Triggers: face swap video, video face swap, replace face video, faceswap, swap face in video, ai face replacement"
allowed-tools: Bash(curl *), WebFetch
---

# Faceswap | Video

Swap faces in videos using AI. Provide a face image and a target video, and the model replaces the face in the video with the one from your image, maintaining natural movement and expressions.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "faceswap-video",
    "version": "0.0.1",
    "input": {
      "face_image_url": "https://example.com/face-photo.jpg",
      "target_video_url": "https://example.com/target-video.mp4"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| face_image_url | string | - | URL of the source face image to use for swapping |
| target_video_url | string | - | URL of the target video where the face will be replaced |

## Examples

**Basic face swap in a video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "faceswap-video",
    "version": "0.0.1",
    "input": {
      "face_image_url": "https://example.com/headshot.jpg",
      "target_video_url": "https://example.com/presentation.mp4"
    }
  }'
```

**Face swap for creative content:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "faceswap-video",
    "version": "0.0.1",
    "input": {
      "face_image_url": "https://example.com/actor-face.jpg",
      "target_video_url": "https://example.com/movie-clip.mp4"
    }
  }'
```

## Related Models

- [PixVerse | Lip Sync](../pixverse-lip-sync/) - Lip sync audio to video
- [ElevenLabs | Voice Changer](../elevenlabs-voice-changer/) - Change voice in audio
- [Luma Dream Machine | Ray 2 | Video Reframe](../luma-dream-machine-ray-2-video-reframe/) - Reframe videos

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
