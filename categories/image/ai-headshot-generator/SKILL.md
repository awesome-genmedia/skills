---
name: ai-headshot-generator
description: "Generate professional AI headshots using each::sense AI. Create LinkedIn-ready portraits, corporate team photos, and business profile pictures from selfies or text descriptions. Supports formal, creative, and casual business styles with studio-quality lighting. Use for: LinkedIn profile photos, corporate headshots, team page portraits, business cards, professional bios, speaker profiles. Triggers: ai headshot, professional headshot, linkedin photo, corporate portrait, business headshot, profile photo, team headshot, professional photo, executive portrait, headshot generator"
allowed-tools: Bash(curl *), WebFetch
---

# AI Headshot Generator

Generate professional headshots for LinkedIn, corporate profiles, and business use using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Professional corporate headshot of a confident woman in her 30s, wearing a navy blazer over a white blouse, soft studio lighting, neutral gray background, sharp focus on face, shoulders up, warm natural smile, DSLR quality"
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
        "content": "Professional corporate headshot of a confident woman in her 30s, wearing a navy blazer over a white blouse, soft studio lighting, neutral gray background, sharp focus on face, shoulders up, warm natural smile, DSLR quality"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Photo

Upload a selfie or casual photo to generate a professional headshot version:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Transform this photo into a professional corporate headshot. Keep the same person, add studio lighting, neutral background, professional attire, shoulders-up framing, sharp focus"},
              {"type": "image_url", "image_url": {"url": "https://example.com/my-selfie.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Headshot Styles

| Style | Description | Best For |
|-------|-------------|----------|
| **Corporate Formal** | Suit/blazer, neutral background, traditional lighting | Finance, law, consulting |
| **Business Casual** | Smart-casual attire, warm tones, approachable | Tech, marketing, startups |
| **Creative Professional** | Bold colors, environmental background, personality | Design, media, entertainment |
| **Medical/Clinical** | White coat, clinical setting, trustworthy | Healthcare professionals |
| **Academic** | Office/library background, intellectual warmth | Professors, researchers |

## Prompt Tips

### What Makes a Great Headshot Prompt

```
Professional headshot + [subject description] + [attire] + [lighting] + [background] + [framing] + [expression]
```

### Background Options

- `neutral gray background` — safest, works everywhere
- `soft white background` — clean, modern
- `blurred office environment` — contextual, professional
- `outdoor bokeh` — approachable, creative
- `dark charcoal background` — dramatic, executive

### Lighting Keywords

- `soft studio lighting` — even, flattering
- `Rembrandt lighting` — dramatic, executive
- `butterfly lighting` — glamorous, beauty
- `natural window light` — approachable, warm
- `rim light with soft fill` — separation from background

## Examples

### LinkedIn Executive Portrait

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Executive headshot of a man in his 50s, silver hair, wearing a charcoal suit with a burgundy tie, Rembrandt lighting, dark background, confident expression, head and shoulders, 85mm lens look, sharp eyes"
      }
    ],
    "stream": false
  }'
```

### Startup Founder Casual

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Business casual headshot of a young man in a dark crew-neck sweater, natural window lighting from the left, blurred modern office background, genuine smile, upper body, clean-shaven, approachable and confident"
      }
    ],
    "stream": false
  }'
```

### Creative Professional

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Creative professional headshot of a woman with colorful braids, wearing a black turtleneck, bold teal background, soft directional lighting, artistic but professional, editorial quality, slight smile"
      }
    ],
    "stream": false
  }'
```

## Team Headshot Batch

Generate consistent headshots for a team page:

```bash
# Use the same style parameters for consistency
STYLE="soft studio lighting, neutral gray background, shoulders up, professional, 85mm portrait lens, DSLR quality"

DESCRIPTIONS=(
  "Professional headshot of a woman in her 30s, dark hair, navy blazer, $STYLE"
  "Professional headshot of a man in his 40s, glasses, light blue dress shirt, $STYLE"
  "Professional headshot of a young woman, curly hair, white blouse, $STYLE"
)

for DESC in "${DESCRIPTIONS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$DESC\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Output Specifications

| Platform | Recommended Size | Aspect Ratio |
|----------|-----------------|--------------|
| LinkedIn | 400x400 px | 1:1 |
| Corporate Website | 600x800 px | 3:4 |
| Email Signature | 200x200 px | 1:1 |
| Business Card | 300x400 px | 3:4 |
| Slack/Teams Avatar | 512x512 px | 1:1 |

## Related Skills

- [AI Portrait Photo](../ai-portrait-photo/SKILL.md) — Studio-quality portrait photography
- [AI Avatar Generator](../ai-avatar-generator/SKILL.md) — Stylized avatars from photos
- [Background Removal](../background-removal/SKILL.md) — Swap headshot backgrounds
- [AI Photo Enhancer](../ai-photo-enhancer/SKILL.md) — Improve photo quality

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for reference-based generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
