---
name: ai-voiceover
description: "Generate professional voiceover audio using each::sense AI. Create narration for commercials, explainer videos, e-learning courses, documentaries, corporate training, and social media. Supports multiple voice styles, tones, pacing, and languages. Use for: video narration, ad voiceover, training material, product demos, documentary narration, social media reels. Triggers: voiceover, voice over, narration, ai narrator, video voice, commercial voice, explainer voice, professional narration, voice acting, recording, vo, voice talent"
allowed-tools: Bash(curl *), WebFetch
---

# AI Voiceover

Generate professional voiceover recordings for videos, ads, and presentations using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a professional voiceover with a confident, friendly male voice for a product explainer video: Meet TaskFlow, the project management tool that actually works. Drag, drop, done. No complicated setups, no learning curve. Just results."
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
        "content": "Generate a professional voiceover with a confident, friendly male voice for a product explainer video: Meet TaskFlow, the project management tool that actually works. Drag, drop, done. No complicated setups, no learning curve. Just results."
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Voiceover Styles by Use Case

| Use Case | Voice Style | Tone | Pace |
|---|---|---|---|
| **TV Commercial** | Bold, clear | Persuasive, excited | Medium-fast |
| **Explainer Video** | Friendly, conversational | Approachable, upbeat | Medium |
| **Documentary** | Deep, authoritative | Serious, reflective | Slow-medium |
| **E-learning** | Clear, patient | Encouraging, warm | Slow-medium |
| **Corporate Training** | Professional, neutral | Informative, steady | Medium |
| **Social Media** | Energetic, casual | Fun, relatable | Fast |
| **Meditation/Wellness** | Soft, soothing | Calm, gentle | Very slow |

## Prompt Engineering Tips

### Structure Your Prompt

Always specify the context, voice characteristics, and then the script:

```
Generate a voiceover for a [context]. [Voice description]: [script text]
```

### Pacing Control

- Short sentences create urgency and punch
- Longer sentences with commas create a flowing, relaxed feel
- Ellipses (...) insert dramatic pauses
- Dashes (--) create natural hesitation

### Script Formatting

Write the script as you want it spoken. Spell out numbers ("twenty-five" not "25"), abbreviations ("U S A" not "USA"), and use phonetic hints for unusual words.

## Examples

### Television Commercial

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a voiceover for a luxury car TV commercial. Deep, smooth male voice with authority and elegance: The all-new Meridian GT. Precision-engineered. Breathtakingly powerful. Every curve tells a story of relentless innovation. Meridian. Drive the future."
      }
    ],
    "stream": false
  }'
```

### E-learning Course

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a voiceover for an e-learning course module. Warm, patient female voice, clear enunciation, moderate pace: In this lesson, we will explore the fundamentals of financial planning. We will cover three key areas: budgeting, saving, and investing. By the end, you will have a clear roadmap for managing your personal finances."
      }
    ],
    "stream": false
  }'
```

### Social Media Reel

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate an energetic voiceover for a 15-second Instagram reel about a cooking hack. Young, excited female voice, fast pace: Okay wait, you need to try this. Freeze your leftover herbs in olive oil using an ice cube tray. Pop one out, toss it in the pan, instant flavor. Game changer!"
      }
    ],
    "stream": false
  }'
```

### Documentary Narration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a documentary voiceover. Deep, authoritative male voice, slow and reflective pace: For millions of years, the glacier carved its path through the valley... shaping the land, defining the rivers, and creating the fjords that would one day draw explorers from across the world."
      }
    ],
    "stream": false
  }'
```

## Workflow: Explainer Video Production

```bash
# Step 1: Generate the opening hook
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a voiceover for an app explainer video opening. Friendly, upbeat male voice: Ever feel like your to-do list is running your life? What if it could run itself?"
      }
    ],
    "stream": false
  }'

# Step 2: Generate the feature walkthrough
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a voiceover, same friendly upbeat male voice: With SmartList, your tasks organize themselves. Just tell it what you need to do, and it handles the when, the where, and the how. Drag to reprioritize. Swipe to complete. It is that simple."
      }
    ],
    "stream": false
  }'

# Step 3: Generate the closing CTA
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a voiceover closing for the SmartList explainer, same friendly male voice, slightly more energetic: Download SmartList today. Free on iOS and Android. Your future self will thank you."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Text to Speech](../text-to-speech/SKILL.md) — General-purpose text to speech
- [AI Podcast Intro](../ai-podcast-intro/SKILL.md) — Podcast branding audio
- [AI Music Generator](../ai-music-generator/SKILL.md) — Background music for your video
- [AI Sound Effects](../ai-sound-effects/SKILL.md) — Enhance your video with SFX

## Related Models

- [minimax-tts-v2](../../../models/minimax-tts-v2/SKILL.md) — High-quality multilingual TTS
- [kokoro-tts](../../../models/kokoro-tts/SKILL.md) — Expressive speech synthesis
- [dia-tts](../../../models/dia-tts/SKILL.md) — Conversational dialogue generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
