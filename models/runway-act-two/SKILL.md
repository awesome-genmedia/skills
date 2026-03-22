---
name: "Runway Act-Two"
description: "Generate performance-driven character animation videos with Runway Act-Two. Trigger: Use when the user wants to animate a character with expressions, or requests 'runway act two', 'character animation', 'expression-driven video', or 'act two'."
allowed-tools: ["Bash"]
---

# Runway | Act-Two

Generate character animation videos driven by a reference performance. Control expression intensity, body movement, and character type for expressive video outputs.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "runway-act-two",
    "version": "0.0.1",
    "input": {
      "character_uri": "https://example.com/character.jpg",
      "reference_uri": "https://example.com/performance-reference.mp4",
      "character_type": "image",
      "aspect_ratio": "1280:720",
      "expression_intensity": 3,
      "body_control": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | `false` | Aspect ratio. Options: `1280:720`, `720:1280`, `960:960`, `1104:832`, `832:1104`, `1584:672` |
| `body_control` | boolean | `true` | Enable body movement control |
| `character_type` | string | `image` | Character input type. Options: `video`, `image` |
| `character_uri` | string | `false` | URL of the character image or video |
| `expression_intensity` | integer | `3` | Expression intensity level |
| `public_figure_moderation` | string | `low` | Moderation level. Options: `auto`, `low` |
| `reference_uri` | string | `false` | URL of the reference performance video |
| `seed` | integer | `false` | Random seed for reproducibility |

## Output

- **Type:** video

## Examples

### Image Character Animation
```json
{
  "model": "runway-act-two",
  "version": "0.0.1",
  "input": {
    "character_uri": "https://example.com/portrait.jpg",
    "reference_uri": "https://example.com/acting-reference.mp4",
    "character_type": "image",
    "aspect_ratio": "1280:720",
    "expression_intensity": 4,
    "body_control": true
  }
}
```

### Video Character with Subtle Expressions
```json
{
  "model": "runway-act-two",
  "version": "0.0.1",
  "input": {
    "character_uri": "https://example.com/character-clip.mp4",
    "reference_uri": "https://example.com/subtle-performance.mp4",
    "character_type": "video",
    "aspect_ratio": "960:960",
    "expression_intensity": 2,
    "body_control": false,
    "seed": 55
  }
}
```

## Related Models

- [Runway Gen4 Aleph](../runway-gen4-aleph/SKILL.md) - Text-to-video generation
- [EchoMimic V3](../echomimic-v3/SKILL.md) - Audio-driven talking head
- [Character 3](../character-3/SKILL.md) - Audio-driven character video

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
