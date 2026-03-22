---
name: toolkit
description: "Toolkit - Video Convert | Video Processing and Conversion. Convert between video formats, extract frames, reverse videos, and more. Triggers: toolkit, video convert, video to gif, extract frames, reverse video, video processing"
allowed-tools: Bash(curl *), WebFetch
---

# Toolkit - Video Convert

Process and convert videos with multiple operations: convert to MP4/GIF, extract audio, combine frames into video, extract frames, reverse, and bounce videos.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "toolkit",
    "version": "0.0.1",
    "input": {
      "input_file": "https://example.com/video.mov",
      "task": "convert_input_to_mp4",
      "fps": 30
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| fps | integer | 1 | Frames per second. Use 0 to keep original fps. Controls output frame rate for conversions |
| input_file | string | - | File to process: zip, image, or video |
| task | string | - | Operation to perform. enum: convert_input_to_mp4, convert_input_to_gif, extract_video_audio_as_mp3, zipped_frames_to_mp4, zipped_frames_to_gif, extract_frames_from_input, reverse_video, bounce_video |

## Examples

**Convert video to GIF:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "toolkit",
    "version": "0.0.1",
    "input": {
      "input_file": "https://example.com/clip.mp4",
      "task": "convert_input_to_gif",
      "fps": 15
    }
  }'
```

**Extract audio from video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "toolkit",
    "version": "0.0.1",
    "input": {
      "input_file": "https://example.com/interview.mp4",
      "task": "extract_video_audio_as_mp3"
    }
  }'
```

**Reverse a video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "toolkit",
    "version": "0.0.1",
    "input": {
      "input_file": "https://example.com/action-clip.mp4",
      "task": "reverse_video",
      "fps": 0
    }
  }'
```

## Related Models

- [mochi-1](../mochi-1/) - AI video generation
- [ltx-video](../ltx-video/) - Text-to-video generation
- [magic-animate](../magic-animate/) - Motion-guided video animation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
