---
name: lyrics-generation
description: "Generate song lyrics using each::sense AI. Create original lyrics for any genre with proper song structure including verses, choruses, bridges, and pre-choruses. Control mood, theme, rhyme scheme, and syllable patterns. Use for: songwriting, creative writing, jingles, poetry, rap verses, musical theater. Triggers: generate lyrics, write lyrics, song lyrics, lyric writer, songwriting, write a song, rap lyrics, chorus lyrics, verse lyrics, lyric generator, ai lyrics, poem"
allowed-tools: Bash(curl *), WebFetch
---

# Lyrics Generation

Generate original song lyrics with professional structure and creative depth using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Write lyrics for an indie folk song about leaving a small town to chase your dreams. Bittersweet tone, 3 verses, a chorus, and a bridge. Use vivid imagery of back roads, train stations, and open skies."}],
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
    messages=[{"role": "user", "content": "Write lyrics for an indie folk song about leaving a small town to chase your dreams. Bittersweet tone, 3 verses, a chorus, and a bridge. Use vivid imagery of back roads, train stations, and open skies."}]
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
              {"type": "text", "text": "Write song lyrics inspired by the mood and scene in this image. Capture the emotion, colors, and atmosphere as poetic lyrics with a verse-chorus structure."},
              {"type": "image_url", "image_url": {"url": "https://example.com/inspiration-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Song Structure Reference

### Structure Markers

Use these labels in your prompts and expect them in the output:

| Marker | Purpose | Typical Lines |
|--------|---------|---------------|
| **[Intro]** | Spoken or minimal opening | 1-2 lines |
| **[Verse 1/2/3]** | Narrative progression, storytelling | 4-8 lines |
| **[Pre-Chorus]** | Builds tension before chorus | 2-4 lines |
| **[Chorus]** | Main hook, central message | 4-8 lines |
| **[Bridge]** | Contrast, new perspective, key change | 4-6 lines |
| **[Outro]** | Resolution, final statement | 2-4 lines |
| **[Hook]** | Hip-hop equivalent of chorus | 2-4 lines |
| **[Ad-lib]** | Background vocals, exclamations | 1-2 lines |

### Common Structures by Genre

| Genre | Recommended Structure |
|-------|----------------------|
| **Pop** | Verse - Pre-Chorus - Chorus - Verse - Pre-Chorus - Chorus - Bridge - Chorus |
| **Rock** | Verse - Chorus - Verse - Chorus - Solo - Chorus |
| **Hip-Hop** | Verse - Hook - Verse - Hook - Verse - Hook |
| **Country** | Verse - Chorus - Verse - Chorus - Bridge - Chorus |
| **Ballad** | Verse - Verse - Chorus - Verse - Chorus - Outro |
| **EDM** | Intro - Build - Drop - Verse - Build - Drop - Outro |

## Prompt Tips

### Specify the Details That Matter

The more context you give, the more tailored the lyrics:

```
"Write pop lyrics about long-distance love.
Rhyme scheme: ABAB in verses, AABB in chorus.
Mood: hopeful but aching.
Perspective: first person.
Include a metaphor about lighthouses."
```

### Rhyme Scheme Control

| Scheme | Pattern | Example |
|--------|---------|---------|
| **ABAB** | Alternating rhymes | Lines 1&3 rhyme, 2&4 rhyme |
| **AABB** | Couplets | Consecutive lines rhyme |
| **ABCB** | Simple ballad | Only 2nd and 4th lines rhyme |
| **Free** | No strict rhyme | Poetic, conversational |
| **Internal** | Rhymes within lines | "I'm pacing, chasing, facing the dawn" |

### Mood Keywords

```
joyful, melancholic, defiant, tender, aggressive, whimsical,
haunting, anthemic, intimate, rebellious, nostalgic, empowering,
brooding, playful, ethereal, raw, triumphant, wistful
```

## Examples

### Pop Love Song

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Write lyrics for an upbeat pop love song about meeting someone at a concert and feeling an instant connection. Structure: Verse 1, Pre-Chorus, Chorus, Verse 2, Pre-Chorus, Chorus, Bridge, Chorus. ABAB rhyme scheme in verses, catchy repetitive chorus. Include references to neon lights, bass drops, and heartbeats."}],
    "stream": false
  }'
```

### Rap Verse

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Write 3 rap verses and a hook about rising from nothing and building success through hard work. Internal rhyme schemes, clever wordplay, and multisyllabic rhymes. Confident but not arrogant tone. Reference late nights, hustle, doubters, and breakthrough moments. Hip-hop style, think Kendrick Lamar meets J. Cole."}],
    "stream": false
  }'
```

### Country Storytelling

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Write country song lyrics telling the story of a grandfather teaching his grandson to fish at their favorite lake. Warm and nostalgic. 3 verses, chorus, and bridge. Each verse covers a different life lesson learned by the water. Simple ABCB rhyme scheme. Imagery of sunrise, red bobbers, old tackle boxes, and quiet mornings."}],
    "stream": false
  }'
```

### Dark Indie Rock

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Write brooding indie rock lyrics about insomnia and overthinking at 3 AM. Moody and introspective. Verse-Chorus-Verse-Chorus-Bridge-Chorus structure. Use metaphors of static, empty rooms, and flickering screens. Free verse style with occasional rhymes. Short punchy lines in the chorus."}],
    "stream": false
  }'
```

### Jingle / Commercial Lyrics

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Write a short, catchy jingle lyric for an organic juice brand called Fresh Squeeze. 4-6 lines total. Must be upbeat, memorable, and include the brand name twice. Rhyming couplets. Focus on freshness, energy, and natural ingredients. Think earworm melody."}],
    "stream": false
  }'
```

## Lyrics-to-Song Workflow

Generate lyrics first, then produce the full song:

```bash
# Step 1: Generate lyrics
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Write pop song lyrics about chasing dreams in a big city. Verse-Chorus-Verse-Chorus-Bridge-Chorus. Uplifting and determined."}],
    "stream": false
  }'

# Step 2: Use the generated lyrics to create a full song
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate an upbeat pop song, female vocal, 122 BPM, with the following lyrics:\n\n[Verse 1]\n(paste generated lyrics here)\n\n[Chorus]\n(paste generated chorus here)"}],
    "stream": false
  }'
```

## Common Pitfalls

- **No genre or style direction** produces generic lyrics. Specify the genre and reference artists for tone.
- **Forgetting structure markers** makes it unclear where verses and choruses begin and end.
- **Too abstract** can produce lyrics that sound poetic but are not singable. Ask for "singable lyrics" if needed.
- **No syllable awareness** may produce lines that do not fit a melody. Mention "keep lines 8-10 syllables" for consistency.
- **Missing emotional arc** makes songs feel flat. Specify how the emotion should build across sections.

## Related Skills

- [Song Generation](../song-generation/SKILL.md) — Turn lyrics into full produced songs with vocals
- [Music Generation](../music-generation/SKILL.md) — Create instrumental backing tracks for your lyrics
- [Voice Generation](../voice-generation/SKILL.md) — Generate spoken-word delivery of lyrics
- [Text to Speech](../text-to-speech/SKILL.md) — Hear lyrics read aloud before singing

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
