---
name: "Kling V1 Standard AI Avatar"
description: "Generate AI avatar videos using Kling V1 Standard. Trigger: Use when the user wants to create a talking avatar video from an image and audio, or requests 'kling standard avatar', 'quick avatar video', or 'budget talking head video'."
allowed-tools: ["Bash"]
---

# Kling V1 | Standard | AI Avatar

Generate AI avatar videos by combining a portrait image with audio. The Standard tier provides fast generation with solid quality at a lower cost than Pro.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-standard-ai-avatar",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/speech.mp3",
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "A person speaking naturally with subtle head movements"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `audio_url` | string | (empty) | The URL of the audio file |
| `image_url` | string | (empty) | The URL of the image to use as your avatar |
| `prompt` | string | (empty) | The prompt to use for the video generation |

## Output

- **Type:** video

## Examples

### Tutorial Narrator
```json
{
  "model": "kling-v1-standard-ai-avatar",
  "version": "0.0.1",
  "input": {
    "audio_url": "https://example.com/tutorial-audio.mp3",
    "image_url": "https://example.com/instructor.jpg",
    "prompt": "An instructor explaining a concept clearly with engaging expressions"
  }
}
```

### Social Media Content
```json
{
  "model": "kling-v1-standard-ai-avatar",
  "version": "0.0.1",
  "input": {
    "audio_url": "https://example.com/social-clip.mp3",
    "image_url": "https://example.com/influencer.jpg",
    "prompt": "A social media creator talking energetically to the camera"
  }
}
```

## Related Models

- [Kling V1 Pro AI Avatar](../kling-v1-pro-ai-avatar/SKILL.md) - Higher quality avatar generation
- [Bytedance OmniHuman](../bytedance-omnihuman/SKILL.md) - Audio-driven human video generation
- [LatentSync](../latentsync/SKILL.md) - Lip sync generation for existing videos

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
