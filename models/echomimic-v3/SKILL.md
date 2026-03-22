---
name: "EchoMimic V3"
description: "Generate talking head videos with audio-driven facial animation. Trigger: Use when the user wants to animate a portrait with audio, or requests 'echomimic', 'talking head animation', or 'animate face with audio'."
allowed-tools: ["Bash"]
---

# EchoMimic V3

Generate realistic talking head videos by combining a portrait image with an audio reference. Features fine-grained control over guidance scale, frame count, and negative prompts.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "echomimic-v3",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "audio_url": "https://example.com/speech.mp3",
      "prompt": "A person speaking naturally with realistic expressions",
      "guidance_scale": 4.5,
      "audio_guidance_scale": 2.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `audio_guidance_scale` | number | `2.5` | The audio guidance scale for the video generation |
| `audio_url` | string | (empty) | The URL of the audio to use as a reference |
| `guidance_scale` | number | `4.5` | The guidance scale for the video generation |
| `image_url` | string | (empty) | The URL of the image to use as a reference |
| `negative_prompt` | string | (empty) | The negative prompt for the video generation |
| `num_frames_per_generation` | integer | `121` | The number of frames to generate at once |
| `prompt` | string | (empty) | The prompt for the video generation |
| `seed` | integer | (empty) | The seed for reproducible generation |

## Output

- **Type:** video

## Examples

### Professional Speaker
```json
{
  "model": "echomimic-v3",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/business-headshot.jpg",
    "audio_url": "https://example.com/presentation.mp3",
    "prompt": "A professional speaker presenting clearly",
    "negative_prompt": "blurry, distorted, low quality",
    "guidance_scale": 5.0,
    "audio_guidance_scale": 3.0,
    "num_frames_per_generation": 121
  }
}
```

### Animated Character
```json
{
  "model": "echomimic-v3",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/character-art.jpg",
    "audio_url": "https://example.com/voice-line.mp3",
    "prompt": "An animated character speaking with lively expressions",
    "guidance_scale": 4.0,
    "audio_guidance_scale": 2.5,
    "seed": 42
  }
}
```

## Related Models

- [Kling V1 Pro AI Avatar](../kling-v1-pro-ai-avatar/SKILL.md) - Pro-tier AI avatar generation
- [LatentSync](../latentsync/SKILL.md) - Lip sync for existing videos
- [Bytedance OmniHuman](../bytedance-omnihuman/SKILL.md) - Audio-driven human video

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
