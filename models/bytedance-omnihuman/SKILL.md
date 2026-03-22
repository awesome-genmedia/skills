---
name: "Bytedance OmniHuman"
description: "Generate human videos driven by audio using ByteDance OmniHuman. Trigger: Use when the user wants to create a talking human video, or requests 'omnihuman', 'bytedance talking video', or 'audio-driven human animation'."
allowed-tools: ["Bash"]
---

# Bytedance | OmniHuman

Generate realistic human animation videos driven by audio. Provide a portrait image and audio to create a video of the person speaking or performing.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-omnihuman",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "audio_url": "https://example.com/speech.mp3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `audio_url` | string | `false` | The URL of the audio file. Audio must be under 30s long |
| `image_url` | string | `false` | The URL of the image used to generate the video |

## Output

- **Type:** video

## Examples

### Professional Presentation
```json
{
  "model": "bytedance-omnihuman",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/speaker-headshot.jpg",
    "audio_url": "https://example.com/presentation-audio.mp3"
  }
}
```

### Educational Content
```json
{
  "model": "bytedance-omnihuman",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/teacher-photo.jpg",
    "audio_url": "https://example.com/lesson-narration.mp3"
  }
}
```

## Related Models

- [Character 3](../character-3/SKILL.md) - Alternative audio-driven character video
- [EchoMimic V3](../echomimic-v3/SKILL.md) - Talking head with detailed controls
- [LatentSync](../latentsync/SKILL.md) - Lip sync for existing videos

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
