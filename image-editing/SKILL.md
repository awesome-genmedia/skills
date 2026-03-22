---
name: image-editing
description: "Edit existing images with natural language using each::sense AI. Modify colors, add or remove objects, change styles, inpaint regions, outpaint to extend canvas, retouch photos, and apply creative effects. Supports up to 4 reference images. Use for: photo retouching, object removal, style transfer, inpainting, outpainting, color correction, creative edits. Triggers: edit image, modify image, change image, image editing, photo edit, retouch, inpaint, outpaint, remove object, add object, style transfer, color grade image"
allowed-tools: Bash(curl *), WebFetch
---

# Image Editing

Edit existing images with natural language instructions using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Change the sky to a dramatic orange and purple sunset. Keep the foreground untouched."}],
    "image_urls": ["https://example.com/landscape-photo.jpg"],
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
    messages=[{"role": "user", "content": "Change the sky to a dramatic orange and purple sunset. Keep the foreground untouched."}],
    extra_body={
        "image_urls": ["https://example.com/landscape-photo.jpg"]
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
    "messages": [{"role": "user", "content": "Apply the color grading and mood from the reference image to the target photo"}],
    "image_urls": ["https://example.com/target-photo.jpg", "https://example.com/style-reference.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Available Models

| Model | Capability | Best For |
|-------|-----------|----------|
| **flux-2-edit** | Natural language image editing | General edits, style changes, object modification |
| **flux-fill-pro** | Inpainting and outpainting | Filling masked areas, extending canvas |
| **eachlabs-bg-remover-v1** | Background removal | Subject isolation, transparent backgrounds |
| **topaz-upscale-image** | Resolution enhancement | Upscaling after edits, detail recovery |
| **kling-face-swap** | Face replacement | Swapping faces between images |

> each::sense automatically selects the right editing model based on your instruction. Describe what you want changed in plain English.

## Editing Capabilities

| Category | What You Can Do | Example Instruction |
|----------|----------------|---------------------|
| **Object Removal** | Remove unwanted elements | "Remove the person standing in the background" |
| **Object Addition** | Add new elements | "Add a golden retriever sitting next to the bench" |
| **Style Transfer** | Change artistic style | "Convert this photo to a Studio Ghibli illustration" |
| **Color Grading** | Adjust colors and mood | "Apply a warm, vintage film look with orange tones" |
| **Inpainting** | Fill or replace regions | "Replace the old car with a modern Tesla" |
| **Outpainting** | Extend the canvas | "Extend this image to the left to show more of the beach" |
| **Retouching** | Clean up imperfections | "Smooth skin blemishes and brighten the eyes" |
| **Season Change** | Alter time/season | "Change the scene from summer to a snowy winter" |
| **Lighting** | Modify lighting conditions | "Change the lighting to golden hour with long shadows" |

## Prompt Tips

### Be Specific About What to Keep

Always mention what should remain unchanged to prevent unintended modifications:

```
"Change the wall color to teal blue. Keep the furniture, people, and floor exactly as they are."
```

### Reference Specific Areas

Use spatial language to target specific regions:

```
"In the top-right corner, add a flock of birds flying in V-formation"
"Replace the object on the left side of the table with a vase of sunflowers"
```

### Chain Edits with Conversation

Use multi-turn messages to apply sequential edits:

```json
{
  "messages": [
    {"role": "user", "content": "Remove the car from the driveway"},
    {"role": "assistant", "content": "..."},
    {"role": "user", "content": "Now change the house color to light blue"}
  ],
  "image_urls": ["https://example.com/house.jpg"]
}
```

## Examples

### Object Removal

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Remove the power lines and utility poles from this landscape photo. Fill in the sky naturally so it looks like they were never there."}],
    "image_urls": ["https://example.com/landscape-with-powerlines.jpg"],
    "stream": false
  }'
```

### Style Transfer

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Transform this city street photo into a Van Gogh Starry Night style painting. Keep the composition and building shapes, but apply swirling brushstrokes and vibrant blues and yellows."}],
    "image_urls": ["https://example.com/city-street.jpg"],
    "stream": false
  }'
```

### Inpainting (Object Replacement)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Replace the wooden dining table with a sleek modern glass table. Keep the chairs, plates, and everything else on the table exactly the same."}],
    "image_urls": ["https://example.com/dining-room.jpg"],
    "stream": false
  }'
```

### Outpainting (Canvas Extension)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Extend this portrait photo into a full 16:9 landscape by expanding the background on both sides. Continue the indoor environment naturally with consistent lighting and style."}],
    "image_urls": ["https://example.com/portrait-crop.jpg"],
    "stream": false
  }'
```

### Color and Mood Change

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Convert this daytime photo to a moody nighttime scene. Add soft neon reflections on wet pavement, streetlight glow, and a slight blue color grade. Keep all buildings and structures intact."}],
    "image_urls": ["https://example.com/daytime-street.jpg"],
    "stream": false
  }'
```

## Batch Editing Workflow

```bash
# Apply the same edit across multiple product photos
IMAGES=(
  "https://example.com/product-1.jpg"
  "https://example.com/product-2.jpg"
  "https://example.com/product-3.jpg"
)

for IMG in "${IMAGES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Remove the background and replace with a clean white studio backdrop. Add a soft drop shadow beneath the product.\"}],
      \"image_urls\": [\"$IMG\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Too vague**: "Make it better" gives unpredictable results. Say exactly what to change.
- **Forgetting to anchor**: Always mention what should stay the same to avoid unwanted edits.
- **Conflicting instructions**: "Remove the car and make the car red" contradicts itself.
- **Expecting pixel-perfect masks**: Describe regions with natural language; the model interprets areas contextually.
- **Over-editing in one pass**: Complex multi-step edits work better as sequential conversation turns.

## Related Skills

- [Image Generation](../image-generation/SKILL.md) — Generate new images from scratch
- [Background Removal](../background-removal/SKILL.md) — Dedicated background removal
- [Face Swap](../face-swap/SKILL.md) — Swap faces between photos
- [Image Upscaling](../image-upscaling/SKILL.md) — Enhance resolution after editing

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
