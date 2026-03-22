---
name: ai-product-video-ad
description: "Create product showcase video ads using each::sense AI. Generate cinematic product reveal videos, unboxing sequences, feature highlight clips, and social media video ads for e-commerce marketing. Supports various formats for Instagram, TikTok, YouTube, and website hero videos. Use for: product launch videos, social media ads, DTC brand videos, Shopify hero videos, promotional clips, product demos. Triggers: product video, product ad video, video ad, product commercial, product showcase video, product promo, social media video ad, product reveal, unboxing video, commercial video"
allowed-tools: Bash(curl *), WebFetch
---

# AI Product Video Ad

Create product showcase video ads and promotional clips using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a product video ad: a sleek matte black wireless speaker slowly rotates on a reflective dark surface, studio lighting creating clean highlights on the curved edges. Camera slowly orbits around the product. Minimal, premium aesthetic, dark background with subtle blue accent light, 4K commercial quality"
      }
    ],
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
        "content": "Generate a product video ad: a sleek matte black wireless speaker slowly rotates on a reflective dark surface, studio lighting creating clean highlights on the curved edges. Camera slowly orbits around the product. Minimal, premium aesthetic, dark background with subtle blue accent light, 4K commercial quality"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide your product photo to animate it:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a product video ad from this product image. The product smoothly descends into frame from above and lands softly on a marble surface. Camera pushes in slowly for a close-up. Dramatic studio lighting, premium feel, commercial video quality."},
              {"type": "image_url", "image_url": {"url": "https://example.com/my-product.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Video Ad Formats

| Format | Aspect Ratio | Duration | Platform |
|--------|-------------|----------|----------|
| **Instagram Reel** | 9:16 vertical | 15-30s | Instagram, TikTok |
| **YouTube Pre-Roll** | 16:9 horizontal | 6-15s | YouTube |
| **Website Hero** | 16:9 horizontal | 5-15s (loop) | Shopify, brand sites |
| **Story Ad** | 9:16 vertical | 5-15s | Instagram, Snapchat |
| **Square Social** | 1:1 square | 15-30s | Facebook, Instagram feed |

## Shot Types for Product Videos

| Shot | Motion | Effect |
|------|--------|--------|
| **Product Orbit** | camera circles the static product | shows all angles, premium feel |
| **Drop Reveal** | product falls/descends into frame | dramatic entrance |
| **Push-In** | camera moves toward product | draws attention to detail |
| **Turntable** | product rotates on a platform | 360-degree view |
| **Lifestyle Cut** | product in use by a person | context and aspiration |
| **Macro Detail** | extreme close-up gliding over surface | texture and craft |
| **Exploded View** | components separate and reassemble | engineering / feature callout |

## Prompt Engineering Tips

### Prompt Structure

```
"Generate a product video ad:" + [product description] + [motion/animation] + [camera movement] + [setting and lighting] + [mood and quality]
```

### Motion Keywords

```
slowly rotates, gently descends, smoothly slides into frame,
orbiting camera, push-in close-up, tracking alongside,
parallax movement, subtle floating hover, product assembling
```

### Lighting for Video

```
studio three-point lighting, dramatic rim light,
soft diffused top light, colored accent backlight,
natural golden hour, high-key bright and clean,
low-key dark and moody, volumetric light beams
```

## Examples

### Skincare Product Reveal

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a product video ad for a luxury skincare serum: a frosted glass bottle with a gold dropper cap descends slowly through soft mist onto a white marble surface. A single water droplet falls onto the marble and ripples outward. Camera pushes in to a close-up of the dropper releasing a golden serum drop. Soft diffused lighting, clean white and gold palette, luxurious spa aesthetic, 9:16 vertical format for Instagram."
      }
    ],
    "stream": false
  }'
```

### Tech Product Launch

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a product video ad for a smartwatch: starts with a dark screen, a beam of light sweeps across revealing the watch face glowing on a dark surface. Camera orbits around the watch showing the slim profile and metal band. The screen lights up showing a fitness dashboard. Sleek modern tech aesthetic, dark background with blue accent lighting, cinematic lens flare, Apple-style product commercial, 16:9 landscape."
      }
    ],
    "stream": false
  }'
```

### Food Product Social Ad

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a product video ad for artisanal chocolate bars: a hand slowly unwraps gold foil to reveal a dark chocolate bar, then breaks it in half with a satisfying snap. Close-up of the cross-section showing rich texture. Melted chocolate drizzles in the background. Warm moody lighting, dark wood surface, premium food photography video style, slow motion detail, 1:1 square format."
      }
    ],
    "stream": false
  }'
```

### Sneaker Drop Announcement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a product video ad for a sneaker release: a pair of white and neon green sneakers drops from above and lands on a concrete surface with a puff of powder. Camera orbits around the shoes at ground level, showing the sole tread and knit upper texture. Urban graffiti wall in the blurred background. Streetwear aesthetic, bass-heavy energy feel, dynamic camera, 9:16 vertical for TikTok."
      }
    ],
    "stream": false
  }'
```

## Multi-Scene Ad Workflow

```bash
PRODUCT="a premium leather wallet in cognac brown"
STYLE="warm studio lighting, dark background, luxury commercial quality"

SCENES=(
  "Scene 1 — Reveal: the wallet slowly slides into frame on a dark leather surface, camera positioned low, dramatic side lighting"
  "Scene 2 — Detail: extreme close-up tracking along the wallet edge showing hand-stitched seams and grain texture"
  "Scene 3 — Feature: the wallet opens to reveal card slots, a person's hand slides a card in and out smoothly"
  "Scene 4 — Lifestyle: a well-dressed man at a restaurant table casually places the wallet beside a glass of whiskey, shallow depth of field"
  "Scene 5 — End card: the wallet centered on a dark surface, camera slowly pulling back, space for text overlay"
)

for SCENE in "${SCENES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Generate a product video ad clip: $PRODUCT. $SCENE. $STYLE\"}],
      \"stream\": false
    }"
  echo "=== SCENE ==="
done
```

## Post-Production Assembly

AI generates individual clips. To create a complete ad:

1. **Generate 3-6 scene clips** covering reveal, detail, lifestyle, and end card
2. **Sequence in a video editor** — add transitions, adjust timing
3. **Add text overlays** — product name, features, price, CTA (AI text is unreliable)
4. **Layer music and sound** — choose tracks matching the brand mood
5. **Export for platform** — correct aspect ratio and duration per platform

## Common Pitfalls

- **Text and logos** will not render correctly in video. Add all text in post-production.
- **Too much motion** in one clip — keep each clip focused on one movement or action.
- **Product inconsistency** — describe the product identically across all scenes for visual coherence.
- **Missing end card space** — always generate a final shot with clean negative space for text overlays.
- **Audio** is not generated — plan for music and sound design separately.

## Related Skills

- [AI Product Photo](../ai-product-photo/SKILL.md) — Still product photography
- [AI Product Mockup](../ai-product-mockup/SKILL.md) — Product mockups
- [AI Lifestyle Photo](../ai-lifestyle-photo/SKILL.md) — Products in real settings
- [AI Catalog Generator](../ai-catalog-generator/SKILL.md) — Full catalog imagery

## Related Models

- [wan-2-1](../../../models/wan-2-1/SKILL.md) — High quality video generation
- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image stills
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
