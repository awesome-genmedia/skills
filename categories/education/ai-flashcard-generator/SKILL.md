---
name: ai-flashcard-generator
description: "Generate visual flashcards for learning using each::sense AI. Create illustrated study cards for vocabulary, science concepts, history, anatomy, geography, and more. Produce engaging visual mnemonics and pictorial study aids. Use for: flashcards, study cards, visual learning, vocabulary cards, memory aids, educational cards, revision materials. Triggers: flashcard, study card, vocabulary card, learning card, flash card, visual flashcard, study aid, revision card, memory card, quiz card"
allowed-tools: Bash(curl *), WebFetch
---

# AI Flashcard Generator

Generate visually engaging flashcards and study aids for learning using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a visual flashcard illustration for learning the Spanish word casa (house): a charming colorful cottage with a red tile roof, flower boxes in the windows, a small garden path, warm inviting illustration style, simple and memorable, clean white border like a card"
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
        "content": "Create a visual flashcard illustration for learning the Spanish word casa (house): a charming colorful cottage with a red tile roof, flower boxes in the windows, a small garden path, warm inviting illustration style, simple and memorable, clean white border like a card"
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Flashcard Generation

- **Keep visuals simple and iconic** — flashcards work best with clear, uncluttered illustrations.
- **Use bold, distinct colors** — high contrast makes cards more memorable.
- **One concept per card** — avoid cramming multiple ideas into a single image.
- **Specify card-like framing** — mention "card format," "white border," or "centered illustration."
- **Add labels separately** — generate the illustration, then overlay text in a design or flashcard app.
- **Batch generate** — loop through a vocabulary list to create a complete study deck.

## Examples

### Anatomy Flashcard

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A medical flashcard illustration of the human heart: a clean anatomical diagram showing four chambers, major arteries and veins in red and blue, labeled sections, educational medical illustration style, white background, clear and detailed"
      }
    ],
    "stream": false
  }'
```

### Geography Flashcard

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A flashcard illustration of Mount Fuji for a geography study set: the iconic symmetrical volcanic cone with snow cap reflected in Lake Kawaguchi, cherry blossoms in the foreground, clean illustrative style, vibrant but simple, card format with white border"
      }
    ],
    "stream": false
  }'
```

### Chemistry Flashcard

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A flashcard illustration for a chemistry study set showing the water molecule H2O: a 3D ball-and-stick model with a large red oxygen atom bonded to two smaller white hydrogen atoms at 104.5 degree angle, clean scientific illustration, soft gradient background, educational"
      }
    ],
    "stream": false
  }'
```

### Batch Vocabulary Deck

```bash
# Generate a set of vocabulary flashcard illustrations
WORDS=(
  "A flashcard illustration of a lighthouse on a rocky cliff at sunset, dramatic waves crashing below, nautical illustration style, card format"
  "A flashcard illustration of a violin with a bow resting across it on a velvet surface, warm light, musical instrument study card, clean illustration"
  "A flashcard illustration of a telescope pointed at a starry night sky, observatory dome in background, astronomy study card, educational illustration"
)

for WORD in "${WORDS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$WORD\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Workflow: Building a Flashcard Deck

1. **Define the subject** — vocabulary, anatomy, history, geography, etc.
2. **List key concepts** — One concept per card.
3. **Generate illustrations** — Create a visual for each concept using consistent style prompts.
4. **Export visuals** — Download the generated images.
5. **Add text labels** — Overlay terms, definitions, and hints in a flashcard app (Anki, Quizlet, etc.).
6. **Review and refine** — Ensure each card is clear and memorable.

## Related Skills

- [AI Diagram Generator](../ai-diagram-generator/SKILL.md) — Diagrams and flowcharts for study
- [AI Illustration](../ai-illustration/SKILL.md) — Detailed custom illustrations
- [AI Educational Video](../ai-educational-video/SKILL.md) — Animated learning content
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Detailed, accurate illustrations
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Clean illustrative styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Rapid batch generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
