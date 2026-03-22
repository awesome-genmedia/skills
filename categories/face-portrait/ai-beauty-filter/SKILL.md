---
name: ai-beauty-filter
description: "Apply AI beauty enhancements to face photos using each::sense AI. Smooth skin, whiten teeth, remove blemishes, brighten eyes, enhance jawline, and apply natural-looking retouching while preserving identity. Use for: portrait retouching, headshot enhancement, social media photos, dating profile photos, professional headshots, selfie enhancement. Triggers: beauty filter, skin smoothing, face enhancement, retouch photo, teeth whitening, blemish removal, portrait enhancement, face beautify, smooth skin, eye brighten, skin retouch, face glow up"
allowed-tools: Bash(curl *), WebFetch
---

# AI Beauty Filter

Apply professional-grade beauty enhancements to face photos using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Enhance this portrait with natural beauty retouching. Smooth the skin while keeping texture, brighten the eyes, whiten teeth slightly, and even out the skin tone. Keep it looking natural, not overly filtered."
      }
    ],
    "image_urls": ["https://example.com/portrait.jpg"],
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
        "content": "Enhance this portrait with natural beauty retouching. Smooth the skin while keeping texture, brighten the eyes, whiten teeth slightly, and even out the skin tone. Keep it looking natural, not overly filtered."
    }],
    extra_body={
        "image_urls": ["https://example.com/portrait.jpg"]
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
    "messages": [{"role": "user", "content": "Apply beauty retouching to this photo: smooth skin, remove blemishes, brighten eyes, keep it natural and realistic"}],
    "image_urls": ["https://example.com/selfie.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Enhancement Options

| Enhancement | Description | Typical Use |
|---|---|---|
| **Skin Smoothing** | Reduces pores and texture while keeping natural look | All portraits |
| **Blemish Removal** | Removes acne, scars, dark spots | Headshots, social media |
| **Teeth Whitening** | Brightens teeth naturally | Smiling portraits |
| **Eye Brightening** | Enhances iris color, adds catchlight | All portraits |
| **Skin Tone Evening** | Reduces redness, evens complexion | Professional headshots |
| **Jawline Enhancement** | Subtle contouring of the jawline | Profile photos |
| **Under-eye Fix** | Reduces dark circles and bags | Tired-looking photos |
| **Hair Enhancement** | Adds shine and volume appearance | Glamour shots |

## Prompt Engineering Tips

### Specify Enhancement Level

Use descriptors like "subtle," "natural," "moderate," or "glamour" to control intensity:

```
Apply [level] beauty enhancement to this portrait: [specific enhancements]. Keep the result [natural/polished].
```

### Natural vs. Glamour

- **Natural retouching**: Preserves skin texture, subtle corrections, looks like the person on a good day
- **Glamour retouching**: Heavier smoothing, dramatic eye enhancement, more like a magazine cover

### Common Mistakes to Avoid

- Requesting "perfect skin" often produces plastic-looking results
- Over-whitening teeth looks unnatural
- Always mention "keep texture" for skin smoothing

## Examples

### Professional Headshot Retouch

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Retouch this professional headshot. Smooth skin lightly while preserving pore texture, remove any blemishes, reduce dark circles under the eyes, even out skin tone, and add a subtle warmth to the overall color. Corporate headshot quality."
      }
    ],
    "image_urls": ["https://example.com/headshot-raw.jpg"],
    "stream": false
  }'
```

### Social Media Selfie Enhancement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Enhance this selfie for Instagram. Brighten the overall image, smooth skin naturally, make eyes pop with slight brightening, whiten teeth a touch, and give the photo a warm golden-hour glow. Should look effortlessly good, not obviously edited."
      }
    ],
    "image_urls": ["https://example.com/casual-selfie.jpg"],
    "stream": false
  }'
```

### Glamour Magazine Style

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply high-end magazine beauty retouching to this portrait. Flawless skin with very smooth texture, bright vivid eyes, perfectly white teeth, defined cheekbones with subtle contouring, and luminous skin glow. Vogue editorial style."
      }
    ],
    "image_urls": ["https://example.com/studio-portrait.jpg"],
    "stream": false
  }'
```

### Subtle Natural Touch-up

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply very subtle retouching to this photo. Just remove the few visible blemishes, slightly reduce the redness around the nose, and brighten the under-eye area. Everything else should stay exactly as-is. The person should not be able to tell the photo was edited."
      }
    ],
    "image_urls": ["https://example.com/natural-photo.jpg"],
    "stream": false
  }'
```

## Workflow: Complete Portrait Enhancement

```bash
# Step 1: Start with basic skin corrections
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Remove blemishes and even out skin tone in this portrait. Do not smooth the skin yet, just fix spots and discoloration. Keep everything else untouched."
      }
    ],
    "image_urls": ["https://example.com/raw-portrait.jpg"],
    "stream": false
  }'

# Step 2: Refine with beauty enhancements
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Now apply natural beauty enhancement to this portrait: light skin smoothing with texture preserved, brighten the eyes, whiten teeth slightly, reduce under-eye shadows, and add a gentle warm glow. Professional but natural result."
      }
    ],
    "image_urls": ["https://example.com/corrected-portrait.jpg"],
    "stream": false
  }'
```

## Related Skills

- [AI Face Restoration](../ai-face-restoration/SKILL.md) — Restore damaged or low-quality photos first
- [AI Makeup Try-On](../ai-makeup-try-on/SKILL.md) — Apply virtual makeup looks
- [AI Expression Editor](../ai-expression-editor/SKILL.md) — Adjust facial expressions
- [AI Aging Filter](../ai-aging-filter/SKILL.md) — Age progression effects
- [AI Face Swap](../ai-face-swap/SKILL.md) — Swap faces between photos

## Related Models

- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Context-aware image editing
- [clarity-upscaler](../../../models/clarity-upscaler/SKILL.md) — Enhance image resolution
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — High-quality image generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
