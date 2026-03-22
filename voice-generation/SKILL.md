---
name: voice-generation
description: "Generate human-like voice audio from text using each::sense AI. Create natural-sounding speech with control over voice character, emotion, pacing, and language. Supports 32 languages, multiple voice styles, and expressive delivery. Use for: voiceovers, narration, audiobooks, character voices, announcements, podcasts, accessibility. Triggers: generate voice, ai voice, voice generation, text to voice, voiceover, narration, ai narrator, voice clone, voice synthesis, speech generation, voice actor, tts"
allowed-tools: Bash(curl *), WebFetch
---

# Voice Generation

Generate human-like voice audio from text with expressive control using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a warm, professional male voice narrating: Welcome to the future of AI. In this episode, we explore how generative media is transforming creative industries around the world."}],
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
    messages=[{"role": "user", "content": "Generate a warm, professional male voice narrating: Welcome to the future of AI. In this episode, we explore how generative media is transforming creative industries around the world."}]
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a voice narration describing what is happening in this image. Use a friendly, conversational female voice as if narrating a travel documentary."}],
    "image_urls": ["https://example.com/travel-scene.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Available Models

| Model | Strengths | Best For |
|-------|-----------|----------|
| **elevenlabs-tts** | Ultra-realistic voices, 32 languages, emotional range | Narration, voiceovers, audiobooks, multilingual content |

> each::sense selects the optimal voice model and configuration based on your prompt description.

## Voice Characteristics

### Voice Types

| Type | Description | Best For |
|------|-------------|----------|
| **Warm Male** | Deep, friendly, trustworthy | Documentaries, podcasts, brand narration |
| **Bright Female** | Clear, energetic, approachable | Tutorials, ads, explainer videos |
| **Authoritative** | Commanding, confident, measured | News, corporate presentations, trailers |
| **Conversational** | Natural, casual, relatable | Vlogs, social media, casual content |
| **Dramatic** | Intense, emotional, theatrical | Audiobooks, storytelling, trailers |
| **Soft / Whispery** | Gentle, intimate, calming | ASMR, meditation, bedtime stories |
| **Elderly** | Wise, seasoned, warm | Storytelling, character voices |
| **Young** | Fresh, enthusiastic, light | Youth content, gaming, upbeat ads |

### Supported Languages

elevenlabs-tts supports 32 languages including:

| Language | | Language | | Language |
|----------|---|----------|---|----------|
| English | | Spanish | | French |
| German | | Italian | | Portuguese |
| Japanese | | Korean | | Chinese (Mandarin) |
| Hindi | | Arabic | | Dutch |
| Polish | | Russian | | Swedish |
| Turkish | | Indonesian | | Filipino |

> Specify the target language in your prompt: "Generate in Spanish: ..."

## Prompt Tips

### Voice Description Formula

```
Generate a [voice type] [gender] voice [speaking style]:
[The text to speak]
```

### Controlling Pace and Emotion

Add delivery instructions before the text:

```
"Speak slowly and calmly with pauses between sentences: ..."
"Deliver with excitement and rising energy: ..."
"Read in a serious, measured tone with gravitas: ..."
```

### Adding Pauses and Emphasis

Use natural punctuation to control delivery:

```
"The results were... unexpected. (pause) Very unexpected."
"This is NOT a drill. I repeat — this is NOT a drill."
```

### SSML-like Control

Describe the delivery style in natural language:

```
"Whisper the first line, then gradually increase volume
and intensity through the paragraph, ending with a powerful
declaration."
```

## Examples

### Documentary Narration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a deep, authoritative male voice with a BBC documentary style. Measured pacing with dramatic pauses. Narrate: Deep beneath the Antarctic ice, a world unknown to science has waited in silence for millions of years. Now, for the first time, a team of researchers is about to descend into the abyss."}],
    "stream": false
  }'
```

### Podcast Introduction

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a friendly, energetic female voice for a podcast intro. Conversational and warm with a slight smile in the voice. Say: Hey everyone, welcome back to Creative Sparks! I am your host, and today we have an incredible guest who is about to blow your mind. Grab your coffee, settle in, and let us dive right in."}],
    "stream": false
  }'
```

### Audiobook Excerpt

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a dramatic male voice reading a thriller novel excerpt. Tense and gripping, with varied pacing — slow during suspense, faster during action. Read: The hallway was dark. Too dark. Marcus pressed his back against the cold wall, his breath coming in short, controlled bursts. Footsteps. Getting closer. He had maybe ten seconds before they turned the corner. His hand found the door handle. Locked. The footsteps stopped."}],
    "stream": false
  }'
```

### Multilingual Voice

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a natural-sounding female voice speaking in Japanese. Polite and professional tone, suitable for a corporate product introduction. Say: こんにちは。本日は弊社の最新製品についてご紹介させていただきます。この革新的なソリューションが、お客様のビジネスをどのように変革できるかをご覧ください。"}],
    "stream": false
  }'
```

### Character Voice (Children Content)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a cheerful, animated female voice for a children storytelling app. Expressive and playful with varied intonation, like a kindergarten teacher reading a storybook. Say: Once upon a time, in a tiny little house at the edge of the Whispering Woods, there lived a very curious bunny named Patches. Patches had the floppiest ears you have ever seen, and a nose that was always — always — twitching."}],
    "stream": false
  }'
```

## Batch Voice Generation

```bash
# Generate the same text in multiple languages
TEXTS=(
  "Generate in English with a professional male voice: Welcome to our service. We are glad to have you."
  "Generate in Spanish with a professional male voice: Bienvenido a nuestro servicio. Nos alegra tenerle."
  "Generate in French with a professional male voice: Bienvenue dans notre service. Nous sommes ravis de vous accueillir."
)

for TEXT in "${TEXTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$TEXT\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **No voice description** produces a default neutral voice. Always describe the voice character.
- **Walls of text** without punctuation produce rushed, monotone output. Use natural punctuation.
- **Conflicting emotions** (e.g., "happy and sad") confuse the delivery. Pick one dominant emotion.
- **Missing language specification** for non-English text may produce incorrect pronunciation.
- **Very long texts** should be broken into paragraphs for better pacing and natural breathing.

## Related Skills

- [Text to Speech](../text-to-speech/SKILL.md) — Focused text-to-speech conversion
- [Song Generation](../song-generation/SKILL.md) — Generate singing voices in songs
- [Sound Effects](../sound-effects/SKILL.md) — Layer ambient sounds with narration
- [Music Generation](../music-generation/SKILL.md) — Create background music for voiceovers

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
