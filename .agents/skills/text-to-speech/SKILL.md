---
name: text-to-speech
description: "Convert text to natural-sounding speech using each::sense AI. Generate realistic voice audio from any text in 32 languages with control over voice, speed, emotion, and style. Powered by elevenlabs-tts for studio-quality output. Use for: narration, audiobooks, accessibility, announcements, IVR systems, e-learning, localization. Triggers: text to speech, tts, read aloud, convert to speech, speak text, voice output, ai speech, synthesize speech, read text, audio from text, narrate text"
allowed-tools: Bash(curl *), WebFetch
---

# Text to Speech

Convert any text to natural-sounding speech in 32 languages using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Convert this text to speech with a clear, professional female voice: Artificial intelligence is reshaping how we create, communicate, and connect. What was once science fiction is now everyday reality."}],
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
    messages=[{"role": "user", "content": "Convert this text to speech with a clear, professional female voice: Artificial intelligence is reshaping how we create, communicate, and connect. What was once science fiction is now everyday reality."}]
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
              {"type": "text", "text": "Describe this image aloud using text-to-speech. Use a warm, conversational voice as if explaining the scene to a friend."},
              {"type": "image_url", "image_url": {"url": "https://example.com/photo.jpg"}}
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
| **elevenlabs-tts** | Ultra-realistic voices, 32 languages, emotional control, multiple voice styles | All text-to-speech use cases |

## Supported Languages

elevenlabs-tts supports 32 languages with native-quality pronunciation:

| | | | |
|---|---|---|---|
| English | Spanish | French | German |
| Italian | Portuguese | Dutch | Polish |
| Russian | Swedish | Norwegian | Danish |
| Finnish | Turkish | Arabic | Hindi |
| Japanese | Korean | Chinese (Mandarin) | Chinese (Cantonese) |
| Indonesian | Filipino | Malay | Thai |
| Vietnamese | Romanian | Czech | Hungarian |
| Greek | Hebrew | Ukrainian | Bulgarian |

## Voice Styles

| Style | When to Use | Prompt Phrase |
|-------|-------------|--------------|
| **Professional** | Corporate, presentations, news | "professional, clear, measured tone" |
| **Conversational** | Podcasts, vlogs, casual content | "conversational, friendly, natural pace" |
| **Dramatic** | Audiobooks, trailers, storytelling | "dramatic, expressive, varied pacing" |
| **Calm** | Meditation, wellness, bedtime | "calm, soothing, slow and gentle" |
| **Energetic** | Ads, promos, sports | "energetic, upbeat, enthusiastic" |
| **Authoritative** | Documentaries, lectures, news | "authoritative, deep, commanding" |
| **Warm** | E-learning, tutorials, guides | "warm, patient, encouraging" |
| **Whisper** | ASMR, intimate content | "soft whisper, gentle, close-mic feel" |

## Prompt Tips

### Basic Text-to-Speech Formula

```
Convert to speech with a [voice style] [gender] voice: [Your text here]
```

### Controlling Speed

```
"Read slowly and deliberately: ..."
"Speak at a fast, excited pace: ..."
"Normal conversational speed: ..."
```

### Adding Emotion

```
"Read with genuine excitement and wonder: ..."
"Deliver with a somber, reflective tone: ..."
"Say this with playful sarcasm: ..."
```

### Pronunciation Hints

For unusual words, names, or acronyms:

```
"Pronounce 'GIF' with a hard G. Read: ..."
"Pronounce 'Nguyen' as 'Win'. Read: ..."
"Read 'API' as individual letters A-P-I, not as a word: ..."
```

### Pauses and Emphasis

Use natural punctuation and formatting:

```
"The answer is... (long pause) ...forty-two."
"This is CRITICAL. Do NOT skip this step."
"First — and this is important — check your settings."
```

## Examples

### E-Learning Narration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Convert to speech with a warm, patient female voice suitable for an e-learning course. Moderate pace with clear enunciation: In this module, you will learn the fundamentals of machine learning. We will start with supervised learning, where the model learns from labeled examples. Think of it like a teacher showing a student flash cards — each card has a question and an answer. Over time, the student learns to predict answers on their own."}],
    "stream": false
  }'
```

### Audiobook Chapter

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Convert to speech with a rich, deep male voice for an audiobook. Dramatic pacing with variation: Chapter One. The Last Signal. The radio crackled to life at three seventeen in the morning. Commander Hayes sat upright in her bunk, instantly awake. She had been waiting for this — dreading it, really — for six hundred and forty-two days. The signal was faint. Barely there. But it was unmistakably human."}],
    "stream": false
  }'
```

### Multilingual Announcement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Convert to speech in French with a professional female voice. Clear and elegant pronunciation: Mesdames et messieurs, bienvenue a bord du vol Air France sept-deux-quatre a destination de Paris Charles de Gaulle. La duree estimee du vol est de huit heures et trente minutes. Nous vous souhaitons un agreable voyage."}],
    "stream": false
  }'
```

### Product Commercial

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Convert to speech with an energetic, confident male voice for a product ad. Punchy delivery with building excitement: Introducing the all-new Galaxy Pro Max. Thinner. Faster. Smarter. With a battery that lasts two full days and a camera system that sees in the dark. This is not just a phone — this is your entire studio, office, and entertainment center, right in your pocket. Galaxy Pro Max. Available now."}],
    "stream": false
  }'
```

### Accessibility / Screen Reader

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Convert to speech with a clear, neutral voice at moderate speed. Optimized for accessibility and easy comprehension: Your order number four-seven-three-nine has been confirmed. Estimated delivery is Thursday, March twenty-sixth. You will receive a tracking link by email within two hours. If you need to make changes, please contact support before midnight tonight."}],
    "stream": false
  }'
```

## Batch Text-to-Speech

```bash
# Convert multiple text segments to speech
SEGMENTS=(
  "Welcome to our app. Let me show you around."
  "First, tap the plus button to create a new project."
  "Next, choose a template or start from scratch."
  "That is it! You are ready to create something amazing."
)

for TEXT in "${SEGMENTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Convert to speech with a friendly female voice: $TEXT\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **No voice description** produces a default voice. Always specify gender, style, and mood.
- **All caps text** may be read letter-by-letter. Use normal casing with emphasis described in the prompt.
- **Numbers and abbreviations** can be misread. Write out "twenty-five" instead of "25" for reliability.
- **Very long texts** without paragraph breaks sound monotone. Break into logical sections.
- **Missing language specification** for non-English text may produce incorrect pronunciation.
- **Special characters** and code snippets may produce unexpected audio. Describe technical content in natural language.

## Related Skills

- [Speech to Text](../speech-to-text/SKILL.md) — Reverse: transcribe audio back to text
- [Voice Generation](../voice-generation/SKILL.md) — Extended voice generation with character control
- [Song Generation](../song-generation/SKILL.md) — Generate singing voices, not just speech
- [Sound Effects](../sound-effects/SKILL.md) — Layer ambient sounds behind speech

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
