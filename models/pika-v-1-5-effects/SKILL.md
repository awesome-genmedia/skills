---
name: pika-v-1-5-effects
description: "Pika v1.5 | Effects. Apply creative visual effects to images using Pika v1.5 AI. Transform images with effects like explode, melt, inflate, squish, and more. Triggers: pika effects, pikaffect, image effects, creative effects, explode effect, melt effect, inflate effect, pika v1.5"
allowed-tools: Bash(curl *), WebFetch
---

# Pika v1.5 | Effects

Apply creative visual effects to images using Pika v1.5. Choose from a wide range of fun and dramatic effects like Explode, Melt, Inflate, Squish, Dissolve, and many more to bring still images to life as animated videos.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v-1-5-effects",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "pikaffect": "Explode",
      "prompt": "dramatic explosion with debris"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | - | URL of the input image |
| negative_prompt | string | - | Text describing what to avoid in the output |
| pikaffect | string | Squish | Effect to apply. Options: `Cake-ify`, `Crumble`, `Crush`, `Decapitate`, `Deflate`, `Dissolve`, `Explode`, `Eye-pop`, `Inflate`, `Levitate`, `Melt`, `Peel`, `Poke`, `Squish`, `Ta-da`, `Tear` |
| prompt | string | - | Text prompt to guide the effect |
| seed | integer | - | Random seed for reproducible results |

## Examples

**Melt effect on a sculpture:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v-1-5-effects",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/ice-sculpture.jpg",
      "pikaffect": "Melt",
      "prompt": "slowly melting into a puddle"
    }
  }'
```

**Inflate effect on a character:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v-1-5-effects",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/cartoon-character.png",
      "pikaffect": "Inflate",
      "prompt": "inflating like a balloon",
      "seed": 12345
    }
  }'
```

**Cake-ify effect on an object:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v-1-5-effects",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sneaker.jpg",
      "pikaffect": "Cake-ify",
      "prompt": "turning into a delicious cake"
    }
  }'
```

## Related Models

- [Cartoonify V2](../cartoonify-v2/) - Convert images to cartoon style
- [Google Veo 3](../veo-3/) - Text-to-video generation
- [PixVerse v4.5 | Extend](../pixverse-v4-5-extend/) - Extend video duration

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
