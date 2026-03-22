---
name: text-to-video
description: "Generate videos from text descriptions using each::sense AI. Create short video clips, animated scenes, cinematic shots, and motion content from text prompts. Supports photorealistic, animated, and stylized video generation with camera movements and transitions. Use for: video content creation, social media clips, concept visualization, storyboard animation, motion design, creative exploration. Triggers: text to video, generate video, create video, ai video, video generation, txt2vid, prompt to video, ai animation, video from text, ai clip, motion generation"
allowed-tools: Bash(curl *), WebFetch
---

# Text to Video

Generate videos from text descriptions using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a video: A golden retriever running through a sunlit meadow of wildflowers, slow motion, cinematic, shallow depth of field, warm afternoon light, camera tracking alongside the dog"
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
        "content": "Generate a video: A golden retriever running through a sunlit meadow of wildflowers, slow motion, cinematic, shallow depth of field, warm afternoon light, camera tracking alongside the dog"
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Prompt Structure

```
Generate a video: [subject] + [action] + [environment] + [style] + [camera movement] + [lighting]
```

## Camera Movement Keywords

| Movement | Description | Use For |
|----------|-------------|---------|
| **Static shot** | Camera does not move | Portraits, product display |
| **Pan left/right** | Horizontal camera rotation | Revealing environments |
| **Tilt up/down** | Vertical camera rotation | Revealing tall structures |
| **Dolly in/out** | Camera moves toward/away | Dramatic focus shifts |
| **Tracking shot** | Camera follows subject | Action, movement sequences |
| **Crane shot** | Rising or descending movement | Epic establishing shots |
| **Orbit** | Camera circles the subject | 360-degree reveals, products |
| **Zoom in/out** | Focal length change | Emphasis, dramatic reveals |
| **Handheld** | Slightly shaky, natural feel | Documentary, intimate |
| **Drone shot** | Aerial perspective | Landscapes, establishing |

## Style Keywords

| Style | Keywords |
|-------|----------|
| **Cinematic** | cinematic, film look, anamorphic, 24fps, shallow DOF |
| **Photorealistic** | photorealistic, real footage, DSLR video, natural |
| **Animated** | 3D animation, cartoon, anime, cel animation |
| **Abstract** | abstract motion, fluid simulation, particle effects |
| **Vintage** | Super 8, VHS, film grain, retro, old footage |
| **Slow Motion** | slow motion, 120fps, bullet time |

## Examples

### Cinematic Nature Shot

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: Aerial drone shot slowly rising over a misty mountain forest at sunrise, revealing snow-capped peaks in the distance, golden light breaking through clouds, cinematic 4K, smooth camera movement, epic landscape"
      }
    ],
    "stream": false
  }'
```

### Product Showcase

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: A sleek black smartwatch rotating slowly on a reflective dark surface, studio lighting with soft highlights, camera orbiting 360 degrees, premium product commercial style, clean minimal background"
      }
    ],
    "stream": false
  }'
```

### Abstract Motion Graphics

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: Abstract fluid simulation of metallic gold and deep blue liquids merging and swirling together, macro close-up, mesmerizing slow movement, reflective surfaces, dark background, satisfying visual"
      }
    ],
    "stream": false
  }'
```

### Character Animation

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: A samurai warrior drawing a katana in a bamboo forest, cherry blossom petals falling in slow motion, dramatic side lighting, anime-inspired cinematic style, camera slowly pushing in, atmospheric fog"
      }
    ],
    "stream": false
  }'
```

## Prompt Tips

- **One action per clip**: AI video works best with a single, clear action rather than complex sequences
- **Specify camera movement**: Without it, you may get a static or randomly moving camera
- **Include lighting**: "golden hour," "studio lighting," "neon glow" dramatically shapes the mood
- **Keep duration realistic**: Current AI video models produce short clips (3-10 seconds)
- **Describe motion explicitly**: "walking slowly," "rotating 360 degrees," "rising upward"
- **Add "smooth" or "fluid"**: Helps avoid jerky or unnatural movement

## Video Planning Workflow

For longer sequences, generate individual shots and edit together:

```bash
# Shot 1: Establishing
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a video: Wide establishing shot of a futuristic city skyline at dusk, flying vehicles crossing the sky, neon lights turning on, drone camera slowly descending, cyberpunk, cinematic"}],
    "stream": false
  }'

# Shot 2: Medium shot
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a video: Medium shot of a woman in a futuristic jacket walking through a neon-lit street market, rain reflecting neon signs, camera tracking from the side, cyberpunk, cinematic"}],
    "stream": false
  }'

# Shot 3: Close-up
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a video: Close-up of a woman looking up in wonder, neon reflections on her face, rain drops, shallow depth of field, camera slowly pushing in, cyberpunk, cinematic"}],
    "stream": false
  }'
```

## Related Skills

- [Image to Video](../image-to-video/SKILL.md) — Animate still images
- [AI Cinematic Trailer](../ai-cinematic-trailer/SKILL.md) — Movie-style trailers
- [AI Video Loop](../ai-video-loop/SKILL.md) — Seamless looping videos
- [AI Slow Motion](../ai-slow-motion/SKILL.md) — Slow motion effects

## Related Models

- [wan-2-1-14b](../../../models/wan-2-1-14b/SKILL.md) — High quality video generation
- [hailuo-minimax-video-01](../../../models/hailuo-minimax-video-01/SKILL.md) — Fast video generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
