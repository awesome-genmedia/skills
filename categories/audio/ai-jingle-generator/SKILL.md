---
name: ai-jingle-generator
description: "Generate short catchy jingles and tunes using each::sense AI. Create brand jingles, ad music, notification sounds, hold music, and sonic logos. Memorable melodies for marketing, apps, and media. Use for: brand audio identity, advertising jingles, notification tones, app startup sounds, hold music, sonic branding. Triggers: jingle, sonic logo, brand tune, ad jingle, catchy tune, notification melody, short music, brand sound, audio logo, hold music, ringtone, startup sound, brand jingle"
allowed-tools: Bash(curl *), WebFetch
---

# AI Jingle Generator

Generate short, catchy jingles and brand tunes using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a 5-second brand jingle for a food delivery app. Bright, cheerful ukulele melody with a xylophone accent, upbeat and memorable, makes you think of fast friendly service."
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
        "content": "Generate a 5-second brand jingle for a food delivery app. Bright, cheerful ukulele melody with a xylophone accent, upbeat and memorable, makes you think of fast friendly service."
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Jingle Types

| Type | Duration | Description | Use Case |
|---|---|---|---|
| **Sonic Logo** | 1-3 sec | Ultra-short brand identifier | App launch, end of ads |
| **Ad Jingle** | 5-15 sec | Catchy melody for commercials | TV/radio/online ads |
| **Notification Tone** | 0.5-2 sec | Alert or notification sound | Mobile apps, software |
| **Hold Music Loop** | 15-30 sec | Pleasant loopable music | Phone systems |
| **Intro Stinger** | 3-5 sec | Opening hit for content | Videos, streams, shows |
| **Sung Jingle** | 10-20 sec | Melody with brand name lyrics | Radio, TV commercials |

## Prompt Engineering Tips

### Keep It Short and Specific

Jingles are about brevity. Specify the exact duration, the instruments, and the emotional response you want.

```
Generate a [duration]-second [type] for [brand/purpose]. [Instruments], [mood], [key characteristic].
```

### Memorable Melody Tips

- Simple melodies (3-5 notes) are most memorable
- Repetition creates recognition
- Rising melodies feel optimistic
- Falling melodies feel resolved and final
- Major keys sound happy; minor keys sound sophisticated

### Brand Personality Keywords

```
playful, luxurious, trustworthy, innovative, warm, bold,
clean, organic, energetic, sophisticated, friendly, powerful
```

## Examples

### Tech Startup Sonic Logo

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 2-second sonic logo for a tech company. Three ascending digital tones followed by a soft shimmer, clean and modern, like a startup sound. Think Intel but softer."
      }
    ],
    "stream": false
  }'
```

### Radio Ad Jingle with Vocals

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 10-second radio jingle for a pizza restaurant called Slice Heaven. Upbeat, fun, with a male voice singing: Slice Heaven, Slice Heaven, every bite is pure perfection! Catchy pop melody with hand claps and a groovy bass line."
      }
    ],
    "stream": false
  }'
```

### Luxury Brand Audio Signature

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 3-second luxury brand sonic logo. A single piano note blooming into a warm string chord, elegant and refined, with a subtle reverb tail. Evokes sophistication and exclusivity."
      }
    ],
    "stream": false
  }'
```

### Phone Hold Music

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate 20 seconds of pleasant hold music for a healthcare company phone line. Soft acoustic guitar with light piano, calm and reassuring, moderate tempo, loopable, no vocals. Should feel professional and not annoying."
      }
    ],
    "stream": false
  }'
```

## Workflow: Complete Brand Audio Kit

```bash
# Step 1: Create the primary sonic logo
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 3-second sonic logo for a fintech app called Vaulta. Four clean digital notes ascending in a major key, ending with a soft chime, modern and trustworthy."
      }
    ],
    "stream": false
  }'

# Step 2: Create a notification sound in the same style
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 1-second notification sound matching the Vaulta sonic logo style. Two quick ascending digital tones with the same chime timbre, clean and subtle, for payment confirmations."
      }
    ],
    "stream": false
  }'

# Step 3: Create an ad jingle extending the theme
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 10-second ad jingle for Vaulta fintech app. Extend the four-note sonic logo into a full melodic phrase, add light electronic percussion and a bass line, confident and modern, ends with the original sonic logo. No vocals."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [AI Music Generator](../ai-music-generator/SKILL.md) — Full-length music tracks
- [AI Sound Effects](../ai-sound-effects/SKILL.md) — Custom sound effects
- [AI Podcast Intro](../ai-podcast-intro/SKILL.md) — Podcast branding audio
- [Text to Speech](../text-to-speech/SKILL.md) — Voice narration for ads

## Related Models

- [ace-step](../../../models/ace-step/SKILL.md) — Song and music generation
- [stable-audio](../../../models/stable-audio/SKILL.md) — High-quality audio synthesis
- [mmaudio](../../../models/mmaudio/SKILL.md) — Multimodal audio generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
