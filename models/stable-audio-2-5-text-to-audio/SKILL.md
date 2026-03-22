---
name: "Stable Audio 2.5 Text to Audio"
description: "Generate audio from text descriptions using Stable Audio 2.5. Trigger: Use when the user wants to create audio from a text prompt, or requests 'text to audio', 'generate sound', 'stable audio', or 'create audio from description'."
allowed-tools: ["Bash"]
---

# Stable Audio 2.5 | Text to Audio

Generate audio clips from text descriptions. Create music, sound effects, ambient soundscapes, and more with controllable duration and quality.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-audio-2-5-text-to-audio",
    "version": "0.0.1",
    "input": {
      "prompt": "A cinematic orchestral score with rising strings and dramatic timpani",
      "seconds_total": 30,
      "guidance_scale": 1,
      "num_inference_steps": 8
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `guidance_scale` | integer | `1` | How strictly the diffusion process adheres to the prompt text (higher values keep closer to prompt) |
| `num_inference_steps` | integer | `8` | The number of steps to denoise the audio for |
| `prompt` | string | (empty) | The prompt to generate audio from |
| `seconds_total` | integer | `190` | The duration of the audio clip to generate |
| `seed` | integer | (empty) | Random seed for reproducibility |

## Output

- **Type:** audio

## Examples

### Sound Effect
```json
{
  "model": "stable-audio-2-5-text-to-audio",
  "version": "0.0.1",
  "input": {
    "prompt": "Thunder rumbling in the distance with heavy rain on a tin roof",
    "seconds_total": 15,
    "guidance_scale": 2,
    "num_inference_steps": 10
  }
}
```

### Background Music
```json
{
  "model": "stable-audio-2-5-text-to-audio",
  "version": "0.0.1",
  "input": {
    "prompt": "Lo-fi hip hop beat with vinyl crackle, mellow piano chords, and a slow drum loop",
    "seconds_total": 60,
    "guidance_scale": 1,
    "num_inference_steps": 8,
    "seed": 77
  }
}
```

### Ambient Soundscape
```json
{
  "model": "stable-audio-2-5-text-to-audio",
  "version": "0.0.1",
  "input": {
    "prompt": "Peaceful forest with birds singing, a gentle stream, and wind through leaves",
    "seconds_total": 120,
    "guidance_scale": 1,
    "num_inference_steps": 8
  }
}
```

## Related Models

- [Stable Audio 2.5 Audio to Audio](../stable-audio-2-5-audio-to-audio/SKILL.md) - Transform existing audio clips
- [Stable Audio 2.5 Inpaint](../stable-audio-2-5-inpaint/SKILL.md) - Inpaint sections of audio
- [Minimax Music V1.5](../minimax-music-v1-5/SKILL.md) - Generate music with lyrics

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
