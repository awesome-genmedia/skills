---
name: face-swap
description: "Swap faces between photos using each::sense AI. Replace faces in target images with faces from source photos while preserving lighting, angle, skin tone, and expression. Powered by kling-face-swap for natural, seamless results. Use for: creative projects, entertainment, memes, virtual try-on, character casting, visual prototyping. Triggers: face swap, swap face, replace face, face replacement, face change, put face on, face transfer, deepfake, face morph"
allowed-tools: Bash(curl *), WebFetch
---

# Face Swap

Swap faces between photos with natural, seamless results using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Swap the face from the first image onto the person in the second image. Maintain natural lighting, skin tone matching, and realistic blending."},
              {"type": "image_url", "image_url": {"url": "https://example.com/source-face.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/target-photo.jpg"}}
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
    messages=[{"role": "user", "content": "Swap the face from the first image onto the person in the second image. Maintain natural lighting, skin tone matching, and realistic blending."}],
    # Images are included in the message content array above
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Use the face from the first image. Place it onto the person in the second image. The third image shows the desired lighting style to match."},
              {"type": "image_url", "image_url": {"url": "https://example.com/face-source.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/body-target.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/lighting-ref.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request. For face swap, you typically need at least 2 images: a source face and a target photo.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Available Models

| Model | Strengths | Best For |
|-------|-----------|----------|
| **kling-face-swap** | High-fidelity face replacement, natural blending, lighting adaptation | All face swap use cases |

> each::sense automatically selects kling-face-swap when face swap is detected in your request.

## How It Works

1. **Source image** (first URL): Contains the face you want to use
2. **Target image** (second URL): Contains the body/scene where the face will be placed
3. The model extracts facial features from the source and seamlessly blends them onto the target, matching:
   - Lighting direction and intensity
   - Skin tone and texture
   - Head angle and pose
   - Expression adaptation

## Image Requirements

| Requirement | Source Face | Target Photo |
|-------------|-----------|--------------|
| **Face visibility** | Clear, front-facing preferred | Face clearly visible |
| **Resolution** | 512px minimum on face | 512px minimum on face |
| **Lighting** | Even lighting on face helps | Any lighting (model adapts) |
| **Obstructions** | No sunglasses or heavy occlusion | Partial occlusion OK |
| **Multiple faces** | One clear primary face | Specify which person if multiple |

## Prompt Tips

### Specify Source and Target Clearly

Always clarify which image is the source face and which is the target:

```
"Take the face from the first image (the woman with dark hair)
and swap it onto the person in the second image (the man in the suit)."
```

### Handle Multiple People in Target

When the target has multiple people, specify the target:

```
"Swap the face from image 1 onto the person on the LEFT in image 2.
Do not modify the other person."
```

### Request Quality Adjustments

```
"Swap faces and ensure skin tone matches perfectly.
Blend the jawline and hairline edges seamlessly.
Match the lighting direction from the target photo."
```

## Examples

### Basic Face Swap

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Swap the face from the first image onto the person in the second image. Keep the result natural and photorealistic with smooth edge blending."},
              {"type": "image_url", "image_url": {"url": "https://example.com/my-face.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/magazine-cover.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Character Casting Visualization

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Place the face from the first image onto the medieval knight character in the second image. Adapt skin tone to match the costume lighting. Keep the helmet and armor unchanged. Result should look like a movie still."},
              {"type": "image_url", "image_url": {"url": "https://example.com/actor-headshot.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/knight-scene.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Professional Headshot Context

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Take the face from my casual photo (first image) and place it onto the professional business portrait (second image). Match the studio lighting, make the skin tones consistent, and ensure the collar and suit remain untouched."},
              {"type": "image_url", "image_url": {"url": "https://example.com/casual-selfie.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/business-portrait-template.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Group Photo Edit

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "In the group photo (second image), swap only the face of the person standing in the center wearing the blue shirt. Use the face from the first image. Keep all other people completely unchanged."},
              {"type": "image_url", "image_url": {"url": "https://example.com/replacement-face.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/group-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Creative / Artistic Swap

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Take the face from the first image and place it onto the Renaissance painting portrait in the second image. Blend the face to match the painting style — oil paint texture, period-appropriate lighting, and slightly warm old-master color palette. The face should look like it was part of the original painting."},
              {"type": "image_url", "image_url": {"url": "https://example.com/modern-face.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/renaissance-portrait.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

## Common Pitfalls

- **Images in wrong order**: The first URL should be the source face, the second should be the target. Swapping them produces inverted results.
- **Low resolution source faces**: Blurry or tiny faces produce blurry swaps. Use the clearest face photo available.
- **Extreme angle mismatches**: A front-facing source onto a full-profile target stretches features. Match angles when possible.
- **Heavy occlusion**: Sunglasses, masks, or hands covering the source face leave the model guessing about hidden features.
- **Not specifying the target person** in multi-person photos causes ambiguity about which face to replace.
- **Expecting video face swap**: This skill handles still images. For video, combine with video generation workflows.

## Ethical Use

Face swap technology should be used responsibly:

- Obtain consent before using someone's likeness
- Do not create deceptive or misleading content
- Do not use for harassment, impersonation, or fraud
- Label AI-generated content appropriately
- Follow applicable laws and platform policies

## Related Skills

- [Image Editing](../image-editing/SKILL.md) — General image editing for touch-ups after swapping
- [Background Removal](../background-removal/SKILL.md) — Clean up backgrounds after face swap
- [Image Generation](../image-generation/SKILL.md) — Generate target scenes for face swap
- [Image Upscaling](../image-upscaling/SKILL.md) — Enhance resolution after face swap

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
