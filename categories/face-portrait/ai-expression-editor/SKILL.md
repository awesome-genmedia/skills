---
name: ai-expression-editor
description: "Change facial expressions in photos using each::sense AI. Transform neutral faces into smiles, add surprise, sadness, anger, laughter, winks, and more while maintaining the person's identity and photo quality. Use for: fixing awkward photos, social media content, creative projects, marketing materials, character design, meme creation. Triggers: change expression, facial expression, make smile, add smile, change face, expression editor, face expression, smiling face, surprised face, happy face, sad face, wink, laugh, expression change"
allowed-tools: Bash(curl *), WebFetch
---

# AI Expression Editor

Change facial expressions in photos naturally using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Change the expression in this photo to a warm, natural smile with slightly squinted eyes. Keep everything else exactly the same — same lighting, background, hair, and clothing."
      }
    ],
    "image_urls": ["https://example.com/neutral-portrait.jpg"],
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
        "content": "Change the expression in this photo to a warm, natural smile with slightly squinted eyes. Keep everything else exactly the same — same lighting, background, hair, and clothing."
    }],
    extra_body={
        "image_urls": ["https://example.com/neutral-portrait.jpg"]
    }
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Make this person look surprised with raised eyebrows and open mouth. Keep the rest of the photo unchanged."}],
    "image_urls": ["https://example.com/photo.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Expression Reference

| Expression | Key Facial Changes | Muscle Groups Involved |
|---|---|---|
| **Happy/Smile** | Upturned mouth corners, crow's feet, raised cheeks | Zygomatic major, orbicularis oculi |
| **Surprise** | Raised eyebrows, wide eyes, open mouth | Frontalis, levator palpebrae |
| **Sadness** | Downturned mouth, furrowed inner brows, droopy eyes | Depressor anguli oris, corrugator |
| **Anger** | Lowered brows, tense jaw, narrowed eyes | Corrugator, masseter |
| **Disgust** | Wrinkled nose, raised upper lip, squinted eyes | Levator labii, nasalis |
| **Fear** | Wide eyes, raised brows, tense mouth | Frontalis, platysma |
| **Contempt** | One-sided smirk, raised chin | Unilateral zygomatic |
| **Wink** | One eye closed, slight smile | Orbicularis oculi (unilateral) |

## Prompt Engineering Tips

### Be Precise About the Expression

Describe the expression in physical terms, not just the emotion name:

```
Change the expression to [emotion]: [specific facial changes]. Keep [everything to preserve].
```

### Intensity Levels

Control how strong the expression is:

- **Subtle**: "a slight smile," "barely noticeable frown"
- **Moderate**: "a clear smile," "visibly surprised"
- **Exaggerated**: "a wide beaming grin," "jaw-dropped shock"

### Preservation is Key

Always explicitly state what should not change:

```
Keep the same person identity, lighting, background, clothing, hair, and photo quality.
Only change the facial expression.
```

## Examples

### Neutral to Laughing

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Change this person from their neutral expression to genuinely laughing. Open mouth showing teeth, crinkled eyes, raised cheeks, natural laugh lines. The laugh should look authentic, not posed. Keep everything else in the photo identical."
      }
    ],
    "image_urls": ["https://example.com/serious-face.jpg"],
    "stream": false
  }'
```

### Add Professional Smile to Headshot

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Add a professional, confident closed-mouth smile to this corporate headshot. Slight upturning of the mouth corners, engaged eyes, approachable but not overly casual. Maintain the professional lighting and background exactly as-is."
      }
    ],
    "image_urls": ["https://example.com/corporate-headshot.jpg"],
    "stream": false
  }'
```

### Surprised Expression

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Change this person expression to genuine surprise. Eyebrows raised high, eyes wide open, mouth in a small O shape, like they just received unexpected good news. Natural and believable, not cartoonish. Keep everything else the same."
      }
    ],
    "image_urls": ["https://example.com/casual-portrait.jpg"],
    "stream": false
  }'
```

### Thoughtful/Pensive Look

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Change this smiling portrait to a thoughtful, contemplative expression. Slight furrowing of the brows, eyes looking slightly upward, closed relaxed mouth, as if deep in thought. Intellectual and introspective feel. Keep the same photo quality and setting."
      }
    ],
    "image_urls": ["https://example.com/smiling-portrait.jpg"],
    "stream": false
  }'
```

## Workflow: Expression Series for Marketing

```bash
# Step 1: Generate a happy version
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Change this portrait to show a bright, genuine smile with teeth showing and happy eyes. Keep everything else identical."
      }
    ],
    "image_urls": ["https://example.com/model-neutral.jpg"],
    "stream": false
  }'

# Step 2: Generate a surprised version
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Change this portrait to a surprised, excited expression. Wide eyes, raised brows, open mouth, like discovering something amazing. Keep everything else identical."
      }
    ],
    "image_urls": ["https://example.com/model-neutral.jpg"],
    "stream": false
  }'

# Step 3: Generate a determined/confident version
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Change this portrait to a confident, determined expression. Firm jaw, direct gaze, slight squint, subtle closed-mouth smile conveying strength. Keep everything else identical."
      }
    ],
    "image_urls": ["https://example.com/model-neutral.jpg"],
    "stream": false
  }'
```

## Related Skills

- [AI Beauty Filter](../ai-beauty-filter/SKILL.md) — Enhance the photo after expression change
- [AI Face Swap](../ai-face-swap/SKILL.md) — Swap faces between photos
- [AI Caricature](../ai-caricature/SKILL.md) — Exaggerated cartoon expressions
- [AI Aging Filter](../ai-aging-filter/SKILL.md) — Age progression effects
- [AI Makeup Try-On](../ai-makeup-try-on/SKILL.md) — Virtual makeup application

## Related Models

- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Context-aware image editing
- [live-portrait](../../../models/live-portrait/SKILL.md) — Facial animation from images
- [pulid-flux](../../../models/pulid-flux/SKILL.md) — Identity-preserving generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
