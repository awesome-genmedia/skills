---
name: ai-hdr-enhancement
description: "Enhance photos with HDR and dynamic range improvements using each::sense AI. Recover shadow detail, tame highlights, boost local contrast, and create vivid high-dynamic-range looks. Improve exposure balance and bring out hidden details in underexposed or overexposed images. Use for: HDR enhancement, dynamic range, exposure correction, detail recovery, photo enhancement. Triggers: HDR, high dynamic range, exposure fix, shadow recovery, highlight recovery, dynamic range, photo enhance, tone mapping, detail enhancement, contrast boost"
allowed-tools: Bash(curl *), WebFetch
---

# AI HDR Enhancement

Enhance photographs with HDR processing and dynamic range improvements using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": [
              {"type": "text", "text": "Enhance this photograph with HDR processing: recover details in the dark shadow areas, bring back blown-out highlights in the sky, boost local contrast for texture detail, create a natural HDR look that is vivid but not over-processed, maintain realistic colors"},
              {"type": "image_url", "image_url": {"url": "https://example.com/underexposed-photo.jpg"}}
            ]
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
        "content": "Enhance this photograph with HDR processing: recover details in the dark shadow areas, bring back blown-out highlights in the sky, boost local contrast for texture detail, create a natural HDR look that is vivid but not over-processed, maintain realistic colors"
    }],
    # Images are included in the message content array above
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for HDR Enhancement

- **Always provide the source image** via `image_urls` for enhancement.
- **Specify the problem** — "dark shadows," "blown highlights," "flat contrast," or "dull colors."
- **Choose the HDR intensity** — "subtle natural enhancement" vs. "dramatic HDR effect."
- **Describe the desired look** — "photojournalistic realism," "dramatic landscape HDR," or "warm golden hour enhancement."
- **Avoid over-processing** — request "natural" or "realistic" to prevent the haloed, overly saturated HDR look.

## Examples

### Landscape HDR

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Apply HDR enhancement to this sunset landscape: recover the foreground details lost in shadow, bring texture back to the bright clouds, enhance the warm golden tones, boost the dramatic sky colors while keeping the rocks and water in the foreground well-exposed, natural dramatic HDR look"},
              {"type": "image_url", "image_url": {"url": "https://example.com/sunset-landscape.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Architecture HDR

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Enhance this interior architecture photograph with HDR: balance the bright windows with the dark interior, bring out texture in the wooden beams and stone walls, make the room feel evenly lit without losing the dramatic window light, professional real estate HDR style"},
              {"type": "image_url", "image_url": {"url": "https://example.com/interior-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Portrait Enhancement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Subtly enhance this portrait with HDR processing: gently lift the shadows under the chin and around the eyes, add micro-contrast for skin texture detail, brighten the catch lights in the eyes, warm the overall tone slightly, keep the enhancement natural and flattering"},
              {"type": "image_url", "image_url": {"url": "https://example.com/portrait-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

## Workflow: Photo Enhancement Pipeline

1. **Assess the exposure** — Identify underexposed shadows and overexposed highlights.
2. **Apply HDR enhancement** — Recover detail across the full tonal range.
3. **Adjust color balance** — Fine-tune warmth, saturation, and color accuracy.
4. **Boost local contrast** — Bring out texture and detail without global over-processing.
5. **Final review** — Compare with the original to ensure improvement without artifacts.

## Related Skills

- [AI Photo Restoration](../ai-photo-restoration/SKILL.md) — Repair damage before enhancement
- [AI Photo Colorization](../ai-photo-colorization/SKILL.md) — Add color to enhanced B&W photos
- [AI Photo Style Transfer](../ai-photo-style-transfer/SKILL.md) — Apply artistic styles to enhanced photos
- [AI Stock Photo](../ai-stock-photo/SKILL.md) — Generate new stock photography

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-fidelity image processing
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Intelligent detail enhancement
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick enhancement previews

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
