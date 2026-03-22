---
name: ai-qr-code-generator
description: "Generate artistic AI QR codes that remain scannable using each::sense AI. Create QR codes integrated into beautiful artwork, landscapes, abstract designs, and brand visuals while maintaining scan functionality. Supports various artistic styles and branding integration. Use for: marketing materials, business cards, restaurant menus, event tickets, branded links, packaging, social media. Triggers: ai qr code, artistic qr code, qr code generator, creative qr code, beautiful qr code, branded qr code, qr art, custom qr code, design qr code, scannable art"
allowed-tools: Bash(curl *), WebFetch
---

# AI QR Code Generator

Generate artistic QR codes that remain scannable using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate an artistic QR code for the URL https://eachlabs.ai. Style: a Japanese zen garden with raked sand patterns, cherry blossom trees, and a small koi pond. The QR code pattern should be integrated into the garden layout. Must remain scannable."
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
        "content": "Generate an artistic QR code for the URL https://eachlabs.ai. Style: a Japanese zen garden with raked sand patterns, cherry blossom trees, and a small koi pond. The QR code pattern should be integrated into the garden layout. Must remain scannable."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Use a brand image or style reference for the QR code design:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Generate a scannable QR code for https://eachlabs.ai using this image as the artistic style reference. Integrate the QR pattern into the visual design while keeping it functional."},
              {"type": "image_url", "image_url": {"url": "https://example.com/brand-artwork.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Art Styles for QR Codes

| Style | Description | Best For |
|-------|-------------|----------|
| **Nature Landscape** | Mountains, forests, gardens | Tourism, wellness, outdoors |
| **Urban/Architecture** | City skyline, buildings, streets | Real estate, urban brands |
| **Abstract Geometric** | Patterns, fractals, shapes | Tech companies, modern brands |
| **Watercolor/Painterly** | Soft brushstrokes, organic flow | Art galleries, creative studios |
| **Cyberpunk/Neon** | Glowing lines, circuit patterns | Tech events, gaming |
| **Food/Culinary** | Ingredients, dishes, kitchen | Restaurants, food delivery |
| **Floral** | Flowers, botanical illustrations | Weddings, beauty, fashion |

## Examples

### Coffee Shop Menu QR

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a scannable artistic QR code for https://menu.example.com. Style: warm coffee-themed artwork with latte art swirls, coffee beans, and steam rising from a cup. Earthy brown and cream color palette. The QR pattern should blend into the coffee imagery."
      }
    ],
    "stream": false
  }'
```

### Tech Event QR

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a scannable QR code for https://event.example.com. Style: cyberpunk circuit board design with glowing blue and purple neon traces, microchip patterns, and digital particles. Dark background with luminous QR code integration."
      }
    ],
    "stream": false
  }'
```

### Wedding Invitation QR

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate an elegant scannable QR code for https://rsvp.example.com. Style: romantic floral design with white roses, peonies, and delicate gold leaf accents. Soft blush pink and ivory palette. The QR code should be woven into the botanical illustration."
      }
    ],
    "stream": false
  }'
```

## Scannability Tips

- **Always test the output** with a QR scanner before using in production
- **Maintain contrast**: The QR pattern needs sufficient contrast against the artwork to scan
- **Keep the three corner squares** (finder patterns) clearly visible — they are critical for scanning
- **Avoid very dark themes** where the QR modules blend into the background
- **Print at adequate size**: Artistic QR codes need at least 3x3 cm (1.2x1.2 in) for reliable scanning
- **Simpler URLs scan better**: Short URLs produce simpler QR patterns that integrate more cleanly

## Prompt Structure

```
Generate a scannable artistic QR code for [URL].
Style: [art theme/description].
Color palette: [colors].
The QR code should [integration description].
Must remain scannable.
```

## Related Skills

- [Text to Image](../text-to-image/SKILL.md) — General image generation
- [AI Pattern Generator](../ai-pattern-generator/SKILL.md) — Seamless patterns and textures

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
