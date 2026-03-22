---
name: ai-aging-filter
description: "Apply age progression and regression effects to face photos using each::sense AI. Simulate how a person might look older or younger with realistic wrinkles, skin texture, hair changes, and facial structure adjustments. Use for: entertainment, social media content, age simulation, genealogy visualization, creative projects, character design. Triggers: aging filter, age progression, age regression, make older, make younger, old face, young face, age face, time lapse aging, age simulation, age effect, age transformation"
allowed-tools: Bash(curl *), WebFetch
---

# AI Aging Filter

Apply realistic age progression and regression effects to face photos using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Age the person in this photo to look about 75 years old. Add realistic wrinkles, age spots, gray hair, and slight sagging while keeping their identity clearly recognizable."
      }
    ],
    "image_urls": ["https://example.com/young-portrait.jpg"],
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
        "content": "Age the person in this photo to look about 75 years old. Add realistic wrinkles, age spots, gray hair, and slight sagging while keeping their identity clearly recognizable."
    }],
    extra_body={
        "image_urls": ["https://example.com/young-portrait.jpg"]
    }
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Make this person look 30 years older with natural aging effects, keeping their identity intact"}],
    "image_urls": ["https://example.com/portrait.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Age Transformation Guide

| Target Age | Key Visual Changes |
|---|---|
| **Child (5-10)** | Rounder face, bigger eyes relative to face, smoother skin, softer features |
| **Teen (13-17)** | Slimmer face, more defined jaw, smooth skin, youthful proportions |
| **Young Adult (25-30)** | Defined features, no wrinkles, full hair color, firm skin |
| **Middle-Aged (45-55)** | Crow's feet, nasolabial folds, slight gray, some skin laxity |
| **Senior (65-75)** | Deep wrinkles, gray/white hair, age spots, thinning skin |
| **Elderly (80+)** | Pronounced wrinkles, very thin skin, white hair, sunken features |

## Prompt Engineering Tips

### Specify Target Age

Be precise about the desired age rather than vague. "Make them look 70" is better than "make them look old."

```
Age the person in this photo to approximately [age]. [Specific changes]. Keep their identity recognizable.
```

### Aging Characteristics to Mention

```
wrinkles, crow's feet, forehead lines, nasolabial folds,
gray hair, white hair, thinning hair, receding hairline,
age spots, sun spots, sagging skin, jowls, under-eye bags
```

### De-aging Characteristics

```
smooth skin, fuller cheeks, no wrinkles, darker hair color,
tighter jawline, even skin tone, brighter eyes, youthful glow
```

## Examples

### Age Progression to Senior

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Transform this person to look about 80 years old. Add deep wrinkles across the forehead and around the eyes, white thinning hair, age spots on the temples, and slight jowls. The skin should look thinner and more translucent. Maintain their identity and expression."
      }
    ],
    "image_urls": ["https://example.com/adult-portrait.jpg"],
    "stream": false
  }'
```

### De-aging to Young Adult

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Make this person look 25 years old. Remove wrinkles, restore the hair to a natural dark color, tighten the jawline, smooth the skin, and brighten the eyes. Keep the same person recognizable but significantly younger."
      }
    ],
    "image_urls": ["https://example.com/older-person.jpg"],
    "stream": false
  }'
```

### Middle-Age Transformation

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Age this 20-something person to look about 50. Add subtle crow's feet, light forehead lines, salt-and-pepper hair at the temples, and very slight nasolabial folds. Keep it realistic and natural, not dramatic."
      }
    ],
    "image_urls": ["https://example.com/young-adult.jpg"],
    "stream": false
  }'
```

### Child Regression

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Transform this adult to look like a child around age 8. Round the face, make the eyes proportionally larger, remove all wrinkles and lines, add a childlike softness to the features. Keep enough resemblance to recognize this is the same person as a child."
      }
    ],
    "image_urls": ["https://example.com/adult-face.jpg"],
    "stream": false
  }'
```

## Workflow: Age Timeline Series

```bash
# Step 1: De-age to childhood
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Transform this person to look like a 10-year-old child. Round face, big eyes, smooth skin, childlike features, same identity."
      }
    ],
    "image_urls": ["https://example.com/current-photo.jpg"],
    "stream": false
  }'

# Step 2: Age to middle-aged
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Age this person to look approximately 50 years old. Subtle wrinkles, some gray hair, slight skin laxity, same identity."
      }
    ],
    "image_urls": ["https://example.com/current-photo.jpg"],
    "stream": false
  }'

# Step 3: Age to elderly
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Age this person to look approximately 85 years old. Deep wrinkles, white hair, thin skin, age spots, same identity."
      }
    ],
    "image_urls": ["https://example.com/current-photo.jpg"],
    "stream": false
  }'
```

## Input Photo Tips

- Use a clear, front-facing portrait with good lighting
- High resolution (at least 512x512 pixels)
- No sunglasses or heavy face obstructions
- Neutral expression gives the most natural aging results

## Related Skills

- [AI Face Restoration](../ai-face-restoration/SKILL.md) — Fix quality after transformation
- [AI Beauty Filter](../ai-beauty-filter/SKILL.md) — Enhance and smooth faces
- [AI Expression Editor](../ai-expression-editor/SKILL.md) — Change expression after aging
- [AI Caricature](../ai-caricature/SKILL.md) — Stylized cartoon versions
- [AI Face Swap](../ai-face-swap/SKILL.md) — Swap faces between photos

## Related Models

- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Context-aware image editing
- [pulid-flux](../../../models/pulid-flux/SKILL.md) — Identity-preserving generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative image generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
