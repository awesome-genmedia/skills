---
name: ai-music-generator
description: "Generate original music tracks using each::sense AI. Create songs, instrumentals, background music, and full compositions across genres including pop, lo-fi, jazz, electronic, orchestral, and hip-hop. Supports lyrics, mood specification, and tempo control. Use for: background music, YouTube videos, game soundtracks, ad music, royalty-free tracks, demo songs. Triggers: ai music, generate music, create song, music generator, instrumental, background music, beat maker, song generator, compose music, music creation, ai composer, soundtrack"
allowed-tools: Bash(curl *), WebFetch
---

# AI Music Generator

Generate original music tracks, songs, and instrumentals using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a chill lo-fi hip-hop instrumental, 90 BPM, with soft piano chords, vinyl crackle, and a mellow drum loop. 30 seconds long, perfect for a study playlist."
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
        "content": "Generate a chill lo-fi hip-hop instrumental, 90 BPM, with soft piano chords, vinyl crackle, and a mellow drum loop. 30 seconds long, perfect for a study playlist."
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Genre Guide

| Genre | Key Descriptors | Typical BPM |
|---|---|---|
| **Lo-fi** | Warm, vinyl, mellow, nostalgic | 70-90 |
| **Electronic/EDM** | Synth, bass drop, energetic, build-up | 120-140 |
| **Jazz** | Swing, improvisation, brass, smooth | 100-130 |
| **Orchestral** | Cinematic, strings, epic, dramatic | 60-120 |
| **Pop** | Catchy, upbeat, polished, hook-driven | 100-130 |
| **Hip-Hop** | Boom-bap, trap, 808s, flow | 80-100 |
| **Ambient** | Atmospheric, pad, ethereal, spacious | 60-80 |
| **Rock** | Guitar, drums, distortion, power | 110-140 |

## Prompt Engineering Tips

### Be Specific About Structure

Include details about instruments, tempo, mood, and duration. The more specific you are, the better the output matches your vision.

```
Generate a [genre] track, [BPM] BPM, with [instruments], [mood] feel, [duration] long
```

### Mood Keywords That Work

```
uplifting, melancholic, triumphant, mysterious, relaxing, intense,
dreamy, aggressive, playful, dark, cinematic, nostalgic, epic
```

### Lyrics Format

When requesting songs with lyrics, include them directly in the prompt with clear structure markers like verse, chorus, and bridge.

## Examples

### Cinematic Orchestral Score

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate an epic cinematic orchestral piece. Starts quiet with solo cello, builds with strings and French horns, crescendo with full orchestra and timpani. Heroic and triumphant mood. 45 seconds, suitable for a movie trailer."
      }
    ],
    "stream": false
  }'
```

### Pop Song with Lyrics

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate an upbeat pop song, 120 BPM, female vocal, with these lyrics:\n\n[Verse]\nWoke up to the golden light\nEverything is feeling right\nGot my coffee, got my song\nNothing here can go wrong\n\n[Chorus]\nThis is our summer, this is our time\nDancing in the sunshine, feeling so alive"
      }
    ],
    "stream": false
  }'
```

### Ambient Background Music

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a calm ambient track for a spa relaxation video. Soft synthesizer pads, gentle wind chimes, distant ocean waves, no percussion. Very slow tempo around 60 BPM. 60 seconds long. Peaceful and meditative."
      }
    ],
    "stream": false
  }'
```

### Electronic Dance Track

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a high-energy electronic dance track, 128 BPM. Start with a filtered synth build-up, add a driving four-on-the-floor kick, heavy sidechain compression on the bass, and a euphoric synth lead melody. Big drop at the 15-second mark. 30 seconds total."
      }
    ],
    "stream": false
  }'
```

## Workflow

```bash
# Step 1: Generate a short concept to test the vibe
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 15-second jazzy lo-fi beat with electric piano and brushed drums, 85 BPM, warm and nostalgic"
      }
    ],
    "stream": false
  }'

# Step 2: Refine and extend the concept
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 15-second jazzy lo-fi beat with electric piano and brushed drums, 85 BPM, warm and nostalgic"
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Great vibe. Now make it 45 seconds and add a muted trumpet melody in the second half, keep the same tempo and feel"
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [AI Sound Effects](../ai-sound-effects/SKILL.md) — Layer sound effects into your music
- [AI Jingle Generator](../ai-jingle-generator/SKILL.md) — Short catchy tunes for brands
- [AI Podcast Intro](../ai-podcast-intro/SKILL.md) — Music beds for podcast intros
- [Text to Speech](../text-to-speech/SKILL.md) — Add narration over your tracks

## Related Models

- [ace-step](../../../models/ace-step/SKILL.md) — Full song generation with lyrics
- [stable-audio](../../../models/stable-audio/SKILL.md) — High-quality music and audio
- [mmaudio](../../../models/mmaudio/SKILL.md) — Multimodal audio generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
