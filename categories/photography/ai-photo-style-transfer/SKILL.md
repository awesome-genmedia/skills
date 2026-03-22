---
name: ai-photo-style-transfer
description: "Apply artistic styles to photos using each::sense AI. Transform photographs into oil paintings, watercolors, pencil sketches, anime, comic book art, impressionist works, and more. Maintain subject composition while changing the visual medium. Use for: style transfer, photo to painting, artistic filter, photo to illustration, artistic transformation. Triggers: style transfer, photo to painting, artistic style, photo to art, oil painting style, watercolor style, sketch style, anime style, comic style, impressionist"
allowed-tools: Bash(curl *), WebFetch
---

# AI Photo Style Transfer

Apply artistic styles to photographs, transforming them into paintings, illustrations, and other visual media using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
              {"type": "text", "text": "Transform this photograph into a Van Gogh-style oil painting: swirling brushstrokes, thick impasto texture, vibrant post-impressionist colors, starry night energy, maintain the original composition and subjects but reimagine entirely in oil paint"},
              {"type": "image_url", "image_url": {"url": "https://example.com/original-photo.jpg"}}
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
        "content": "Transform this photograph into a Van Gogh-style oil painting: swirling brushstrokes, thick impasto texture, vibrant post-impressionist colors, starry night energy, maintain the original composition and subjects but reimagine entirely in oil paint"
    }],
    # Images are included in the message content array above
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Style Transfer

- **Always provide the source photo** via `image_urls` for transformation.
- **Name the target style explicitly** — "oil painting," "watercolor," "charcoal sketch," "anime," "pop art."
- **Reference specific artists or movements** — "Monet impressionism," "Hokusai woodblock," "Warhol pop art."
- **Control the transformation intensity** — "subtle stylization" vs. "complete reimagining."
- **Specify what to preserve** — "keep the facial features accurate" or "maintain the building architecture."

## Examples

### Watercolor Transformation

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Convert this landscape photograph into a delicate watercolor painting: soft color washes bleeding at the edges, visible paper texture, loose brushwork in the foliage, sharper detail in the foreground, traditional watercolor technique with wet-on-wet blending"},
              {"type": "image_url", "image_url": {"url": "https://example.com/landscape.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Anime Style

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Transform this portrait into anime style: large expressive eyes, clean line art, flat color shading with subtle gradients, characteristic anime hair rendering, maintain the person's overall look and clothing but fully converted to Japanese anime aesthetic"},
              {"type": "image_url", "image_url": {"url": "https://example.com/portrait.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Pencil Sketch

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Transform this city street photo into a detailed pencil sketch: fine hatching and cross-hatching for shadows, clean lines for architecture, varying pencil pressure for depth, white paper background showing through, skilled draughtsman quality, graphite on paper"},
              {"type": "image_url", "image_url": {"url": "https://example.com/city-street.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Pop Art

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Transform this portrait into Andy Warhol pop art style: bold flat colors, high contrast, four-panel grid with different color variations — pink and yellow, blue and green, orange and purple, red and teal — Ben-Day dots texture, iconic pop art screen print aesthetic"},
              {"type": "image_url", "image_url": {"url": "https://example.com/face-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

## Workflow: Style Transfer Gallery

1. **Select source photos** — Choose high-quality, well-composed photographs.
2. **Choose target styles** — Pick artistic styles that complement each image.
3. **Transform with style cues** — Apply detailed style descriptions for best results.
4. **Compare results** — Review the transformation against the original.
5. **Create a style series** — Apply the same style to multiple photos for a cohesive set.

## Related Skills

- [AI Photo Restoration](../ai-photo-restoration/SKILL.md) — Restore photos before styling
- [AI Photo Colorization](../ai-photo-colorization/SKILL.md) — Add color before artistic transfer
- [AI HDR Enhancement](../ai-hdr-enhancement/SKILL.md) — Enhance photos before transformation
- [AI Stock Photo](../ai-stock-photo/SKILL.md) — Generate base photos for styling

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Precise style application
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Rich artistic interpretation
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick style previews

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
