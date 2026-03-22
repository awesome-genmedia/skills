---
name: ai-portrait-photo
description: "Generate studio-quality AI portrait photography using each::sense AI. Create editorial portraits, fashion photography, environmental portraits, and artistic character studies with professional lighting and composition. Supports various lighting setups, moods, and photographic styles. Use for: editorial photography, model portfolios, character portraits, artistic photography, fashion lookbooks, author photos. Triggers: ai portrait, portrait photography, studio portrait, editorial portrait, fashion portrait, artistic portrait, character portrait, portrait photo, ai photography, portrait session"
allowed-tools: Bash(curl *), WebFetch
---

# AI Portrait Photo

Generate studio-quality portrait photography using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Studio portrait of an elderly man with deep wrinkles and kind eyes, wearing a wool fisherman sweater, Rembrandt lighting, shallow depth of field, 85mm f/1.4 lens, medium format film grain, intimate close-up"
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
        "content": "Studio portrait of an elderly man with deep wrinkles and kind eyes, wearing a wool fisherman sweater, Rembrandt lighting, shallow depth of field, 85mm f/1.4 lens, medium format film grain, intimate close-up"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Use a reference photo for style matching or subject likeness:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a studio portrait of this person in the style of Annie Leibovitz. Dramatic side lighting, rich tones, dark background, contemplative expression, editorial quality"
      }
    ],
    "image_urls": ["https://example.com/reference-person.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Lighting Setups

| Setup | Description | Mood |
|-------|-------------|------|
| **Rembrandt** | 45-degree key light, triangle shadow on cheek | Dramatic, classic |
| **Butterfly** | Light directly above and in front | Glamorous, beauty |
| **Split** | Light from one side, half-face shadow | Moody, mysterious |
| **Broad** | Key light on the side closest to camera | Flattering, fills face |
| **Loop** | Small shadow of nose on cheek | Natural, versatile |
| **Rim/Edge** | Backlight outlining the subject | Dramatic, separation |
| **Natural Window** | Soft diffused side light | Intimate, warm |

## Lens and Camera Keywords

```
85mm f/1.4 — classic portrait lens, beautiful bokeh
135mm f/2 — compressed background, flattering proportions
50mm f/1.2 — natural field of view, cinematic
medium format — larger sensor look, shallow DOF
Hasselblad — medium format film quality
Kodak Portra 400 — warm skin tones, film look
Fuji Pro 400H — cooler tones, pastel film look
```

## Examples

### Editorial Fashion Portrait

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "High fashion editorial portrait of a model with slicked-back hair, wearing an oversized black blazer with nothing underneath, strong jawline, sharp cheekbones, dramatic side lighting, desaturated tones, Vogue editorial style, 135mm lens"
      }
    ],
    "stream": false
  }'
```

### Environmental Portrait

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Environmental portrait of a female ceramicist in her workshop, clay-dusted apron, natural light from a large window, pottery wheel and shelves of work visible in soft background, warm earthy tones, 50mm f/1.8, documentary style"
      }
    ],
    "stream": false
  }'
```

### Fine Art Portrait

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Fine art portrait inspired by Dutch Golden Age paintings. A woman in a deep blue velvet dress, pearl earring, chiaroscuro lighting, oil painting texture, rich dark background, three-quarter view, classical composition"
      }
    ],
    "stream": false
  }'
```

## Prompt Structure

```
[portrait type] of [subject description], [attire/styling], [lighting setup],
[background], [lens/camera], [mood/tone], [composition]
```

## Common Mistakes to Avoid

- **Skipping lighting details** — lighting defines the mood of a portrait more than anything else
- **Too many accessories** — keep styling simple; one statement piece works better
- **Ignoring background** — a busy background competes with the subject
- **Not specifying framing** — "close-up," "half-body," or "three-quarter" changes the feel dramatically

## Related Skills

- [AI Headshot Generator](../ai-headshot-generator/SKILL.md) — Professional headshots
- [AI Avatar Generator](../ai-avatar-generator/SKILL.md) — Stylized avatar portraits
- [AI Photo Enhancer](../ai-photo-enhancer/SKILL.md) — Improve portrait quality
- [Background Removal](../background-removal/SKILL.md) — Isolate portrait subjects

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for reference-based portraits
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
