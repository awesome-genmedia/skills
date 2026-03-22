---
name: song-generation
description: "Generate complete songs with vocals and instrumentals using each::sense AI. Create original music with singing, lyrics, full production across pop, rock, hip-hop, R&B, country, electronic, and more. Control genre, mood, tempo, and vocal style. Use for: original songs, demo tracks, jingles, social media audio, creative projects. Triggers: generate song, create song, ai song, song maker, song with lyrics, sing, vocal track, make a song, write a song, song generator, ai singer, music with vocals"
allowed-tools: Bash(curl *), WebFetch
---

# Song Generation

Generate complete songs with vocals and full instrumental production using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate an upbeat indie pop song about road trips and summer freedom, female vocal, 120 BPM, with acoustic guitar, claps, and a catchy whistling hook in the chorus"}],
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
    messages=[{"role": "user", "content": "Generate an upbeat indie pop song about road trips and summer freedom, female vocal, 120 BPM, with acoustic guitar, claps, and a catchy whistling hook in the chorus"}]
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
              {"type": "text", "text": "Generate a song inspired by the mood and atmosphere of this image. Match the emotion, whether it feels melancholy, joyful, or mysterious."},
              {"type": "image_url", "image_url": {"url": "https://example.com/mood-photo.jpg"}}
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
| **mureka-generate-music** | Full song generation with vocals, lyrics, and production | Complete songs across all genres |
| **stable-audio-2-5** | High-quality short audio generation | Short musical snippets, hooks, intros |

> each::sense automatically selects the right model. For full songs with vocals, mureka-generate-music is the primary model.

## Song Structure Guide

### Standard Song Structures

| Structure | Pattern | Duration |
|-----------|---------|----------|
| **Pop Standard** | Verse - Chorus - Verse - Chorus - Bridge - Chorus | 3-4 min |
| **Simple** | Verse - Chorus - Verse - Chorus | 2-3 min |
| **Extended** | Intro - Verse - Pre-Chorus - Chorus - Verse - Pre-Chorus - Chorus - Bridge - Chorus - Outro | 4-5 min |
| **Hip-Hop** | Intro - Verse - Hook - Verse - Hook - Verse - Hook - Outro | 3-4 min |
| **Ballad** | Intro - Verse - Verse - Chorus - Verse - Chorus - Outro | 3-5 min |

### Providing Lyrics

Include lyrics directly in your prompt with structure markers:

```
Generate a pop rock song, male vocal, 110 BPM:

[Verse 1]
Walking down these empty streets at dawn
Shadows fading as the night moves on
Every step I take leads back to you
Underneath this sky of fading blue

[Chorus]
We were golden, we were fire
Burning brighter, climbing higher
Now I'm standing in the rain
Chasing echoes of your name
```

## Genre Guide

| Genre | Typical BPM | Key Descriptors | Vocal Style |
|-------|-------------|-----------------|-------------|
| **Pop** | 100-130 | Catchy hooks, polished production | Clean, bright, harmonized |
| **Rock** | 110-140 | Electric guitar, driving drums | Powerful, raw, dynamic |
| **Hip-Hop** | 80-100 | 808 bass, hi-hats, trap beats | Rhythmic flow, rap |
| **R&B** | 60-90 | Smooth bass, lush chords | Soulful, melismatic |
| **Country** | 90-130 | Acoustic guitar, fiddle, steel guitar | Warm, storytelling |
| **Electronic** | 120-150 | Synths, drops, build-ups | Processed, vocoded, chopped |
| **Indie** | 100-130 | Lo-fi textures, jangly guitars | Intimate, conversational |
| **Jazz** | 80-140 | Swing, improvisation, brass | Smooth, scatting |

## Prompt Tips

### Vocal Specification

Be explicit about the vocal characteristics:

```
"female vocal, alto range, smooth and breathy tone"
"male vocal, deep baritone, raspy rock voice"
"duet with male and female vocals trading verses"
"choir-style harmonies in the chorus"
```

### Mood and Emotion

Layer emotional descriptors for nuanced output:

```
"bittersweet and nostalgic, like remembering a perfect day you can never return to"
"triumphant and empowering, building from quiet determination to explosive confidence"
```

### Instrumentation Details

List specific instruments for precise control:

```
"acoustic guitar, brush drums, upright bass, warm Rhodes piano, subtle strings"
"heavy distorted electric guitar, double kick drums, bass guitar, screaming lead solo"
```

## Examples

### Pop Song with Custom Lyrics

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate an upbeat pop song, female vocal, 118 BPM, with synth bass and claps:\n\n[Verse 1]\nWoke up to the golden light\nEverything is feeling right\nGot my coffee, got my song\nNothing here can go wrong\n\n[Chorus]\nThis is our summer, this is our time\nDancing in the sunshine, feeling so alive\nWe are unstoppable, we are on fire\nTaking it higher and higher"}],
    "stream": false
  }'
```

### Rock Anthem

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate an arena rock anthem about never giving up. Male vocal with a gritty, powerful voice. 130 BPM. Driving electric guitar riff, pounding drums, bass guitar, and a massive singalong chorus. Think Foo Fighters meets Queen. 3 minutes long."}],
    "stream": false
  }'
```

### Hip-Hop Track

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a chill hip-hop track about city nights and ambition. Male rap vocal with a smooth flow. 88 BPM. Dark trap beat with 808 bass, hi-hats, ambient synth pads, and a soulful R&B female vocal hook on the chorus. Moody and atmospheric."}],
    "stream": false
  }'
```

### Acoustic Ballad

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a tender acoustic ballad about saying goodbye to a childhood home. Female vocal, intimate and emotional. 72 BPM. Fingerpicked acoustic guitar, soft cello, and gentle piano. Build to a fuller arrangement in the final chorus with strings. Bittersweet and moving."}],
    "stream": false
  }'
```

### Jingle / Short Song

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a 15-second catchy jingle for a coffee brand called Morning Brew. Upbeat and cheerful, male and female vocals harmonizing, ukulele and handclaps, with the tagline: Rise and brew, the best in you. Earworm melody that sticks."}],
    "stream": false
  }'
```

## Common Pitfalls

- **No vocal direction** produces generic voices. Always specify gender, style, and energy level.
- **Missing tempo** lets the model guess BPM, which may not match your vision. Specify BPM.
- **Lyrics without structure markers** make it hard for the model to assign verses and choruses correctly.
- **Too many genre mixes** (e.g., "jazz-metal-country-electronic fusion") dilute the output. Blend 2 genres maximum.
- **Ignoring song length** may produce clips that are too short or too long for your needs.

## Related Skills

- [Lyrics Generation](../lyrics-generation/SKILL.md) — Generate lyrics first, then produce the song
- [Music Generation](../music-generation/SKILL.md) — Instrumental-only tracks without vocals
- [Voice Generation](../voice-generation/SKILL.md) — Generate spoken word or narration audio
- [Sound Effects](../sound-effects/SKILL.md) — Layer effects into your productions

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
