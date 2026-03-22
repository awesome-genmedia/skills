---
name: ai-testimonial-video
description: "Generate customer testimonial style videos using each::sense AI. Create talking-head style videos, animated quote visuals, and testimonial scene compositions for marketing. Use for: customer testimonials, review videos, case study visuals, social proof content, testimonial ads. Triggers: testimonial video, customer review, testimonial, talking head, review video, social proof video, case study video, customer story, testimonial ad, quote video"
allowed-tools: Bash(curl *), WebFetch
---

# AI Testimonial Video Generator

Generate customer testimonial style video content for marketing campaigns using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a short video of a professional woman in her 30s sitting in a modern office, speaking directly to the camera with a warm genuine smile, natural lighting from a window to her left, shallow depth of field, testimonial interview style, corporate but approachable"
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
        "content": "Generate a short video of a professional woman in her 30s sitting in a modern office, speaking directly to the camera with a warm genuine smile, natural lighting from a window to her left, shallow depth of field, testimonial interview style, corporate but approachable"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Animate this portrait into a testimonial-style video: the person gently nods and speaks to camera, subtle natural head movements, professional interview lighting, soft background blur"
      }
    ],
    "image_urls": ["https://example.com/portrait.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Testimonial Videos

- **Describe the setting realistically** — office, home, cafe, or outdoor settings give context and credibility.
- **Specify camera framing** — "medium close-up," "head and shoulders," or "waist up" for classic testimonial framing.
- **Include subtle motion cues** — "gentle head nod," "slight gesturing," "looking to camera" for natural movement.
- **Match your brand environment** — specify background elements and color tones.
- **Pair with voiceover** — use text-to-speech skills to add narration to the generated video.

## Examples

### Corporate Testimonial Scene

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A short video of a middle-aged businessman in a navy suit sitting in a boardroom, speaking to camera with confident gestures, large windows showing a city skyline behind him, warm professional lighting, shallow depth of field, corporate testimonial interview"
      }
    ],
    "stream": false
  }'
```

### Casual Customer Review

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video of a young man in a casual t-shirt sitting on a couch in a bright living room, talking to camera with an enthusiastic expression, holding a phone in one hand, natural daylight, candid vlog-style testimonial"
      }
    ],
    "stream": false
  }'
```

### Healthcare Professional Testimonial

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A short video of a female doctor in a white coat sitting in a clean modern medical office, speaking calmly to camera, stethoscope around her neck, neutral medical background, soft even lighting, professional healthcare testimonial style"
      }
    ],
    "stream": false
  }'
```

## Workflow: Testimonial Video Production

1. **Define the persona** — Describe the speaker's role, appearance, and setting.
2. **Generate the base video** — Create the talking-head testimonial clip.
3. **Add voiceover** — Use text-to-speech to create the audio narration.
4. **Create B-roll** — Generate supplementary video clips of product usage or outcomes.
5. **Compose in editor** — Combine testimonial video, B-roll, audio, and text overlays.

## Related Skills

- [AI Ad Creative](../ai-ad-creative/SKILL.md) — Ad visuals to accompany testimonials
- [AI Campaign Visuals](../ai-campaign-visuals/SKILL.md) — Multi-format campaign assets
- [Text to Speech](../../audio/text-to-speech/SKILL.md) — Generate voiceover audio
- [Image to Video Pipeline](../../workflows/image-to-video-pipeline/SKILL.md) — Animate stills into video

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-quality portrait generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Expressive visual styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations for scene exploration

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
