---
name: "Stable Audio 2.5 Inpaint"
description: "Inpaint specific sections of an audio clip using Stable Audio 2.5. Trigger: Use when the user wants to replace or fill in parts of an audio clip, or requests 'audio inpainting', 'fix audio section', 'stable audio inpaint', or 'replace part of audio'."
allowed-tools: ["Bash"]
---

# Stable Audio 2.5 | Inpaint

Replace or regenerate specific sections of an audio clip using a text prompt. Define the start and end points of the mask to target exactly which portion of the audio to inpaint.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-audio-2-5-inpaint",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/track.wav",
      "prompt": "Smooth transition with a drum fill",
      "mask_start": 30,
      "mask_end": 60,
      "guidance_scale": 1,
      "num_inference_steps": 8,
      "seconds_total": 190
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `audio_url` | string | (empty) | The audio clip to inpaint |
| `guidance_scale` | integer | `1` | How strictly the diffusion process adheres to the prompt text (higher values keep closer to prompt) |
| `mask_end` | integer | `190` | The end point of the audio mask |
| `mask_start` | integer | `30` | The start point of the audio mask |
| `num_inference_steps` | integer | `8` | The number of steps to denoise the audio for |
| `prompt` | string | (empty) | The prompt to guide the audio generation |
| `seconds_total` | integer | `190` | The duration of the audio clip to generate. If not provided, matches input length |
| `seed` | integer | (empty) | Random seed for reproducibility |

## Output

- **Type:** audio

## Examples

### Replace a Section with Music
```json
{
  "model": "stable-audio-2-5-inpaint",
  "version": "0.0.1",
  "input": {
    "audio_url": "https://example.com/podcast.wav",
    "prompt": "Upbeat background music transition",
    "mask_start": 45,
    "mask_end": 75,
    "guidance_scale": 2,
    "num_inference_steps": 10,
    "seconds_total": 120
  }
}
```

### Fill Gap with Ambient Sound
```json
{
  "model": "stable-audio-2-5-inpaint",
  "version": "0.0.1",
  "input": {
    "audio_url": "https://example.com/nature-recording.wav",
    "prompt": "Birds chirping with gentle wind in a forest",
    "mask_start": 10,
    "mask_end": 40,
    "guidance_scale": 1,
    "num_inference_steps": 8,
    "seed": 123
  }
}
```

## Related Models

- [Stable Audio 2.5 Audio to Audio](../stable-audio-2-5-audio-to-audio/SKILL.md) - Transform entire audio clips
- [Stable Audio 2.5 Text to Audio](../stable-audio-2-5-text-to-audio/SKILL.md) - Generate audio from text
- [Minimax Music V1.5](../minimax-music-v1-5/SKILL.md) - Generate music with lyrics

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
