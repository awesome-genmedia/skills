---
name: change-haircut
description: "Hairstyle Changer. Change hairstyles and hair color in photos using AI. Try different haircuts and colors on any portrait. Triggers: change hairstyle, haircut changer, hair color change, hairstyle ai, try hairstyle, virtual haircut, hair makeover, change hair"
allowed-tools: Bash(curl *), WebFetch
---

# Hairstyle Changer

Change hairstyles and hair color in photos using AI. Upload a portrait and select from dozens of hairstyle options and 30+ hair colors to preview different looks before committing to a change.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "change-haircut",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/selfie.jpg",
      "haircut": "Bob",
      "hair_color": "Platinum Blonde"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Output aspect ratio. Options: `1:1`, `16:9`, `9:16`, `4:3`, `3:4`, `3:2`, `2:3`, `4:5`, `5:4`, `21:9`, `9:21`, `2:1`, `1:2` |
| gender | string | none | Gender hint. Options: `none`, `male`, `female` |
| hair_color | string | No change | Hair color. Options include: `No change`, `Random`, `Blonde`, `Brunette`, `Black`, `Dark Brown`, `Medium Brown`, `Light Brown`, `Auburn`, `Copper`, `Red`, `Strawberry Blonde`, `Platinum Blonde`, `Silver`, `White`, `Blue`, `Purple`, `Pink`, `Green`, `Rose Gold`, and more |
| haircut | string | No change | Hairstyle. Options include: `No change`, `Random`, `Straight`, `Wavy`, `Curly`, `Bob`, `Pixie Cut`, `Layered`, `Messy Bun`, `High Ponytail`, `French Braid`, `Undercut`, `Mohawk`, `Crew Cut`, `Slicked Back`, `Side-Parted`, `Blunt Bangs`, `Shag`, `Lob`, `Dreadlocks`, `Cornrows`, `Box Braids`, `Chignon`, `Beehive`, `Victory Rolls`, and many more |
| input_image | string | - | Image of the person. Must be jpeg, png, or webp |
| output_format | string | png | Output format. Options: `jpg`, `png` |
| safety_tolerance | integer | 2 | Safety tolerance, 0 is most strict and 2 is most permissive |
| seed | integer | - | Random seed for reproducible generation |

## Examples

**Try a pixie cut with auburn color:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "change-haircut",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/portrait.jpg",
      "haircut": "Pixie Cut",
      "hair_color": "Auburn",
      "gender": "female",
      "output_format": "png"
    }
  }'
```

**Try a slicked back style for men:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "change-haircut",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/male-photo.jpg",
      "haircut": "Slicked Back",
      "hair_color": "Dark Brown",
      "gender": "male"
    }
  }'
```

**Random hairstyle and color:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "change-haircut",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/face.jpg",
      "haircut": "Random",
      "hair_color": "Random",
      "seed": 42
    }
  }'
```

## Related Models

- [Cartoonify V2](../cartoonify-v2/) - Convert photos to cartoon style
- [Faceswap | Video](../faceswap-video/) - Swap faces in videos
- [Flux.1 Kontext | Pro](../flux-kontext-pro/) - AI image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
