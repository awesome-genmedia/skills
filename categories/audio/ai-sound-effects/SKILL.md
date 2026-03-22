---
name: ai-sound-effects
description: "Create custom sound effects using each::sense AI. Generate realistic or stylized audio for explosions, footsteps, weather, sci-fi, UI sounds, nature, vehicles, and more. Perfect for any project needing unique audio assets. Use for: game development, video editing, app UI sounds, film foley, animation, podcast production. Triggers: sound effect, sfx, audio effect, foley, game sound, ui sound, notification sound, explosion sound, nature sound, ambient sound, create sfx, generate sound"
allowed-tools: Bash(curl *), WebFetch
---

# AI Sound Effects

Create custom sound effects for any project using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a sound effect: heavy rain on a tin roof with distant thunder rumbling, 10 seconds long, realistic and immersive"
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
        "content": "Generate a sound effect: heavy rain on a tin roof with distant thunder rumbling, 10 seconds long, realistic and immersive"
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Sound Effect Categories

| Category | Examples | Common Uses |
|---|---|---|
| **Nature** | Rain, wind, birds, ocean, fire | Film, meditation apps, games |
| **Mechanical** | Engines, gears, doors, machines | Sci-fi, industrial videos |
| **Impact** | Explosions, crashes, punches, drops | Games, action sequences |
| **UI/Digital** | Clicks, notifications, whoosh, beeps | Apps, websites, software |
| **Sci-fi** | Lasers, teleportation, force fields | Games, movies, trailers |
| **Human** | Crowd cheer, footsteps, applause | Film, podcasts, presentations |
| **Animals** | Dogs barking, birds chirping, horses | Nature docs, games, films |
| **Musical** | Stingers, risers, transitions | Video editing, broadcasts |

## Prompt Engineering Tips

### Be Descriptive About the Sound

Describe the physical properties of the sound: what is making it, the environment, material, intensity, and duration.

```
Generate a sound effect: [source] [action] in [environment], [intensity], [duration] long
```

### Useful Descriptors

```
metallic, wooden, glass, wet, dry, hollow, sharp, muffled,
echoing, close-up, distant, rapid, slow, layered, single
```

### Duration Guidelines

- **UI sounds**: 0.5-2 seconds
- **Impacts**: 1-3 seconds
- **Ambience**: 10-30 seconds
- **Transitions**: 1-5 seconds

## Examples

### Sci-fi Laser Blast

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a sound effect: futuristic laser blaster firing three quick shots, high-pitched zap with a low reverb tail, sci-fi energy weapon style, 2 seconds total"
      }
    ],
    "stream": false
  }'
```

### Forest Ambience

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a sound effect: peaceful forest ambience with birds singing, gentle breeze through leaves, a distant stream flowing over rocks, no human sounds. 15 seconds, loopable."
      }
    ],
    "stream": false
  }'
```

### App Notification Sound

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a sound effect: a friendly, short notification chime for a mobile app. Two ascending tones, bright and pleasant, like a marimba tap. Under 1 second, clean and modern."
      }
    ],
    "stream": false
  }'
```

### Cinematic Whoosh Transition

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a sound effect: cinematic whoosh transition, starts from the left, sweeps to the right, deep bass undertone with a high-frequency air trail. 1.5 seconds, dramatic and punchy."
      }
    ],
    "stream": false
  }'
```

## Workflow: Building a Sound Design Library

```bash
# Step 1: Generate a base ambient loop
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a sound effect: busy city street ambience, car traffic, distant sirens, pedestrian chatter, urban daytime. 15 seconds, loopable."
      }
    ],
    "stream": false
  }'

# Step 2: Generate accent sounds to layer on top
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a sound effect: car horn honking twice in a busy street, realistic, 2 seconds"
      }
    ],
    "stream": false
  }'

# Step 3: Generate a transition sound
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a sound effect: scene change swoosh, a quick low-frequency rumble with a high-pitched tail, cinematic. 1 second."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [AI Music Generator](../ai-music-generator/SKILL.md) — Full music tracks and instrumentals
- [AI Jingle Generator](../ai-jingle-generator/SKILL.md) — Short catchy tunes for brands
- [AI Voiceover](../ai-voiceover/SKILL.md) — Voiceover to pair with your sound design
- [AI Podcast Intro](../ai-podcast-intro/SKILL.md) — Intro music and sound beds

## Related Models

- [stable-audio](../../../models/stable-audio/SKILL.md) — High-quality audio generation
- [mmaudio](../../../models/mmaudio/SKILL.md) — Multimodal audio synthesis
- [ace-step](../../../models/ace-step/SKILL.md) — Music and audio generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
