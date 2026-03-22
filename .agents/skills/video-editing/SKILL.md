---
name: video-editing
description: "Edit existing videos with AI using each::sense. Apply effects, color grading, speed changes, trimming, transitions, style transfer, and visual enhancements. Transform raw footage into polished content. Use for: color grading, speed ramping, style transfer, video enhancement, social media edits, content post-production. Triggers: edit video, video editing, color grade, speed change, video effects, trim video, video filter, slow motion, timelapse, video style, video enhance, post production"
allowed-tools: Bash(curl *), WebFetch
---

# Video Editing

Edit and transform existing videos with AI-powered tools using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Apply a warm cinematic color grade to this video. Boost the orange tones in highlights and teal in the shadows, add slight film grain."},
              {"type": "image_url", "image_url": {"url": "https://example.com/raw-footage.mp4"}}
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
    messages=[{"role": "user", "content": "Apply a warm cinematic color grade to this video. Boost the orange tones in highlights and teal in the shadows, add slight film grain."}],
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
              {"type": "text", "text": "Apply the color grading and visual style from this reference image to my video clip"},
              {"type": "image_url", "image_url": {"url": "https://example.com/my-video.mp4"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/style-reference.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Editing Capabilities

| Category | What You Can Do | Example Instruction |
|----------|----------------|---------------------|
| **Color Grading** | Adjust colors, contrast, mood | "Apply a moody teal and orange color grade" |
| **Speed Control** | Slow motion, timelapse, ramping | "Convert to smooth slow motion at 0.5x speed" |
| **Style Transfer** | Apply artistic styles | "Make this look like a Wes Anderson film" |
| **Enhancement** | Sharpen, denoise, stabilize | "Stabilize the shaky handheld footage" |
| **Trimming** | Cut and select portions | "Keep only the first 5 seconds of this clip" |
| **Effects** | Add visual effects | "Add a subtle lens flare when the sun appears" |
| **Format** | Change aspect ratio, crop | "Crop to 9:16 vertical for TikTok, focus on the center subject" |
| **Transitions** | Add transition effects | "Add a smooth fade-in at the start and fade-out at the end" |

## Prompt Tips

### Describe the Target Look

Be specific about the visual outcome you want:

```
"Make this look like it was shot on 35mm Kodak Portra 400 film.
Desaturate slightly, add warm highlights, lift the blacks,
and include subtle film grain."
```

### Specify Temporal Changes

When edits should apply to specific moments:

```
"Slow motion from 0:02 to 0:04 when the ball is in the air,
then return to normal speed."
```

### Reference-Based Editing

Use a second image or frame as a style reference:

```
"Match the color grading of the reference image.
Apply the same contrast, saturation, and color temperature."
```

## Examples

### Cinematic Color Grade

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Apply a cinematic color grade inspired by Blade Runner 2049. Push shadows toward deep blue, highlights toward warm amber. High contrast, slightly desaturated midtones, add atmospheric haze effect."},
              {"type": "image_url", "image_url": {"url": "https://example.com/city-footage.mp4"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Slow Motion Effect

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Convert this video to smooth slow motion at 0.25x speed. Use frame interpolation to keep the motion fluid and artifact-free. Maintain the original resolution."},
              {"type": "image_url", "image_url": {"url": "https://example.com/action-clip.mp4"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Style Transfer to Animation

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Transform this real-world video into a Studio Ghibli anime style. Keep the motion and composition, but render everything as hand-painted animation with soft colors and visible brushstrokes."},
              {"type": "image_url", "image_url": {"url": "https://example.com/nature-walk.mp4"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Social Media Reformat

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Reformat this 16:9 landscape video to 9:16 vertical for TikTok. Intelligently crop to keep the main subject centered. Add a quick zoom-in effect at the beginning for engagement."},
              {"type": "image_url", "image_url": {"url": "https://example.com/horizontal-clip.mp4"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Vintage Film Effect

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Make this video look like it was recorded on a VHS camcorder from the 1990s. Add scan lines, tracking artifacts, slight color bleeding, a date stamp in the corner reading 08/15/1994, and lower the resolution slightly."},
              {"type": "image_url", "image_url": {"url": "https://example.com/modern-video.mp4"}}
            ]
          }
    ],
    "stream": false
  }'
```

## Color Grading Presets

Common color grading descriptions to use in your prompts:

| Style | Description |
|-------|-------------|
| **Teal & Orange** | Cool shadows, warm highlights, popular blockbuster look |
| **Film Noir** | High contrast black and white, deep shadows, sharp highlights |
| **Vintage Film** | Lifted blacks, faded highlights, warm muted tones |
| **Neon Cyberpunk** | Saturated magentas and cyans, high contrast, dark blacks |
| **Pastel Dream** | Desaturated, lifted shadows, soft pink and blue tones |
| **Documentary** | Natural colors, slight desaturation, neutral contrast |
| **Golden Hour** | Warm amber tones, soft contrast, glowing highlights |
| **Nordic Minimal** | Cool desaturated blues and grays, low contrast, clean |

## Common Pitfalls

- **Vague instructions** like "make it look cool" give inconsistent results. Describe the specific look.
- **Ignoring temporal context** when the edit should apply to specific moments in the clip.
- **Expecting frame-accurate cuts** from natural language. For precise trimming, include timestamps.
- **Over-processing** by requesting too many effects at once. Apply edits in stages for best results.
- **Forgetting source quality** matters. Low-resolution input limits what enhancements can achieve.

## Related Skills

- [Video Generation](../video-generation/SKILL.md) — Generate videos from scratch
- [Image Editing](../image-editing/SKILL.md) — Edit individual frames or thumbnails
- [Sound Effects](../sound-effects/SKILL.md) — Add audio effects to edited videos
- [Music Generation](../music-generation/SKILL.md) — Create background music for video edits

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
