---
name: ai-educational-video
description: "Generate educational and tutorial videos using each::sense AI. Create animated explainer videos, science demonstrations, historical reenactment clips, step-by-step tutorials, and visual lectures for e-learning platforms. Use for: educational videos, tutorials, e-learning content, explainer animations, science visualizations, lecture visuals. Triggers: educational video, tutorial video, explainer video, e-learning, lecture video, science video, how-to video, teaching video, training video, instructional video"
allowed-tools: Bash(curl *), WebFetch
---

# AI Educational Video Generator

Generate educational and tutorial video content for e-learning and classroom use using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a short educational video showing the solar system: planets orbiting the sun in sequence from Mercury to Neptune, each planet correctly sized relative to the others, smooth orbital motion, dark space background with stars, scientific visualization style"
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
        "content": "Generate a short educational video showing the solar system: planets orbiting the sun in sequence from Mercury to Neptune, each planet correctly sized relative to the others, smooth orbital motion, dark space background with stars, scientific visualization style"
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
        "content": [
              {"type": "text", "text": "Animate this diagram into a short educational video: show each component appearing one by one with smooth transitions, highlight connections between parts, gentle zoom and pan effects, clean educational presentation style"},
              {"type": "image_url", "image_url": {"url": "https://example.com/science-diagram.png"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Educational Videos

- **Describe the visual progression** — explain what happens step by step in the animation.
- **Keep scenes focused** — one concept or process per video clip works best.
- **Specify the visualization style** — "3D scientific," "2D animation," "whiteboard sketch," or "motion graphics."
- **Include motion cues** — "zoom into," "rotate around," "pan across," "fade between stages."
- **Combine with audio** — pair generated video with text-to-speech narration for complete lessons.

## Examples

### Chemistry Reaction Visualization

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A short educational video showing a chemical reaction at the molecular level: two molecules approaching each other, bonds breaking and reforming into new molecules, glowing energy release at the moment of reaction, 3D molecular visualization, dark background with soft lighting, scientific animation style"
      }
    ],
    "stream": false
  }'
```

### Historical Scene

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A short video depicting an ancient Roman marketplace: bustling scene with merchants selling goods at stone stalls, citizens in togas walking through columned archways, slow camera pan through the forum, warm Mediterranean light, cinematic historical reconstruction style"
      }
    ],
    "stream": false
  }'
```

### Step-by-Step Tutorial

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video showing hands demonstrating origami: paper being folded step by step into a crane shape on a wooden desk, overhead camera angle, natural lighting, close-up detail of precise folds, calm and methodical tutorial pace"
      }
    ],
    "stream": false
  }'
```

## Workflow: E-Learning Video Production

1. **Script the lesson** — Outline the concept and visual progression.
2. **Generate key visual scenes** — Create video clips for each step or concept.
3. **Create supplementary diagrams** — Use the diagram generator for static reference visuals.
4. **Add narration** — Generate voiceover with text-to-speech.
5. **Assemble in editor** — Combine video clips, diagrams, narration, and captions.
6. **Review for accuracy** — Verify that visual content correctly represents the concept.

## Related Skills

- [AI Diagram Generator](../ai-diagram-generator/SKILL.md) — Static educational diagrams
- [AI Flashcard Generator](../ai-flashcard-generator/SKILL.md) — Visual study cards
- [AI Illustration](../ai-illustration/SKILL.md) — Detailed educational illustrations
- [Text to Speech](../../audio/text-to-speech/SKILL.md) — Generate narration audio
- [Image to Video Pipeline](../../workflows/image-to-video-pipeline/SKILL.md) — Animate still images

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-quality visual generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative animation styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick scene prototyping

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
