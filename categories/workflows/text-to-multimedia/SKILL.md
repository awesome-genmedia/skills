---
name: text-to-multimedia
description: "Generate image, video, and audio from a single text description using each::sense AI. A multi-step workflow that produces a complete multimedia package — a still image, an animated video, and a matching audio track — all from one creative brief. Use for: multimedia content, multi-format generation, content packages, rich media, complete media assets. Triggers: text to multimedia, multimedia generation, multi-format, image and video, content package, media suite, full media, all formats, multimedia pipeline, complete media"
allowed-tools: Bash(curl *), WebFetch
---

# Text to Multimedia Pipeline

Generate a complete multimedia package — image, video, and audio — from a single text description using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Step 1: Generate the Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A cozy cabin in a snowy forest at night, warm golden light glowing from the windows, smoke rising from the stone chimney, northern lights dancing in the sky above, tall snow-covered pines surrounding the cabin, photorealistic winter landscape"
      }
    ],
    "stream": false
  }'
```

### Step 2: Generate the Video

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Animate this winter cabin scene: smoke gently curling from the chimney, northern lights slowly shifting colors and dancing across the sky, snowflakes drifting down softly, a warm flicker of firelight in the windows, slow dolly-in camera movement, peaceful and atmospheric"
      }
    ],
    "image_urls": ["IMAGE_URL_FROM_STEP_1"],
    "stream": false
  }'
```

### Step 3: Generate the Audio

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate ambient audio for a winter cabin scene: gentle wind blowing through pine trees, distant crackling of a fireplace, soft snowfall sounds, occasional owl hooting in the distance, peaceful winter night atmosphere"
      }
    ],
    "stream": false
  }'
```

### Full Pipeline in Python

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

description = "A cozy cabin in a snowy forest at night with northern lights"

# Step 1: Generate image
print("Step 1: Generating image...")
image_response = client.chat.completions.create(
    model="eachsense/beta",
    messages=[{
        "role": "user",
        "content": f"{description}, warm golden light from windows, smoke from chimney, snow-covered pines, photorealistic"
    }]
)
print("Image:", image_response.choices[0].message.content)

# Step 2: Generate video (using image URL from Step 1)
print("Step 2: Generating video...")
video_response = client.chat.completions.create(
    model="eachsense/beta",
    messages=[{
        "role": "user",
        "content": "Animate this scene: northern lights dancing, smoke curling from chimney, snowflakes drifting, slow cinematic camera movement"
    }],
    extra_body={"image_urls": ["IMAGE_URL_FROM_STEP_1"]}
)
print("Video:", video_response.choices[0].message.content)

# Step 3: Generate audio
print("Step 3: Generating audio...")
audio_response = client.chat.completions.create(
    model="eachsense/beta",
    messages=[{
        "role": "user",
        "content": "Generate ambient winter night audio: gentle wind in pine trees, crackling fireplace, soft snowfall, occasional owl sounds"
    }]
)
print("Audio:", audio_response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Multimedia Generation

- **Start with a strong visual description** — the image sets the tone for all subsequent media.
- **Adapt prompts for each format** — images need composition details, videos need motion, audio needs soundscape.
- **Keep the theme consistent** — use the same setting, mood, and atmosphere across all three prompts.
- **Generate audio that matches the visual mood** — calm visuals with calm audio, dramatic visuals with intense audio.
- **Process sequentially** — image first (for video reference), then video, then audio (can be parallel with video).

## Examples

### Cinematic Nature Scene

**Image:**
```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "A dramatic thunderstorm over a vast wheat field, dark purple storm clouds with lightning bolts, golden wheat swaying in strong wind, a lone farmhouse in the distance, cinematic wide angle, photorealistic"}],
    "stream": false
  }'
```

**Video:**
```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Animate this storm scene: wheat field swaying dramatically in gusting wind, lightning flash illuminating the clouds, rain beginning to fall, camera slowly tracking forward toward the farmhouse, cinematic stormy atmosphere"}],
    "image_urls": ["IMAGE_URL"],
    "stream": false
  }'
```

**Audio:**
```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate storm soundscape audio: rolling thunder in the distance, strong wind gusts through grain fields, scattered raindrops building to a downpour, occasional close thunder cracks, dramatic atmospheric storm sounds"}],
    "stream": false
  }'
```

## Workflow: Text to Multimedia

1. **Write the creative brief** — One description covering the scene, mood, and purpose.
2. **Generate the image** — Create the visual anchor for the multimedia package.
3. **Animate to video** — Use the image as reference for video generation.
4. **Generate matching audio** — Create ambient sound or music that fits the scene.
5. **Combine in editor** — Layer video and audio together, add titles if needed.
6. **Export for platforms** — Render in the appropriate formats for target distribution.

## Related Skills

- [Image to Video Pipeline](../image-to-video-pipeline/SKILL.md) — Image-to-video animation
- [Product Media Suite](../product-media-suite/SKILL.md) — Product-focused multimedia
- [Brand Asset Pipeline](../brand-asset-pipeline/SKILL.md) — Brand identity multi-asset generation
- [Text to Speech](../../audio/text-to-speech/SKILL.md) — Narration audio generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative multimedia styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast pipeline execution

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
