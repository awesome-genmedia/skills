---
name: ai-makeup-try-on
description: "Apply virtual makeup to face photos using each::sense AI. Try on lipstick, eyeshadow, foundation, blush, eyeliner, mascara, contouring, and complete looks without any physical products. Supports natural, glam, editorial, and avant-garde styles. Use for: beauty e-commerce, social media content, makeup experimentation, bridal look planning, beauty tutorials, product visualization. Triggers: makeup try on, virtual makeup, apply makeup, lipstick, eyeshadow, beauty look, makeup filter, glam look, bridal makeup, makeup test, cosmetics try on, makeup simulation, beauty try on"
allowed-tools: Bash(curl *), WebFetch
---

# AI Makeup Try-On

Apply virtual makeup to face photos with realistic results using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Apply a natural everyday makeup look to this photo. Light foundation evening out skin tone, subtle peach blush on the cheeks, brown eyeshadow with soft blending, thin black eyeliner, natural brown mascara, and a nude pink lipstick. Keep it realistic and wearable."
      }
    ],
    "image_urls": ["https://example.com/bare-face.jpg"],
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
        "content": "Apply a natural everyday makeup look to this photo. Light foundation evening out skin tone, subtle peach blush on the cheeks, brown eyeshadow with soft blending, thin black eyeliner, natural brown mascara, and a nude pink lipstick. Keep it realistic and wearable."
    }],
    extra_body={
        "image_urls": ["https://example.com/bare-face.jpg"]
    }
)

print(response.choices[0].message.content)
```

### With Reference Image

You can use a second image as a makeup style reference:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Apply the makeup style from the second image onto the face in the first image. Match the lipstick color, eyeshadow, and overall look."}],
    "image_urls": ["https://example.com/my-face.jpg", "https://example.com/makeup-reference.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Makeup Categories

| Category | Products | Key Descriptors |
|---|---|---|
| **Base** | Foundation, concealer, primer | Matte, dewy, natural, full coverage |
| **Cheeks** | Blush, bronzer, highlighter, contour | Peach, rose, coral, golden, sculpted |
| **Eyes** | Eyeshadow, eyeliner, mascara, brow | Smoky, cut crease, winged, natural |
| **Lips** | Lipstick, gloss, liner | Red, nude, berry, matte, glossy |
| **Special** | Glitter, gems, metallic, dramatic lashes | Editorial, festival, avant-garde |

## Makeup Styles

| Style | Description | When to Use |
|---|---|---|
| **No-Makeup Makeup** | Barely visible enhancement, skin-first | Daily wear, office |
| **Natural/Everyday** | Visible but subtle, enhances features | Casual outings, photos |
| **Glam** | Full face, bold lips or eyes, polished | Events, date night |
| **Bridal** | Elegant, lasting, camera-ready | Weddings, formal events |
| **Editorial** | Creative, artistic, unconventional | Fashion, photography |
| **Smoky Eye** | Dark, blended eye focus, paired with nude lip | Evening events, drama |
| **Bold Lip** | Statement lip color, minimal eyes | Classic, impactful |
| **Festival** | Glitter, color, face gems, playful | Music festivals, parties |

## Prompt Engineering Tips

### Be Specific About Each Area

Describe makeup for each facial area separately for best results:

```
Apply makeup to this photo:
- Base: [foundation type and coverage]
- Eyes: [eyeshadow colors, liner style, lash look]
- Cheeks: [blush color and placement, contour]
- Lips: [color, finish, style]
```

### Color Precision

Use specific color names rather than generic ones:

```
Good: "dusty rose lipstick," "champagne gold eyeshadow," "terracotta blush"
Vague: "pink lipstick," "light eyeshadow," "some blush"
```

### Finish Types

Specify the finish for a more accurate result:

```
Matte, satin, glossy, dewy, shimmer, metallic, glitter, velvet
```

## Examples

### Glamorous Evening Look

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply a glamorous evening makeup look to this portrait. Full coverage matte foundation, sculpted contour on the cheekbones, warm bronze and gold smoky eyeshadow blended into the crease, dramatic winged black eyeliner, full false lash effect, rose gold highlighter on cheekbones, and a classic matte red lipstick. Polished and camera-ready."
      }
    ],
    "image_urls": ["https://example.com/bare-portrait.jpg"],
    "stream": false
  }'
```

### Bridal Makeup

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply elegant bridal makeup to this face. Flawless dewy foundation, soft peach blush, champagne shimmer eyeshadow with subtle brown in the crease, thin brown eyeliner with individual lashes, groomed natural brows, and a soft mauve pink satin lipstick. Timeless, romantic, and photograph-ready."
      }
    ],
    "image_urls": ["https://example.com/bride-bare.jpg"],
    "stream": false
  }'
```

### Bold Editorial Look

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply an editorial avant-garde makeup look. Flawless porcelain base, no blush, graphic cobalt blue eyeliner extending past the outer eye in a geometric wing shape, no mascara for a clean modern look, bleached and brushed-up brows, and a deep plum matte lip. High-fashion editorial style."
      }
    ],
    "image_urls": ["https://example.com/model-clean.jpg"],
    "stream": false
  }'
```

### Quick Lip Color Try-On

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply only a lipstick to this face photo. Deep berry-wine matte lipstick with a precise, clean lip line. Do not change anything else about the face, just add the lipstick."
      }
    ],
    "image_urls": ["https://example.com/face-closeup.jpg"],
    "stream": false
  }'
```

## Workflow: Compare Multiple Looks

```bash
# Step 1: Natural everyday look
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply natural everyday makeup: light tinted moisturizer, subtle peach blush, beige matte eyeshadow, brown mascara, tinted lip balm in rose. Keep it minimal and fresh."
      }
    ],
    "image_urls": ["https://example.com/my-face.jpg"],
    "stream": false
  }'

# Step 2: Smoky eye evening look
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply a smoky eye look: medium coverage foundation, subtle contour, dark charcoal and black smoky eyeshadow blended outward, smudged black eyeliner on upper and lower lash line, volumizing mascara, nude lip with gloss. Dramatic but elegant."
      }
    ],
    "image_urls": ["https://example.com/my-face.jpg"],
    "stream": false
  }'

# Step 3: Bold lip minimal eye look
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply a bold lip look: even skin base, light pink blush, minimal eye makeup with just mascara and clean brows, and a vibrant true red matte lipstick as the focal point. Classic and striking."
      }
    ],
    "image_urls": ["https://example.com/my-face.jpg"],
    "stream": false
  }'
```

## Input Photo Tips

- Use a clear, front-facing photo with even lighting
- Bare-faced or minimal makeup gives the best canvas
- High resolution allows more detailed makeup application
- Avoid heavy shadows across the face

## Related Skills

- [AI Beauty Filter](../ai-beauty-filter/SKILL.md) — Skin and feature enhancement
- [AI Face Restoration](../ai-face-restoration/SKILL.md) — Fix photo quality before applying makeup
- [AI Expression Editor](../ai-expression-editor/SKILL.md) — Adjust expression for the perfect shot
- [AI Caricature](../ai-caricature/SKILL.md) — Stylized cartoon portraits
- [AI Face Swap](../ai-face-swap/SKILL.md) — Swap faces between photos

## Related Models

- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Context-aware image editing
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — High-quality image generation
- [pulid-flux](../../../models/pulid-flux/SKILL.md) — Identity-preserving generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
