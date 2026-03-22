---
name: "Moonvalley Marey Text to Video"
description: "Generate videos from text using Moonvalley Marey. Trigger: Use when the user wants to create a video with Moonvalley, or requests 'moonvalley video', 'marey text to video', or 'moonvalley marey'."
allowed-tools: ["Bash"]
---

# Moonvalley | Marey | Text to Video

Generate high-quality videos from text prompts using Moonvalley's Marey model. Supports multiple dimensions, durations, and detailed negative prompts.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "moonvalley-marey-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A timelapse of a flower blooming in a garden, soft natural light",
      "dimensions": "1920x1080",
      "duration": "5s"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `dimensions` | string | `1920x1080` | Video dimensions. Options: `1920x1080`, `1152x1152`, `1536x1152`, `1152x1536` |
| `duration` | string | `5s` | Video duration. Options: `5s`, `10s` |
| `negative_prompt` | string | *(long default)* | Negative prompt to avoid undesirable features. Has a detailed default value |
| `prompt` | string | `false` | The prompt to generate a video from |
| `seed` | integer | `false` | Random seed for reproducibility |

## Output

- **Type:** video

## Examples

### Cinematic Nature Scene
```json
{
  "model": "moonvalley-marey-text-to-video",
  "version": "0.0.1",
  "input": {
    "prompt": "A majestic waterfall cascading into a crystal clear pool surrounded by lush tropical vegetation, cinematic drone shot",
    "dimensions": "1920x1080",
    "duration": "10s"
  }
}
```

### Square Format Animation
```json
{
  "model": "moonvalley-marey-text-to-video",
  "version": "0.0.1",
  "input": {
    "prompt": "Abstract colorful paint swirling and mixing in slow motion, mesmerizing fluid dynamics",
    "dimensions": "1152x1152",
    "duration": "5s",
    "seed": 42
  }
}
```

### Portrait Video
```json
{
  "model": "moonvalley-marey-text-to-video",
  "version": "0.0.1",
  "input": {
    "prompt": "A woman walking through a rain-soaked neon-lit city street at night, reflections on the wet pavement",
    "dimensions": "1152x1536",
    "duration": "5s"
  }
}
```

## Related Models

- [Runway Gen4 Aleph](../runway-gen4-aleph/SKILL.md) - Alternative text-to-video
- [PixVerse v5 Text to Video](../pixverse-v5-text-to-video/SKILL.md) - PixVerse video generation
- [Wan v2.2 A14B Text to Video Turbo](../wan-v2-2-a14b-text-to-video-turbo/SKILL.md) - Fast text-to-video

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
