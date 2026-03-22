---
name: "Stable Audio 2.5 Audio to Audio"
description: "Transform existing audio clips using Stable Audio 2.5. Trigger: Use when the user wants to modify or restyle an audio clip, or requests 'audio to audio', 'transform audio', 'stable audio remix', or 'restyle my audio'."
allowed-tools: ["Bash"]
---

# Stable Audio 2.5 | Audio to Audio

Transform an existing audio clip into a new version guided by a text prompt. Control how much of the original audio is preserved with the strength parameter.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-audio-2-5-audio-to-audio",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/original-track.wav",
      "prompt": "Ambient electronic music with reverb and soft pads",
      "strength": 0.8,
      "guidance_scale": 1,
      "num_inference_steps": 8
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `audio_url` | string | (empty) | The audio clip to transform |
| `guidance_scale` | integer | `1` | How strictly the diffusion process adheres to the prompt text (higher values keep closer to prompt) |
| `num_inference_steps` | integer | `8` | The number of steps to denoise the audio for |
| `prompt` | string | (empty) | The prompt to guide the audio generation |
| `seed` | integer | (empty) | Random seed for reproducibility |
| `strength` | number | `0.8` | Controls how much influence the original audio has. Lower values preserve more of the original |
| `total_seconds` | integer | (empty) | The duration of the audio clip to generate. If not provided, matches the input length |

## Output

- **Type:** audio

## Examples

### Restyle to Jazz
```json
{
  "model": "stable-audio-2-5-audio-to-audio",
  "version": "0.0.1",
  "input": {
    "audio_url": "https://example.com/piano-melody.wav",
    "prompt": "Smooth jazz with saxophone and upright bass",
    "strength": 0.7,
    "guidance_scale": 2,
    "num_inference_steps": 12
  }
}
```

### Add Ambient Texture
```json
{
  "model": "stable-audio-2-5-audio-to-audio",
  "version": "0.0.1",
  "input": {
    "audio_url": "https://example.com/field-recording.wav",
    "prompt": "Dreamy ambient soundscape with ethereal pads and gentle reverb",
    "strength": 0.5,
    "guidance_scale": 1,
    "num_inference_steps": 8,
    "seed": 42
  }
}
```

## Related Models

- [Stable Audio 2.5 Text to Audio](../stable-audio-2-5-text-to-audio/SKILL.md) - Generate audio from text only
- [Stable Audio 2.5 Inpaint](../stable-audio-2-5-inpaint/SKILL.md) - Inpaint specific sections of audio
- [Minimax Music V1.5](../minimax-music-v1-5/SKILL.md) - Generate music with lyrics

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
