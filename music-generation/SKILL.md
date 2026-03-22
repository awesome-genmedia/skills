---
name: music-generation
description: "Generate instrumental music and background tracks using each::sense AI. Create royalty-free instrumentals, background music, soundscapes, and compositions across all genres. Control tempo, instruments, mood, and duration. Use for: background music, YouTube videos, game soundtracks, podcast beds, ad music, ambient tracks, film scores. Triggers: generate music, instrumental, background music, beat, soundtrack, compose music, ai music, music generator, bgm, score, ambient music, backing track, instrumental track"
allowed-tools: Bash(curl *), WebFetch
---

# Music Generation

Generate instrumental music and background tracks using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a chill lo-fi hip-hop instrumental, 85 BPM, with warm Rhodes piano, vinyl crackle, mellow drum loop, and a soft bass line. 45 seconds long, perfect for a study playlist."}],
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
    messages=[{"role": "user", "content": "Generate a chill lo-fi hip-hop instrumental, 85 BPM, with warm Rhodes piano, vinyl crackle, mellow drum loop, and a soft bass line. 45 seconds long, perfect for a study playlist."}]
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate instrumental background music that matches the mood and atmosphere of this image. Create a soundscape that a viewer would expect to hear while looking at this scene."}],
    "image_urls": ["https://example.com/scenic-photo.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Available Models

| Model | Strengths | Best For |
|-------|-----------|----------|
| **mureka-generate-music** | Full music generation with rich arrangements | Complete instrumentals, complex compositions |
| **stable-audio-2-5** | High-quality short audio, precise control | Loops, short clips, sound design, ambient textures |

> each::sense picks the optimal model based on your prompt. Specify "instrumental" or "no vocals" to ensure vocal-free output.

## Genre Guide

| Genre | Typical BPM | Key Instruments | Use Cases |
|-------|-------------|-----------------|-----------|
| **Lo-fi** | 70-90 | Rhodes piano, vinyl crackle, soft drums | Study music, chill content |
| **Ambient** | 50-80 | Synth pads, reverb textures, field recordings | Meditation, backgrounds, ASMR |
| **Cinematic** | 60-120 | Strings, brass, percussion, choir | Film scores, trailers, presentations |
| **Electronic** | 120-150 | Synths, drum machines, bass, arps | Gaming, workout, energetic content |
| **Jazz** | 80-140 | Piano, upright bass, brushed drums, sax | Restaurants, vlogs, sophisticated content |
| **Classical** | 60-130 | Piano, strings, woodwinds, orchestra | Elegant content, education, focus |
| **Hip-Hop** | 80-100 | 808s, hi-hats, samples, bass | Rap beats, urban content |
| **Rock** | 100-140 | Electric guitar, drums, bass, organ | Action content, sports, energy |
| **World** | 70-130 | Tabla, koto, sitar, djembe, kalimba | Travel content, cultural videos |
| **Synthwave** | 80-120 | Analog synths, arpeggios, gated reverb | Retro content, 80s aesthetic |

## Prompt Tips

### The Instrumental Prompt Formula

```
Generate a [genre] instrumental, [BPM] BPM, with [instruments].
[Mood/emotion] feel. [Duration] long. [Use case context].
```

### Mood Keywords

```
uplifting, melancholic, triumphant, mysterious, relaxing, intense,
dreamy, aggressive, playful, dark, cinematic, nostalgic, epic,
serene, brooding, whimsical, majestic, eerie, warm, ethereal
```

### Dynamic Instructions

Describe how the track should evolve over time:

```
"Start with solo piano, add strings at 10 seconds,
build to full orchestra by 30 seconds, then
pull back to piano and cello for the ending."
```

### Avoiding Vocals

Be explicit when you want instrumental-only output:

```
"Generate an instrumental track, no vocals, no singing, no humming"
```

## Examples

### Cinematic Epic Score

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate an epic cinematic orchestral instrumental. Starts quiet with a solo cello melody, builds with layered strings and French horns, crescendo with full orchestra, timpani rolls, and crashing cymbals. Heroic and triumphant mood. 60 seconds, suitable for a movie trailer. No vocals."}],
    "stream": false
  }'
```

### YouTube Background Music

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a friendly, upbeat background instrumental for a tech review YouTube video. Acoustic guitar, light percussion, subtle synth pad, and pizzicato strings. 110 BPM. Not too busy so it does not compete with narration. 45 seconds, seamless loop potential."}],
    "stream": false
  }'
```

### Ambient Soundscape

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a deep ambient soundscape for a meditation app. No rhythm or percussion. Slow-evolving synthesizer pads, distant wind chimes, subtle harmonic overtones, and soft low-frequency drones. Peaceful and spacious. 60 seconds. Very slow, almost timeless feel."}],
    "stream": false
  }'
```

### Jazz Trio

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a smooth jazz trio instrumental. Piano playing soft chord voicings, walking upright bass, and brushed snare drums with occasional cymbal rides. 105 BPM, relaxed swing feel. Think late-night jazz club atmosphere. 45 seconds. Warm and sophisticated."}],
    "stream": false
  }'
```

### Game Soundtrack

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a retro synthwave instrumental for an indie platformer game. Pulsing analog bass synth, bright arpeggio lead, gated snare reverb, and warm analog pad. 100 BPM. Nostalgic 80s vibe but modern production quality. Energetic and adventurous. 30 seconds, loopable."}],
    "stream": false
  }'
```

## Workflow: Music for Video

```bash
# Step 1: Generate background music
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a gentle acoustic instrumental for a travel vlog montage. Fingerpicked guitar, soft tambourine, light strings. Warm and wanderlust feeling. 100 BPM, 45 seconds. No vocals."}],
    "stream": false
  }'

# Step 2: Refine with multi-turn conversation
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {"role": "user", "content": "Generate a gentle acoustic instrumental for a travel vlog montage. Fingerpicked guitar, soft tambourine, light strings. 100 BPM, 45 seconds. No vocals."},
      {"role": "assistant", "content": "..."},
      {"role": "user", "content": "Great vibe. Now make a more energetic variation for the action segments. Same instruments but faster at 130 BPM with more percussion. 30 seconds."}
    ],
    "stream": false
  }'
```

## Common Pitfalls

- **Not specifying "instrumental"** may produce tracks with vocals. Be explicit: "no vocals."
- **Missing BPM** leaves tempo to chance. Always include target BPM for consistent results.
- **Vague instrument lists** like "some music" give generic output. Name specific instruments.
- **Duration ambiguity** can produce clips that are too short or too long. State duration clearly.
- **Ignoring dynamics** results in flat tracks. Describe how energy should build and release.

## Related Skills

- [Song Generation](../song-generation/SKILL.md) — Full songs with vocals and lyrics
- [Sound Effects](../sound-effects/SKILL.md) — Layer sound effects with your music
- [Lyrics Generation](../lyrics-generation/SKILL.md) — Write lyrics to pair with instrumentals
- [Voice Generation](../voice-generation/SKILL.md) — Add narration over instrumental tracks

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
