---
name: ai-photo-enhancer
description: "Enhance photo quality with AI using each::sense AI. Improve sharpness, fix lighting, reduce noise, correct colors, restore old photos, and bring out hidden detail in underexposed or degraded images. Supports batch enhancement and targeted corrections. Use for: photo restoration, noise reduction, color correction, lighting fixes, old photo repair, image sharpening, HDR enhancement. Triggers: photo enhancer, enhance photo, improve photo, fix photo, photo quality, color correction, noise reduction, sharpen photo, restore photo, photo fixer, image enhancement, ai enhance"
allowed-tools: Bash(curl *), WebFetch
---

# AI Photo Enhancer

Improve photo quality, fix lighting, reduce noise, and restore images using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Enhance this photo: improve sharpness, fix the underexposed shadows, boost color vibrancy slightly, and reduce noise while preserving natural skin texture."
      }
    ],
    "image_urls": ["https://example.com/dark-noisy-photo.jpg"],
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
        "content": "Enhance this photo: improve sharpness, fix the underexposed shadows, boost color vibrancy slightly, and reduce noise while preserving natural skin texture."
    }],
    extra_body={
        "image_urls": ["https://example.com/dark-noisy-photo.jpg"]
    }
)

print(response.choices[0].message.content)
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Enhancement Types

| Enhancement | Prompt Keywords | When to Use |
|-------------|----------------|-------------|
| **Sharpening** | sharpen, improve detail, crisp | Soft or slightly out-of-focus photos |
| **Noise Reduction** | reduce noise, denoise, remove grain | High-ISO or low-light photos |
| **Exposure Fix** | brighten shadows, fix exposure, recover highlights | Under/overexposed shots |
| **Color Correction** | fix white balance, correct color cast, true-to-life | Wrong white balance, tinted photos |
| **HDR Enhancement** | HDR effect, dynamic range, balanced exposure | High-contrast scenes |
| **Old Photo Restoration** | restore, fix damage, remove scratches | Vintage or damaged prints |
| **Deblurring** | remove motion blur, sharpen movement | Motion-blurred shots |

## Examples

### Fix Low-Light Photo

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "This photo was taken in low light. Brighten the shadows without blowing out highlights, reduce the visible noise and grain, improve color accuracy, and sharpen the subject. Keep the moody atmosphere but make details visible."
      }
    ],
    "image_urls": ["https://example.com/lowlight-event.jpg"],
    "stream": false
  }'
```

### Restore Old Family Photo

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Restore this old photograph from the 1970s. Remove the yellowing and faded color cast, fix scratches and dust spots, sharpen facial details, and bring the colors back to a natural look. Preserve the original composition."
      }
    ],
    "image_urls": ["https://example.com/old-family-1975.jpg"],
    "stream": false
  }'
```

### Product Photo Enhancement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Enhance this product photo for e-commerce: correct the slightly warm color cast to neutral, increase sharpness of the product details, ensure the white background is pure white, and boost contrast slightly for a clean commercial look."
      }
    ],
    "image_urls": ["https://example.com/product-raw.jpg"],
    "stream": false
  }'
```

### Batch Enhancement

```bash
PHOTOS=(
  "https://example.com/vacation-1.jpg"
  "https://example.com/vacation-2.jpg"
  "https://example.com/vacation-3.jpg"
)

ENHANCEMENT="Enhance this photo: improve sharpness, correct white balance to natural daylight, reduce noise, boost vibrancy slightly. Keep the edit subtle and natural-looking."

for URL in "${PHOTOS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$ENHANCEMENT\"}],
      \"image_urls\": [\"$URL\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Prompt Tips

- **Be specific about what is wrong**: "the shadows are too dark" is better than "fix this photo"
- **Mention what to preserve**: "Keep the warm sunset tones" prevents over-correction
- **Specify the intent**: "for social media posting" vs. "for large print" changes the approach
- **Avoid conflicting instructions**: "make it brighter but keep the moody dark look" is contradictory
- **Use "subtle" or "natural"** to prevent aggressive over-processing

## Common Problems and Prompts

| Problem | Suggested Prompt |
|---------|-----------------|
| Too dark | "Brighten the exposure, lift shadows, keep highlights intact" |
| Too bright/washed out | "Reduce exposure, recover blown highlights, deepen shadows" |
| Yellow/orange cast | "Correct the warm color cast to neutral white balance" |
| Blue/cold cast | "Fix the blue color cast, warm up the tones slightly" |
| Blurry | "Sharpen and improve focus, especially on the main subject" |
| Grainy/noisy | "Reduce noise and grain while preserving fine detail" |
| Faded colors | "Restore color vibrancy and saturation to natural levels" |
| Old/damaged | "Restore: remove scratches, fix discoloration, sharpen details" |

## Related Skills

- [Image Upscaling](../image-upscaling/SKILL.md) — Increase resolution
- [AI Image Editor](../ai-image-editor/SKILL.md) — Edit specific elements
- [Background Removal](../background-removal/SKILL.md) — Remove or replace backgrounds
- [Inpainting & Outpainting](../inpainting-outpainting/SKILL.md) — Repair damaged areas

## Related Models

- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image editing tasks
- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
