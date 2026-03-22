---
name: ai-podcast-intro
description: "Generate podcast intros, outros, and jingles using each::sense AI. Create professional audio branding with voice narration, background music, and sound effects tailored to your show. Supports various genres, moods, and formats. Use for: podcast branding, show intros, episode outros, segment transitions, audio bumpers. Triggers: podcast intro, podcast outro, podcast jingle, show intro, audio intro, podcast theme, podcast branding, intro music, outro music, podcast bumper, episode intro, show opener"
allowed-tools: Bash(curl *), WebFetch
---

# AI Podcast Intro

Generate professional podcast intros, outros, and transition jingles using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a podcast intro for a tech news show called The Daily Byte. Energetic electronic music bed, confident male voice saying: Welcome to The Daily Byte, your five-minute breakdown of the biggest stories in tech. 10 seconds total."
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
        "content": "Generate a podcast intro for a tech news show called The Daily Byte. Energetic electronic music bed, confident male voice saying: Welcome to The Daily Byte, your five-minute breakdown of the biggest stories in tech. 10 seconds total."
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Podcast Audio Types

| Type | Duration | Purpose |
|---|---|---|
| **Show Intro** | 10-20 sec | Opens every episode, establishes brand |
| **Show Outro** | 10-15 sec | Closes the episode, call to action |
| **Segment Bumper** | 3-5 sec | Transitions between segments |
| **Mid-roll Transition** | 2-3 sec | In/out of ad breaks |
| **Cold Open Stinger** | 1-2 sec | Quick hit before the intro |

## Prompt Engineering Tips

### Include All Elements

Describe the music style, voice characteristics, spoken text, and duration. The more complete your prompt, the better the result.

```
Generate a podcast [type] for [show name]. [Music description], [voice description] saying: [spoken text]. [Duration] total.
```

### Match Your Show's Tone

- **True crime**: Dark ambient pads, suspenseful, low male voice
- **Comedy**: Upbeat, playful, bright instruments, fun voice
- **Business**: Clean, professional, moderate tempo, authoritative voice
- **Wellness**: Calm, acoustic, warm female voice, gentle
- **Sports**: High energy, drums, bold, hype voice

## Examples

### True Crime Podcast Intro

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a dark, atmospheric podcast intro for a true crime show called Cold Trail. Low droning synth pads, subtle heartbeat rhythm, a tense female whisper voice saying: Some cases go cold. But the truth never dies. This is Cold Trail. 12 seconds total, builds tension gradually."
      }
    ],
    "stream": false
  }'
```

### Comedy Show Outro

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a podcast outro for a comedy show called Laugh Track. Upbeat funky bass line with light drums, cheerful male voice saying: Thanks for listening to Laugh Track! New episodes drop every Wednesday. Smash that subscribe button and leave us a review. Peace! 10 seconds, fun and energetic."
      }
    ],
    "stream": false
  }'
```

### Wellness Podcast Intro

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a gentle podcast intro for a mindfulness show called Breathe Easy. Soft acoustic guitar, ambient nature sounds, warm female voice saying: Welcome to Breathe Easy, a space for slowing down and reconnecting with yourself. 15 seconds, peaceful and calming."
      }
    ],
    "stream": false
  }'
```

### Segment Transition Bumper

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a short podcast segment transition bumper. Quick electronic swoosh with a two-note synth stab, modern and clean, no voice. 3 seconds total, suitable as a segment divider."
      }
    ],
    "stream": false
  }'
```

## Workflow: Complete Podcast Audio Branding

```bash
# Step 1: Generate the main show intro
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a podcast intro for a business strategy show called The Growth Lab. Clean modern electronic music, professional male voice saying: Welcome to The Growth Lab. Strategies, insights, and conversations that scale your business. 12 seconds."
      }
    ],
    "stream": false
  }'

# Step 2: Generate the matching outro
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a podcast outro matching the same clean electronic style as The Growth Lab intro. Same male voice saying: That is a wrap on this episode of The Growth Lab. Subscribe wherever you listen, and we will see you next week. Music fades out. 10 seconds."
      }
    ],
    "stream": false
  }'

# Step 3: Generate segment bumpers
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 3-second segment bumper in the same clean electronic style as The Growth Lab podcast. Quick musical stinger, no voice, just a short transition sound."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Text to Speech](../text-to-speech/SKILL.md) — Generate narration for your episodes
- [AI Music Generator](../ai-music-generator/SKILL.md) — Full background music tracks
- [AI Sound Effects](../ai-sound-effects/SKILL.md) — Sound effects for production
- [AI Jingle Generator](../ai-jingle-generator/SKILL.md) — Short brand tunes
- [AI Voiceover](../ai-voiceover/SKILL.md) — Professional voice recordings

## Related Models

- [ace-step](../../../models/ace-step/SKILL.md) — Full song and music generation
- [stable-audio](../../../models/stable-audio/SKILL.md) — High-quality audio generation
- [dia-tts](../../../models/dia-tts/SKILL.md) — Dialogue-style speech generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
