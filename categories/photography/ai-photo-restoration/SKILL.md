---
name: ai-photo-restoration
description: "Restore old and damaged photos using each::sense AI. Repair scratches, tears, fading, water damage, and age deterioration. Reconstruct missing details, sharpen blurry areas, and bring damaged photographs back to life. Use for: photo restoration, old photo repair, damaged photo fix, vintage photo enhancement, archival restoration. Triggers: photo restoration, restore old photo, fix damaged photo, repair photo, old photo, vintage photo, photo repair, scratch removal, photo recovery, archival restoration"
allowed-tools: Bash(curl *), WebFetch
---

# AI Photo Restoration

Restore old and damaged photographs to their former quality using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Restore this old damaged photograph: remove scratches and tears, fix faded areas, sharpen blurry details, reconstruct any missing portions naturally, maintain the original character and era of the photo while making it clean and clear"
      }
    ],
    "image_urls": ["https://example.com/old-damaged-photo.jpg"],
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
        "content": "Restore this old damaged photograph: remove scratches and tears, fix faded areas, sharpen blurry details, reconstruct any missing portions naturally, maintain the original character and era of the photo while making it clean and clear"
    }],
    extra_body={"image_urls": ["https://example.com/old-damaged-photo.jpg"]}
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Photo Restoration

- **Always provide the source image** via `image_urls` — restoration requires the original damaged photo.
- **Describe the specific damage** — scratches, tears, water stains, fading, mold spots, or crease lines.
- **Specify what to preserve** — "maintain the 1950s aesthetic," "keep the sepia tone," or "preserve the original composition."
- **Request incremental fixes** — start with scratch removal, then sharpening, then detail reconstruction.
- **Combine with colorization** — after restoration, use the photo colorization skill to add color to black and white photos.

## Examples

### Scratch and Tear Repair

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Restore this vintage family portrait: remove the deep scratches across the center, repair the torn corner in the upper right, clean up the yellowed and stained areas, sharpen the faces while keeping the natural film grain, preserve the warm vintage tone"
      }
    ],
    "image_urls": ["https://example.com/scratched-family-photo.jpg"],
    "stream": false
  }'
```

### Faded Photo Enhancement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Restore this severely faded photograph: bring back the lost contrast and detail, recover the shadow areas that have become flat grey, enhance the highlights without blowing them out, reconstruct facial features that have faded, maintain natural photographic quality"
      }
    ],
    "image_urls": ["https://example.com/faded-photo.jpg"],
    "stream": false
  }'
```

### Water Damage Repair

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Repair this water-damaged photograph: remove the water stains and discoloration, fix the warped and bubbled areas, reconstruct the portions where the emulsion has been washed away, restore natural skin tones and background details"
      }
    ],
    "image_urls": ["https://example.com/water-damaged-photo.jpg"],
    "stream": false
  }'
```

## Workflow: Photo Restoration Pipeline

1. **Scan the original** — Digitize the physical photo at the highest resolution possible.
2. **Assess damage** — Identify scratches, tears, fading, stains, and missing areas.
3. **Restore structural damage** — Remove scratches, repair tears, and clean stains.
4. **Enhance clarity** — Sharpen details, restore contrast, and recover faded areas.
5. **Reconstruct missing parts** — Use AI to fill in damaged or missing sections.
6. **Colorize (optional)** — Add color to black and white restored photos.
7. **Final review** — Compare with original to ensure faithful restoration.

## Related Skills

- [AI Photo Colorization](../ai-photo-colorization/SKILL.md) — Add color to black and white photos
- [AI HDR Enhancement](../ai-hdr-enhancement/SKILL.md) — Dynamic range and detail enhancement
- [AI Photo Style Transfer](../ai-photo-style-transfer/SKILL.md) — Apply artistic styles
- [AI Stock Photo](../ai-stock-photo/SKILL.md) — Generate new stock photography

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-fidelity image reconstruction
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Intelligent detail recovery
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick restoration previews

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
