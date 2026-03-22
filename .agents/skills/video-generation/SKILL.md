---
name: video-generation
description: "Generate videos from text prompts or images using each::sense AI. Create cinematic clips, product demos, social media reels, animations, and motion graphics. Supports text-to-video and image-to-video with audio. 8 specialized models including veo-3, kling-3-0, and sora-2-pro. Use for: social media content, product videos, trailers, animations, storytelling, marketing clips. Triggers: generate video, create video, text to video, ai video, video generation, image to video, animate image, make video, video from text, ai animation, motion, clip"
allowed-tools: Bash(curl *), WebFetch
---

# Video Generation

Generate videos from text prompts or static images using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "A golden retriever running through a field of wildflowers in slow motion, cinematic, shallow depth of field, warm afternoon light"}],
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
    messages=[{"role": "user", "content": "A golden retriever running through a field of wildflowers in slow motion, cinematic, shallow depth of field, warm afternoon light"}]
)

print(response.choices[0].message.content)
```

### With Reference Image (Image-to-Video)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Animate this photo: the woman slowly turns her head toward the camera and smiles, her hair gently blowing in the breeze, natural movement"},
              {"type": "image_url", "image_url": {"url": "https://example.com/portrait-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Available Models

### Text-to-Video

| Model | Strengths | Best For |
|-------|-----------|----------|
| **veo-3** | Best overall quality, generates synchronized audio | Cinematic clips, ads, content with sound |
| **veo3-1-fast** | Fast generation with good quality | Quick iterations, social media content |
| **kling-3-0** | High quality with consistent motion | Character animation, dynamic scenes |
| **wan-v2-6-text-to-video** | Reliable text-to-video generation | General purpose video creation |
| **pixverse-v4-1** | Stylized and artistic outputs | Animated content, creative videos |
| **sora-2-pro** | Cinematic quality with natural physics | Film-like scenes, professional content |

### Image-to-Video

| Model | Strengths | Best For |
|-------|-----------|----------|
| **kling-2-1-image-to-video** | Smooth animation from still images | Product animations, portrait animations |
| **wan-v2-6-image-to-video** | Consistent with source image details | Extending photos into motion |

> each::sense automatically picks the right model based on your prompt. Mention "animate this image" or provide an image_url to trigger image-to-video models.

## Prompt Engineering Guide

### Prompt Structure for Video

```
[subject] + [action/motion] + [environment] + [camera movement] + [style] + [mood/lighting]
```

### Motion Keywords

| Motion Type | Keywords |
|-------------|----------|
| **Camera** | pan left, dolly forward, orbit around, zoom in, crane shot, tracking shot |
| **Subject** | walking, running, turning, dancing, gesturing, floating |
| **Environment** | wind blowing, rain falling, clouds moving, waves crashing, leaves drifting |
| **Speed** | slow motion, timelapse, real-time, fast forward, bullet time |

### Cinematic Keywords

```
cinematic, 4K, film grain, anamorphic lens, letterbox,
shallow depth of field, bokeh, golden hour, dramatic lighting
```

### Duration Guidance

Specify approximate duration in your prompt when needed:

```
"... 5-second clip of ..."
"... short loop, 3 seconds ..."
"... 10-second establishing shot ..."
```

## Examples

### Cinematic Landscape

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Aerial drone shot slowly flying over a misty mountain range at sunrise, clouds weaving between peaks, golden light spilling across ridgelines, cinematic 4K, orchestral mood"}],
    "stream": false
  }'
```

### Product Demo Animation

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "A sleek smartphone rotating slowly on a dark reflective surface, studio lighting revealing its design from all angles, subtle light reflections, product commercial style, 5 seconds"}],
    "stream": false
  }'
```

### Image-to-Video (Portrait Animation)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Animate this portrait: subtle breathing motion, a gentle blink, the person then looks slightly to the left and gives a warm smile. Natural and realistic movement."},
              {"type": "image_url", "image_url": {"url": "https://example.com/headshot.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Social Media Reel

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "A barista pouring latte art in a cozy coffee shop, close-up shot, steam rising from the cup, warm ambient lighting, 9:16 vertical format for Instagram Reels, satisfying and aesthetic"}],
    "stream": false
  }'
```

### Video with Generated Audio (veo-3)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "A thunderstorm rolling over a vast prairie, lightning bolts illuminating dark clouds, heavy rain sweeping across golden grass, with realistic thunder sounds and rain audio, cinematic wide shot"}],
    "stream": false
  }'
```

## Common Pitfalls

- **Static descriptions** produce still-looking videos. Always describe motion and action explicitly.
- **Too many scene changes** in one prompt confuse the model. Focus on one continuous scene.
- **Ignoring camera movement** produces locked-off shots. Specify pans, dollies, or tracking for dynamic feel.
- **Complex character interactions** (two people talking) can produce inconsistent results. Keep interactions simple.
- **No temporal structure** makes clips feel random. Describe what happens from start to end.

## Text-to-Video vs. Image-to-Video

| Feature | Text-to-Video | Image-to-Video |
|---------|--------------|----------------|
| **Input** | Text prompt only | Text prompt + source image |
| **Control** | Full creative freedom | Preserves visual identity from image |
| **Consistency** | Model interprets everything | Anchored to source image appearance |
| **Best for** | Original content from scratch | Animating existing designs, photos, art |
| **How to trigger** | Just describe the scene | Include `image_urls` and say "animate this" |

## Related Skills

- [Image Generation](../image-generation/SKILL.md) — Generate starting frames for image-to-video
- [Video Editing](../video-editing/SKILL.md) — Edit and refine generated videos
- [Song Generation](../song-generation/SKILL.md) — Create music to pair with videos
- [Sound Effects](../sound-effects/SKILL.md) — Add sound effects to video projects
- [Voice Generation](../voice-generation/SKILL.md) — Generate narration for videos

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
