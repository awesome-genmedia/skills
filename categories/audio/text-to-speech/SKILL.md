---
name: text-to-speech
description: "Convert text to natural-sounding speech using each::sense AI. Generate high-quality voiceovers with multiple voices, accents, languages, and emotional tones. Supports long-form narration, short clips, and real-time streaming. Use for: audiobooks, accessibility, video narration, language learning, app voice interfaces, automated announcements. Triggers: text to speech, tts, ai voice, speech synthesis, read aloud, voice generator, narration, text reader, convert text to audio, spoken word, voice output, ai narrator"
allowed-tools: Bash(curl *), WebFetch
---

# Text to Speech

Convert written text into natural, human-sounding speech using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Convert to speech with a warm female voice: Welcome to the Sunrise Meditation podcast. Today we will explore breathing techniques that help you start your morning with clarity and calm."
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
        "content": "Convert to speech with a warm female voice: Welcome to the Sunrise Meditation podcast. Today we will explore breathing techniques that help you start your morning with clarity and calm."
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Voice Characteristics

| Characteristic | Options | Example Prompt Phrase |
|---|---|---|
| **Gender** | Male, female, neutral | "deep male voice" |
| **Tone** | Warm, authoritative, cheerful, calm, dramatic | "cheerful and upbeat tone" |
| **Pace** | Slow, moderate, fast | "slow and deliberate pace" |
| **Accent** | American, British, Australian, and many more | "British English accent" |
| **Language** | English, Spanish, French, German, Japanese, etc. | "in French" |

## Prompt Engineering Tips

### Specify Voice Details

Be explicit about the voice you want. Include gender, tone, pace, and accent in your prompt for best results.

```
Convert to speech with a [gender] [accent] voice, [tone] tone, [pace] pace: [your text]
```

### Punctuation Matters

- Use commas for natural pauses
- Use periods for full stops
- Use ellipses (...) for dramatic pauses
- Use exclamation marks for emphasis

### Long-Form Content

For long text, break it into paragraphs. The AI handles multi-paragraph content but shorter segments give you more control over pacing and tone.

## Examples

### Audiobook Narration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate speech with a deep, calm male narrator voice, slow pace, British accent: The old lighthouse keeper climbed the spiral staircase for the last time. Forty years of storms, shipwrecks, and solitary nights had carved deep lines into his face. Tonight, the automated system would take over, and the light would shine without him."
      }
    ],
    "stream": false
  }'
```

### Product Announcement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert to speech with an energetic, confident female voice, American accent: Introducing the all-new Galaxy Fit Pro! Track your workouts, monitor your sleep, and stay connected — all from your wrist. Available now for just ninety-nine dollars."
      }
    ],
    "stream": false
  }'
```

### Language Learning

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate speech in Spanish with a clear, slow female voice for a beginner language lesson: Buenos días. Me llamo María. Hoy vamos a aprender los números del uno al diez. Repitan después de mí."
      }
    ],
    "stream": false
  }'
```

### Accessibility Voice

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert to clear, friendly speech at moderate pace: You have three new notifications. First, a message from Sarah about tomorrow meeting. Second, a reminder to pick up groceries. Third, your flight to Denver is confirmed for Friday at 8 AM."
      }
    ],
    "stream": false
  }'
```

## Workflow

```bash
# Step 1: Generate a test clip with your preferred voice
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert to speech with a warm, professional female voice: This is a voice test for our upcoming video series."
      }
    ],
    "stream": false
  }'

# Step 2: Once satisfied, generate the full narration
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert to speech with a warm, professional female voice: In this episode, we explore three proven strategies for building a morning routine that sticks. Strategy one: start the night before. Strategy two: anchor your habits. Strategy three: track your progress."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [AI Voiceover](../ai-voiceover/SKILL.md) — Professional voiceover for videos and ads
- [AI Podcast Intro](../ai-podcast-intro/SKILL.md) — Generate podcast intros and outros
- [AI Music Generator](../ai-music-generator/SKILL.md) — Background music for your narration
- [AI Sound Effects](../ai-sound-effects/SKILL.md) — Sound effects to layer with speech

## Related Models

- [minimax-tts-v2](../../../models/minimax-tts-v2/SKILL.md) — High-quality multilingual TTS
- [kokoro-tts](../../../models/kokoro-tts/SKILL.md) — Expressive speech synthesis
- [dia-tts](../../../models/dia-tts/SKILL.md) — Conversational dialogue generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
