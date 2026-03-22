---
name: "Kling V1 Pro AI Avatar"
description: "Generate AI avatar videos using Kling V1 Pro. Trigger: Use when the user wants to create a talking avatar video from an image and audio, or requests 'kling pro avatar', 'AI avatar video', or 'talking head video with pro quality'."
allowed-tools: ["Bash"]
---

# Kling V1 | Pro | AI Avatar

Generate high-quality AI avatar videos by combining a portrait image with audio input. The Pro tier delivers superior lip-sync accuracy and visual fidelity.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-pro-ai-avatar",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/speech.mp3",
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "A professional speaker presenting with natural expressions"
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

### Corporate Presentation Avatar
```json
{
  "model": "kling-v1-pro-ai-avatar",
  "version": "0.0.1",
  "input": {
    "audio_url": "https://example.com/corporate-speech.mp3",
    "image_url": "https://example.com/business-headshot.jpg",
    "prompt": "A confident business professional speaking in a modern office setting"
  }
}
```

### Casual Talking Avatar
```json
{
  "model": "kling-v1-pro-ai-avatar",
  "version": "0.0.1",
  "input": {
    "audio_url": "https://example.com/casual-narration.mp3",
    "image_url": "https://example.com/casual-portrait.jpg",
    "prompt": "A friendly person chatting naturally with warm expressions"
  }
}
```

## Related Models

- [Kling V1 Standard AI Avatar](../kling-v1-standard-ai-avatar/SKILL.md) - Standard quality avatar generation at lower cost
- [EchoMimic V3](../echomimic-v3/SKILL.md) - Alternative talking head generation
- [Character 3](../character-3/SKILL.md) - Audio-driven character video generation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
