---
name: sound-effects
description: "Generate custom sound effects using each::sense AI. Create realistic and stylized audio for any scenario including impacts, ambiences, foley, UI sounds, nature, mechanical effects, and transitions. Powered by stable-audio-2-5 for precise audio generation. Use for: video production, game development, podcasts, apps, UI/UX, presentations, film. Triggers: sound effect, sfx, audio effect, foley, generate sound, ambient sound, ui sound, impact sound, whoosh, explosion, nature sound, notification sound, create audio"
allowed-tools: Bash(curl *), WebFetch
---

# Sound Effects

Generate custom sound effects for any use case using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a sound effect: a heavy wooden door creaking open slowly in a stone castle hallway, with echo and reverb. 3 seconds long."}],
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
    messages=[{"role": "user", "content": "Generate a sound effect: a heavy wooden door creaking open slowly in a stone castle hallway, with echo and reverb. 3 seconds long."}]
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
              {"type": "text", "text": "Generate realistic sound effects that match this scene. Create the ambient soundscape a viewer would hear if they were standing in this location."},
              {"type": "image_url", "image_url": {"url": "https://example.com/forest-scene.jpg"}}
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

| Model | Strengths | Best For |
|-------|-----------|----------|
| **stable-audio-2-5** | Precise audio generation, short-form content, high quality | Sound effects, foley, ambiences, UI sounds |
| **mureka-generate-music** | Musical sound design, tonal effects | Musical stingers, jingles, tonal transitions |

## Sound Effect Categories

| Category | Examples | Typical Duration |
|----------|----------|-----------------|
| **Nature** | Rain, thunder, wind, birds, ocean waves, fire crackling | 3-30 sec |
| **Impacts** | Punch, crash, explosion, slam, shatter, thud | 0.5-3 sec |
| **Mechanical** | Engine start, gear shift, hydraulic press, clock ticking | 1-10 sec |
| **UI / Digital** | Notification ping, button click, error buzz, level up chime | 0.1-2 sec |
| **Foley** | Footsteps, cloth rustle, paper crumple, pouring liquid | 1-5 sec |
| **Transitions** | Whoosh, swoosh, riser, reverse cymbal, stinger | 0.5-3 sec |
| **Sci-Fi** | Laser blast, warp drive, force field hum, alien chatter | 0.5-5 sec |
| **Horror** | Creaking floorboard, whisper, distant scream, heartbeat | 1-10 sec |
| **Cartoon** | Boing, splat, slide whistle, comedy honk | 0.5-2 sec |
| **Ambient** | Coffee shop murmur, office hum, city traffic, subway | 10-30 sec |

## Prompt Tips

### Sound Effect Prompt Formula

```
Generate a sound effect: [what it is] + [material/texture] + [environment/space] + [duration]
```

### Describing Sound Qualities

| Quality | Keywords |
|---------|----------|
| **Bright** | crisp, sharp, metallic, ringing, clear |
| **Dark** | deep, rumbling, low, muffled, thick |
| **Wet** | reverb, echo, spacious, cavernous, underwater |
| **Dry** | close-mic, tight, no reverb, intimate |
| **Distorted** | overdriven, gritty, clipped, saturated |
| **Clean** | pure, pristine, digital, polished |

### Duration Guidelines

Be specific about length:

```
"0.5 seconds" — quick hits, clicks, notifications
"1-3 seconds" — impacts, transitions, short effects
"5-10 seconds" — ambient loops, longer foley
"15-30 seconds" — environment ambiences, atmospheric beds
```

### Layering Instructions

Request multiple elements in one effect:

```
"A thunderclap with: initial crack, rolling rumble that
fades over 5 seconds, light rain in the background throughout"
```

## Examples

### Cinematic Impact

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a sound effect: cinematic deep bass impact hit followed by a reverb tail that decays over 3 seconds. Like a movie trailer boom. Massive sub-bass presence, felt in the chest. Dry initial hit, then spacious reverb."}],
    "stream": false
  }'
```

### UI Notification Sound

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a sound effect: a pleasant, subtle notification chime for a mobile app. Two ascending xylophone-like tones, bright and friendly. 0.5 seconds total. Clean and digital, not overly attention-grabbing. Think premium tech product."}],
    "stream": false
  }'
```

### Nature Ambience

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a sound effect: a peaceful forest ambience at dawn. Gentle birdsong from multiple species at varying distances, a soft breeze rustling through leaves, a distant stream trickling over rocks. 20 seconds long. Naturalistic and immersive."}],
    "stream": false
  }'
```

### Sci-Fi Laser

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a sound effect: a futuristic laser blaster firing three rapid shots. Each shot has a sharp zap with a synthesized sizzle tail. High-pitched, energetic, slightly different pitch for each shot. 1.5 seconds total. Sci-fi video game style."}],
    "stream": false
  }'
```

### Horror Atmosphere

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a sound effect: unsettling horror ambience for a haunted house scene. Low droning hum, occasional distant creaking wood, a faint whisper that passes from left to right, and a single slow heartbeat. 15 seconds. Dark, tense, and deeply unsettling."}],
    "stream": false
  }'
```

## Batch Sound Effect Generation

```bash
# Generate a complete UI sound kit
EFFECTS=(
  "Generate a sound effect: app launch whoosh, 0.3 seconds, bright and modern"
  "Generate a sound effect: button tap click, soft and tactile, 0.1 seconds"
  "Generate a sound effect: success completion chime, three ascending notes, 0.8 seconds, cheerful"
  "Generate a sound effect: error notification, two low descending tones, 0.5 seconds, gentle warning"
  "Generate a sound effect: message received ping, single bright bell tone, 0.3 seconds, pleasant"
)

for EFFECT in "${EFFECTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$EFFECT\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **No duration** lets the model guess length, which may not fit your project. Always specify duration.
- **Too vague** ("a cool sound") produces generic results. Describe the sound with physical detail.
- **Expecting exact replication** of specific copyrighted sounds is unreliable. Describe the characteristics instead.
- **Ignoring the environment** produces context-free sounds. Mention reverb, room size, and distance for realism.
- **Overloaded requests** with too many simultaneous elements may produce muddy audio. Layer complex scenes from individual effects.

## Related Skills

- [Music Generation](../music-generation/SKILL.md) — Generate instrumental music and background tracks
- [Voice Generation](../voice-generation/SKILL.md) — Generate voice audio to layer with sound effects
- [Video Generation](../video-generation/SKILL.md) — Create videos with matched audio
- [Song Generation](../song-generation/SKILL.md) — Full song production with effects

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
