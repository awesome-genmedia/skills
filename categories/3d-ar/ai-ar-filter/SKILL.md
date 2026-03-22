---
name: ai-ar-filter
description: "Generate AR face filters and effects using each::sense AI. Create augmented reality face overlays, masks, makeup effects, character transformations, and decorative face filters for social media, apps, and entertainment. Use for: social media filters, face effects, AR masks, character face filters, beauty filters, novelty effects. Triggers: ar filter, face filter, face effect, ar mask, ar face, snapchat filter, instagram filter, face overlay, augmented reality filter, face transformation"
allowed-tools: Bash(curl *), WebFetch
---

# AI AR Filter

Generate augmented reality face filters and effects using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply an AR filter effect to this face photo: add glowing butterfly wings framing the face, tiny floating sparkles around the head, and soft pastel rainbow light streaks across the cheeks. Dreamy ethereal effect, high quality, natural face preserved underneath."
      }
    ],
    "image_urls": ["https://example.com/selfie.jpg"],
    "stream": false
  }'
```

### Using Python (OpenAI SDK)

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

response = client.chat.completions.create(
    model="eachsense/beta",
    messages=[{
        "role": "user",
        "content": "Apply an AR filter effect to this face photo: add glowing butterfly wings framing the face, tiny floating sparkles around the head, and soft pastel rainbow light streaks across the cheeks. Dreamy ethereal effect, high quality, natural face preserved underneath."
    }],
    extra_body={
        "image_urls": ["https://example.com/selfie.jpg"]
    }
)

print(response.choices[0].message.content)
```

### With Reference Image

This skill is inherently image-driven. Provide a face photo to apply the filter to:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply this AR filter style from the second image onto the face in the first image. Match the same overlay elements, color effects, and positioning. Preserve the original face features naturally."
      }
    ],
    "image_urls": [
      "https://example.com/my-selfie.jpg",
      "https://example.com/filter-reference.jpg"
    ],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Filter Categories

| Category | Examples | Mood |
|----------|----------|------|
| **Beauty / Glamour** | soft skin, light blush, eye enhancement, lip color | polished, refined |
| **Fantasy / Mythical** | elf ears, fairy wings, crown of flowers, glowing eyes | magical, whimsical |
| **Animal Faces** | cat ears and nose, puppy face, fox features, bunny | cute, playful |
| **Seasonal** | snowflakes, autumn leaves, cherry blossoms, fireworks | festive, thematic |
| **Horror / Dark** | zombie skin, vampire fangs, cracked porcelain, black eyes | spooky, edgy |
| **Character Transform** | comic book style, pixel face, oil painting effect, clay face | artistic, novelty |
| **Cultural** | Day of the Dead face paint, Holi powder, carnival mask | cultural, celebratory |
| **Decorative** | flower crowns, neon face paint, geometric overlays, starlight | decorative, fun |

## Prompt Engineering Tips

### Prompt Structure

```
"Apply an AR filter effect to this face photo:" + [overlay elements] + [color/light effects] + [positioning relative to face] + [mood/style] + [preservation note]
```

### Always Preserve the Face

Include phrasing like:
```
"Preserve the original face features, identity, and expression naturally underneath the filter."
```

### Effect Placement Keywords

```
around the face, framing the head, on the cheeks,
across the forehead, over the eyes, around the hairline,
floating above the head, extending from the ears,
along the jawline, covering the lower face
```

## Examples

### Neon Cyberpunk Filter

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply a cyberpunk AR filter to this face: neon circuit-board line patterns glowing in cyan across the cheeks and forehead, one eye replaced with a red cybernetic lens, holographic data readout floating next to the head, and a subtle neon purple underglow. Dark moody lighting, high-tech aesthetic, face identity preserved."
      }
    ],
    "image_urls": ["https://example.com/portrait.jpg"],
    "stream": false
  }'
```

### Floral Crown Beauty Filter

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply a beauty AR filter to this selfie: a lush flower crown of pink peonies, white daisies, and green eucalyptus leaves resting on the head. Soft skin smoothing, subtle rosy blush on cheeks, bright sparkling eyes. Warm golden light filter over the entire image, soft bokeh background. Natural and elegant."
      }
    ],
    "image_urls": ["https://example.com/selfie.jpg"],
    "stream": false
  }'
```

### Comic Book Effect

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Transform this face photo into a comic book AR effect: bold black ink outlines around facial features, halftone dot shading on skin, exaggerated contrast, vibrant pop art color palette. Comic-style speech bubble floating next to the head (empty for text). Retro comic book aesthetic, face structure preserved."
      }
    ],
    "image_urls": ["https://example.com/face-photo.jpg"],
    "stream": false
  }'
```

### Holiday Themed Filter

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply a winter holiday AR filter to this face photo: a cozy knit Santa hat on the head, soft snowflakes falling in the foreground, a warm red nose glow, frost crystals forming at the edges of the frame, and a subtle warm golden light. Cheerful festive mood, face naturally preserved."
      }
    ],
    "image_urls": ["https://example.com/winter-selfie.jpg"],
    "stream": false
  }'
```

## Batch Workflow: Filter Pack

```bash
FACE_PHOTO="https://example.com/model-face.jpg"

FILTERS=(
  "golden goddess: metallic gold face paint patterns on cheekbones and forehead, gold leaf flakes in hair, warm amber glow"
  "ice queen: frost crystals spreading from temples, pale blue lip color, snowflake particles, cold blue lighting"
  "neon butterfly: glowing neon butterfly wings extending from the sides of the face, pink and purple light trails, dark background"
  "vintage film: soft warm grain overlay, light leaks in corners, slightly desaturated colors, retro 1970s Polaroid feel"
  "galaxy face: cosmic nebula pattern blending across the skin, tiny stars scattered over the cheeks, deep purple and blue tones"
)

for FILTER in "${FILTERS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Apply an AR filter to this face photo: $FILTER. Preserve the original face identity and features naturally. High quality.\"}],
      \"image_urls\": [\"$FACE_PHOTO\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Face distortion** — without the preservation instruction, the AI may alter facial features too aggressively.
- **Overlay misalignment** — specify where elements go relative to facial landmarks (eyes, cheeks, forehead, hairline).
- **Multiple faces** in one photo — specify which face to apply the filter to, or crop to a single face.
- **Static output** — AI generates still images, not animated AR filters. For animated effects, generate key frames and animate in post.
- **Text in filters** — speech bubbles and text overlays will have garbled text. Add text in post-production.

## Related Skills

- [AI 3D Model Generator](../ai-3d-model-generator/SKILL.md) — 3D mask and prop creation
- [AI Texture Generator](../ai-texture-generator/SKILL.md) — Face paint and overlay textures
- [Image to 3D](../image-to-3d/SKILL.md) — Convert face accessories to 3D
- [AI Fashion Lookbook](../../fashion/ai-fashion-lookbook/SKILL.md) — Complete styled looks

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image-guided edits
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
