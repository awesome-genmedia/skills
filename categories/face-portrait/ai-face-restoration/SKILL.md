---
name: ai-face-restoration
description: "Restore damaged, blurry, or low-quality face photos using each::sense AI. Fix old photos, remove scratches and damage, enhance resolution, sharpen details, recover lost facial features, and upscale low-resolution portraits. Use for: old family photo restoration, damaged photo repair, low-res face enhancement, historical photo recovery, blurry photo fix, heritage preservation. Triggers: face restoration, photo restoration, fix old photo, repair photo, enhance face, unblur face, restore portrait, fix blurry, old photo repair, damaged photo, upscale face, photo recovery, enhance resolution"
allowed-tools: Bash(curl *), WebFetch
---

# AI Face Restoration

Restore damaged, blurry, or low-quality face photos to sharp, clear portraits using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Restore this old damaged family photo. Fix the scratches, remove the fading and yellowing, sharpen the faces, and enhance the overall quality to look like a modern photograph while preserving the original composition."
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
        "content": "Restore this old damaged family photo. Fix the scratches, remove the fading and yellowing, sharpen the faces, and enhance the overall quality to look like a modern photograph while preserving the original composition."
    }],
    extra_body={
        "image_urls": ["https://example.com/old-damaged-photo.jpg"]
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
    "messages": [{"role": "user", "content": "Restore and enhance this blurry low-resolution face photo. Sharpen all facial details, improve clarity, and upscale to high quality"}],
    "image_urls": ["https://example.com/blurry-face.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Restoration Capabilities

| Issue | What AI Can Fix | Difficulty |
|---|---|---|
| **Blur/Out of Focus** | Sharpens features, recovers detail | Easy |
| **Low Resolution** | Upscales and adds realistic detail | Easy |
| **Scratches/Tears** | Removes physical damage artifacts | Medium |
| **Fading/Yellowing** | Restores original tones and contrast | Easy |
| **Water Damage** | Reconstructs warped or stained areas | Medium |
| **Missing Sections** | Intelligently fills in gaps | Hard |
| **Noise/Grain** | Reduces excessive film grain | Easy |
| **Color Loss** | Re-colorizes faded or B&W photos | Medium |

## Prompt Engineering Tips

### Describe the Damage

Be specific about what needs fixing so the AI can prioritize:

```
Restore this photo: [describe damage]. Fix [specific issues]. Enhance [quality aspects]. Preserve [what to keep unchanged].
```

### Preservation Keywords

Always mention what to preserve:

```
Keep the original composition, maintain the person's identity,
preserve the original expression, don't change the background,
keep the vintage clothing accurate
```

### Quality Enhancement Keywords

```
sharpen facial details, enhance resolution, improve clarity,
restore true-to-life colors, recover fine details, upscale
```

## Examples

### Old Family Photo with Scratches

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Restore this 1960s family photograph. It has multiple scratches across the surface, yellowed with age, and the faces have lost detail. Remove all scratches, correct the yellowing to natural colors, sharpen the faces so individual features are clear, and enhance the overall resolution. Keep the vintage clothing and setting accurate."
      }
    ],
    "image_urls": ["https://example.com/1960s-family.jpg"],
    "stream": false
  }'
```

### Blurry Low-Resolution Portrait

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "This is a very low-resolution, blurry face photo, probably from an old phone camera. Upscale it to high resolution, sharpen all facial features including eyes, nose, lips, and eyebrows. Recover skin texture and hair detail. Make it look like it was taken with a modern camera."
      }
    ],
    "image_urls": ["https://example.com/low-res-face.jpg"],
    "stream": false
  }'
```

### Water-Damaged Photograph

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "This photo has water damage with warping and discoloration stains, especially in the lower half. Restore the damaged areas, fix the color staining, straighten any warped features, and recover the original appearance. The subject face in the upper portion is partially affected too."
      }
    ],
    "image_urls": ["https://example.com/water-damaged.jpg"],
    "stream": false
  }'
```

### Black and White Colorization

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Restore and colorize this black and white portrait from the 1940s. Sharpen the face, enhance details, and add natural realistic colors: skin tones, hair color matching the era, colorize the clothing appropriately for the 1940s. Keep it photorealistic, not painted-looking."
      }
    ],
    "image_urls": ["https://example.com/bw-1940s-portrait.jpg"],
    "stream": false
  }'
```

## Workflow: Complete Photo Restoration

```bash
# Step 1: Fix physical damage first
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Remove all scratches, tears, and physical damage from this old photo. Do not change the resolution or colors yet, just clean up the damage artifacts."
      }
    ],
    "image_urls": ["https://example.com/damaged-original.jpg"],
    "stream": false
  }'

# Step 2: Enhance quality and resolution
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Upscale and enhance this restored photo. Sharpen all faces, improve resolution, correct the faded colors to look vibrant and natural, and enhance overall clarity. Preserve the original composition exactly."
      }
    ],
    "image_urls": ["https://example.com/cleaned-photo.jpg"],
    "stream": false
  }'

# Step 3: Final color correction
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply final color correction to this restored photo. Balance the white point, ensure natural skin tones, and adjust contrast for a clean modern look. Do not change the composition or faces."
      }
    ],
    "image_urls": ["https://example.com/enhanced-photo.jpg"],
    "stream": false
  }'
```

## Input Tips

- Scan old photos at the highest resolution possible before uploading
- Even very small or severely damaged photos can be improved
- For best results, crop to focus on the face area
- Multiple passes can progressively improve results

## Related Skills

- [AI Beauty Filter](../ai-beauty-filter/SKILL.md) — Further enhance restored portraits
- [AI Aging Filter](../ai-aging-filter/SKILL.md) — Age effects after restoration
- [AI Expression Editor](../ai-expression-editor/SKILL.md) — Adjust expressions
- [AI Face Swap](../ai-face-swap/SKILL.md) — Face manipulation after restoration

## Related Models

- [clarity-upscaler](../../../models/clarity-upscaler/SKILL.md) — Image upscaling and enhancement
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Context-aware image editing
- [real-esrgan](../../../models/real-esrgan/SKILL.md) — Super-resolution upscaling
- [aura-sr](../../../models/aura-sr/SKILL.md) — AI super-resolution

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
