---
name: ai-car-configurator
description: "Visualize car customizations using each::sense AI. Generate photorealistic renders of vehicles with custom paint colors, wheel styles, body kits, interior trims, and aftermarket modifications. Preview automotive builds before purchasing. Use for: car configuration, vehicle customization, auto visualization, custom paint preview, wheel fitment, body kit preview. Triggers: car configurator, vehicle customization, car color, wheel style, body kit, car customize, auto config, car build, vehicle preview, custom car"
allowed-tools: Bash(curl *), WebFetch
---

# AI Car Configurator

Visualize car customizations and configurations with photorealistic renders using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A photorealistic render of a sports sedan in deep metallic midnight blue, fitted with 20-inch matte black forged wheels, carbon fiber front splitter and rear diffuser, lowered suspension, tinted windows, parked in an underground concrete garage with moody directional lighting, automotive photography style"
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
        "content": "A photorealistic render of a sports sedan in deep metallic midnight blue, fitted with 20-inch matte black forged wheels, carbon fiber front splitter and rear diffuser, lowered suspension, tinted windows, parked in an underground concrete garage with moody directional lighting, automotive photography style"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Take this car and visualize it with a custom paint job: change the color to matte army green, add bronze-colored rally wheels, install a roof rack with LED light bar, lift the suspension slightly for an off-road look, keep the same car model and angle"
      }
    ],
    "image_urls": ["https://example.com/my-car.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Car Configuration

- **Specify the vehicle type clearly** — "sports coupe," "luxury SUV," "classic muscle car," "electric hatchback."
- **Describe modifications in detail** — exact wheel size, material finishes, body kit components.
- **Include paint finish type** — "metallic," "matte," "satin," "pearlescent," "gloss," or "chrome."
- **Set the scene** — showroom, street, track, mountain road, or studio background.
- **Mention camera angle** — "three-quarter front view," "rear perspective," "profile side shot," or "low angle."

## Examples

### Custom Paint and Wheels

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A photorealistic render of a classic 1960s muscle car in candy apple red with white racing stripes, chrome bumpers and trim, polished 17-inch Torq Thrust style wheels, wide rear tires, parked on a desert highway at sunset, low angle three-quarter front view, cinematic automotive photography"
      }
    ],
    "stream": false
  }'
```

### Interior Configuration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A photorealistic interior render of a luxury sedan cockpit: quilted tan leather seats with contrast stitching, carbon fiber dashboard trim, brushed aluminum accents, digital instrument cluster, ambient lighting in cool blue, steering wheel with paddle shifters, shot from the driver door looking across the cabin, showroom lighting"
      }
    ],
    "stream": false
  }'
```

### Electric Vehicle Concept

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A futuristic electric SUV in pearlescent white, aerodynamic body with flush door handles and panoramic glass roof, illuminated front light bar, 22-inch turbine-style aero wheels, charging at a sleek modern charging station, nighttime city street with reflections on wet pavement, concept car photography"
      }
    ],
    "stream": false
  }'
```

## Workflow: Vehicle Configuration Preview

1. **Choose the base vehicle** — Specify make, model, or vehicle type.
2. **Configure exterior** — Paint color, wheels, body kit, and trim.
3. **Configure interior** — Upholstery, trim materials, and technology features.
4. **Generate hero shots** — Create the primary presentation views.
5. **Show in context** — Place the configured vehicle in lifestyle scenarios.
6. **Compare variants** — Generate side-by-side configurations for decision making.

## Related Skills

- [AI Vehicle Wrap](../ai-vehicle-wrap/SKILL.md) — Custom wrap and livery designs
- [AI Auto Ad](../ai-auto-ad/SKILL.md) — Automotive advertisement imagery
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation
- [Image to Video Pipeline](../../workflows/image-to-video-pipeline/SKILL.md) — Animate car reveals

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Photorealistic vehicle renders
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative automotive concepts
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick configuration previews

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
