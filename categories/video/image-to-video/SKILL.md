---
name: image-to-video
description: "Animate still images into videos using each::sense AI. Bring photographs, illustrations, and artwork to life with motion, camera movements, and environmental effects. Transform static images into dynamic video clips with natural movement and cinematic quality. Use for: photo animation, artwork animation, social media content, living photos, cinemagraphs, animated illustrations. Triggers: image to video, animate image, img2vid, bring to life, animate photo, photo to video, living photo, moving image, animate picture, image animation, motion from image"
allowed-tools: Bash(curl *), WebFetch
---

# Image to Video

Animate still images into dynamic video clips using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Animate this image: gentle wind blowing through the trees, leaves rustling, clouds drifting slowly across the sky, subtle camera push-in, cinematic, natural motion"
      }
    ],
    "image_urls": ["https://example.com/landscape-photo.jpg"],
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
        "content": "Animate this image: gentle wind blowing through the trees, leaves rustling, clouds drifting slowly across the sky, subtle camera push-in, cinematic, natural motion"
    }],
    extra_body={
        "image_urls": ["https://example.com/landscape-photo.jpg"]
    }
)

print(response.choices[0].message.content)
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Motion Types

| Motion | Description | Best Image Types |
|--------|-------------|-----------------|
| **Environment Motion** | Wind, water, clouds, fire | Landscapes, nature shots |
| **Camera Movement** | Pan, zoom, orbit, push-in | Any static scene |
| **Character Motion** | Walking, turning, blinking | Portraits, character art |
| **Particle Effects** | Snow, rain, petals, sparks | Outdoor scenes, moody shots |
| **Subtle Animation** | Hair movement, fabric sway | Fashion, portraits |
| **Parallax** | 2.5D depth movement | Illustrations, layered scenes |

## Examples

### Portrait Animation

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Animate this portrait: the person slowly turns their head to face the camera, a subtle smile appears, hair moves gently as if in a light breeze, natural blinking, soft lighting remains consistent, cinematic"
      }
    ],
    "image_urls": ["https://example.com/portrait.jpg"],
    "stream": false
  }'
```

### Ocean Scene

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Animate this beach photo: ocean waves rolling in and crashing on the shore, foam sliding up the sand, seagulls flying in the background, palm trees swaying in wind, camera static, ambient natural motion"
      }
    ],
    "image_urls": ["https://example.com/beach-sunset.jpg"],
    "stream": false
  }'
```

### Illustration to Animation

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Animate this fantasy illustration: the dragon spreads its wings slowly, fire flickers from torches on the castle walls, clouds drift behind the mountains, magical sparkles float in the air, smooth animation, maintain the artistic style"
      }
    ],
    "image_urls": ["https://example.com/fantasy-castle.jpg"],
    "stream": false
  }'
```

### Product Reveal

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Animate this product photo: camera slowly orbits around the product, studio lighting highlights shift as the angle changes, reflections move on the surface, premium commercial feel, smooth 360-degree rotation"
      }
    ],
    "image_urls": ["https://example.com/product-hero.jpg"],
    "stream": false
  }'
```

## Prompt Tips

- **Describe specific motions**: "waves crashing," "hair blowing left," "slow zoom in" — vague prompts produce random movement
- **Keep motion consistent with the image**: Do not ask a sitting person to run; describe plausible motion
- **Specify what stays still**: "Camera static, only the water moves" prevents unwanted warping
- **Mention style preservation**: "Maintain the illustration style" for artwork, "keep photorealistic" for photos
- **One primary motion focus**: Videos look best when one main element moves rather than everything at once
- **Add "smooth" and "natural"**: Prevents jittery or unnatural animation

## Image Selection Tips

Best images for animation:
- **Clear subjects** with distinct foreground and background
- **High resolution** source images produce better video quality
- **Simple compositions** with one main subject
- **Implied motion** — images that suggest movement (a person mid-stride, flowing water)

Challenging images:
- Very busy/cluttered scenes
- Extreme close-ups with no environmental context
- Abstract art without clear subjects to animate
- Very low resolution images

## Related Skills

- [Text to Video](../text-to-video/SKILL.md) — Generate videos from text
- [AI Video Loop](../ai-video-loop/SKILL.md) — Create seamless loops
- [AI Slow Motion](../ai-slow-motion/SKILL.md) — Slow motion effects
- [AI Video Editor](../ai-video-editor/SKILL.md) — Edit video with AI

## Related Models

- [wan-2-1-14b](../../../models/wan-2-1-14b/SKILL.md) — High quality video generation
- [hailuo-minimax-video-01](../../../models/hailuo-minimax-video-01/SKILL.md) — Fast video generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
