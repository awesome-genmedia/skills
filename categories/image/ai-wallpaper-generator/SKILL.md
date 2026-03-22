---
name: ai-wallpaper-generator
description: "Generate desktop and mobile wallpapers using each::sense AI. Create stunning backgrounds for phones, tablets, desktops, and ultrawide monitors in any style from abstract gradients to photorealistic landscapes. Supports all common device resolutions and aspect ratios. Use for: phone wallpapers, desktop backgrounds, lock screens, ultrawide monitors, tablet backgrounds, dual monitor setups. Triggers: ai wallpaper, wallpaper generator, desktop background, phone wallpaper, mobile wallpaper, lock screen, create wallpaper, custom wallpaper, background image, screen background, aesthetic wallpaper"
allowed-tools: Bash(curl *), WebFetch
---

# AI Wallpaper Generator

Generate stunning desktop and mobile wallpapers using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a desktop wallpaper: a bioluminescent forest at night with glowing mushrooms, fireflies, and a narrow path winding through ancient moss-covered trees. Deep blues and teals with bright cyan bioluminescence. 16:9 aspect ratio, 4K quality."
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
        "content": "Generate a desktop wallpaper: a bioluminescent forest at night with glowing mushrooms, fireflies, and a narrow path winding through ancient moss-covered trees. Deep blues and teals with bright cyan bioluminescence. 16:9 aspect ratio, 4K quality."
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Device Resolutions

| Device | Resolution | Aspect Ratio |
|--------|-----------|--------------|
| **iPhone** | 1290x2796 | 9:19.5 |
| **Android Phone** | 1080x2400 | 9:20 |
| **iPad** | 2048x2732 | 3:4 |
| **Desktop 1080p** | 1920x1080 | 16:9 |
| **Desktop 4K** | 3840x2160 | 16:9 |
| **Ultrawide** | 3440x1440 | 21:9 |
| **MacBook** | 2880x1800 | 16:10 |
| **Dual Monitor** | 7680x2160 | 32:9 |

## Wallpaper Styles

| Style | Keywords |
|-------|----------|
| **Abstract Gradient** | smooth gradient, color transition, flowing shapes |
| **Nature Photography** | landscape, mountains, ocean, forest, photorealistic |
| **Minimalist** | clean, simple, single subject, lots of negative space |
| **Dark/OLED** | dark background, deep black, AMOLED friendly |
| **Geometric** | geometric shapes, triangles, hexagons, low-poly |
| **Space** | nebula, galaxy, stars, cosmic, aurora |
| **Anime/Illustrated** | anime scenery, digital painting, fantasy landscape |

## Examples

### Phone Wallpaper (OLED Dark)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Phone wallpaper in 9:20 portrait ratio. Deep black AMOLED background with a single glowing jellyfish in the center, bioluminescent tentacles trailing down, subtle purple and pink glow, minimalist, no other elements."
      }
    ],
    "stream": false
  }'
```

### Ultrawide Desktop

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Ultrawide 21:9 desktop wallpaper. Vast mountain panorama at golden hour, snow-capped peaks stretching across the entire frame, a crystal-clear alpine lake in the foreground reflecting the mountains, warm golden light, photorealistic landscape photography."
      }
    ],
    "stream": false
  }'
```

### Abstract Minimalist

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Desktop wallpaper 16:9. Minimalist abstract composition with soft flowing shapes in muted earth tones — terracotta, sand, sage green, warm cream. Smooth gradients, no sharp edges, calming and professional. Clean enough that desktop icons remain readable."
      }
    ],
    "stream": false
  }'
```

### Seasonal Wallpaper Set

```bash
SEASONS=(
  "Spring: cherry blossom trees along a gentle stream, pink petals floating on the water, soft morning light"
  "Summer: tropical beach at sunset, palm tree silhouettes, warm orange and magenta sky, calm turquoise water"
  "Autumn: a winding forest path covered in red and golden fallen leaves, misty atmosphere, warm sunlight filtering through trees"
  "Winter: a cozy cabin in the woods covered in fresh snow, warm light glowing from windows, northern lights in the sky"
)

for SEASON in "${SEASONS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Desktop wallpaper 16:9, 4K quality. $SEASON. Photorealistic, stunning landscape photography.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Wallpaper Design Tips

- **Specify the aspect ratio** in every prompt — it dramatically affects composition
- **Keep the center clean** for phone wallpapers (clock, widgets sit there)
- **Dark wallpapers save battery** on OLED screens — mention "AMOLED-friendly deep black"
- **Avoid text and small details** that get obscured by desktop icons
- **Include "4K quality"** for crisp results on high-DPI displays
- **Gradients and simple compositions** keep your desktop looking clean and professional

## Related Skills

- [Text to Image](../text-to-image/SKILL.md) — General image generation
- [AI Pattern Generator](../ai-pattern-generator/SKILL.md) — Seamless patterns
- [Image Upscaling](../image-upscaling/SKILL.md) — Upscale to higher resolutions
- [AI Photo Enhancer](../ai-photo-enhancer/SKILL.md) — Enhance wallpaper quality

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
