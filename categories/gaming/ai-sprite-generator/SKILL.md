---
name: ai-sprite-generator
description: "Generate 2D sprite sheets for game development using each::sense AI. Create animated character sprites, walk cycles, attack animations, idle loops, and effect sprites in pixel art or hand-drawn styles. Supports side-scrolling, top-down, and isometric perspectives. Use for: 2D game development, pixel art animation, character sprites, game prototyping, indie games, sprite sheet creation. Triggers: sprite generator, sprite sheet, pixel sprite, game sprite, walk cycle, animation sprite, 2d character sprite, pixel animation, sprite art, character animation"
allowed-tools: Bash(curl *), WebFetch
---

# AI Sprite Generator

Generate 2D sprite sheets and animated character sprites using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a pixel art sprite sheet showing a knight character walk cycle. 8 frames in a horizontal strip, side-view facing right, 32x32 pixels per frame. The knight wears silver armor with a blue cape and carries a sword. Classic 16-bit SNES style, transparent background, evenly spaced frames."
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
        "content": "Generate a pixel art sprite sheet showing a knight character walk cycle. 8 frames in a horizontal strip, side-view facing right, 32x32 pixels per frame. The knight wears silver armor with a blue cape and carries a sword. Classic 16-bit SNES style, transparent background, evenly spaced frames."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Match the style of existing sprites:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a new enemy sprite sheet matching the art style of this reference. Design a skeleton archer: idle pose, drawing bow, releasing arrow, and taking damage. 4 frames horizontal strip, same pixel size and palette as the reference."},
              {"type": "image_url", "image_url": {"url": "https://example.com/existing-sprites.png"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Sprite Sheet Types

| Type | Frames | Description |
|------|--------|-------------|
| **Walk Cycle** | 4-8 | character locomotion loop |
| **Run Cycle** | 6-8 | faster movement loop |
| **Idle** | 2-4 | breathing or subtle motion loop |
| **Attack** | 4-6 | swing, slash, or projectile |
| **Jump** | 3-5 | crouch, rise, apex, fall, land |
| **Death** | 4-6 | hit reaction and collapse |
| **Effect** | 4-8 | explosion, magic spell, smoke |
| **Direction Set** | 4-8 | same pose facing N, S, E, W |

## Prompt Engineering Tips

### Prompt Structure

```
"Generate a [art style] sprite sheet showing [character] [animation type]." + [frame count] + [layout] + [pixel size] + [visual details] + [background]
```

### Layout Specifications

```
horizontal strip — all frames in a single row
vertical strip — all frames in a single column
grid layout (4x4) — rows and columns for multiple animations
single sprite — one frame only (static asset)
```

### Pixel Art Resolution Keywords

```
8-bit NES style (8x8, 16x16 pixels)
16-bit SNES style (16x16, 32x32 pixels)
32-bit style (32x32, 64x64 pixels)
high-res pixel art (64x64, 128x128 pixels)
```

## Examples

### Top-Down RPG Character Directions

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a pixel art sprite sheet for a top-down RPG character. A young wizard in blue robes with a pointed hat and a wooden staff. Show walk cycle in 4 directions (down, left, right, up), 4 frames each, arranged in a 4x4 grid. 32x32 pixels per frame, 16-bit JRPG style, transparent background."
      }
    ],
    "stream": false
  }'
```

### Platformer Enemy

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a pixel art sprite sheet for a slime enemy in a 2D platformer. Green translucent slime blob with two simple dot eyes. Animations: idle (2 frames, gentle bounce), move (4 frames, squish and stretch hopping), and death (3 frames, splat into puddle). All frames in a single horizontal row, 32x32 per frame, cute retro style, transparent background."
      }
    ],
    "stream": false
  }'
```

### Hand-Drawn Character Sprites

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a hand-drawn 2D sprite sheet for a ninja character. Clean line art with flat color fills, side-view facing right. Show: idle (2 frames), run (6 frames), jump (3 frames), sword slash (4 frames). Each row is one animation, 128x128 pixels per frame. Black outfit, red scarf flowing. White background, clean outlines, indie game style."
      }
    ],
    "stream": false
  }'
```

### VFX Effect Sprites

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a sprite sheet for a fire explosion effect: 8 frames showing ignition to full blast to smoke dissipation. Horizontal strip, 64x64 pixels per frame, bright orange and yellow flames transitioning to grey smoke in later frames. Dark background, stylized hand-painted VFX, game-ready."
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Character Action Set

```bash
CHARACTER="a female samurai in red armor with a katana, pixel art 32x32, 16-bit style, side-view facing right, transparent background"

ANIMATIONS=(
  "idle animation: 4 frames, subtle breathing motion, sword at rest"
  "walk cycle: 6 frames, steady stride, sword at hip"
  "attack slash: 5 frames, wind-up and horizontal sword swing"
  "jump: 4 frames, crouch, rise, apex with sword raised, falling"
  "take damage: 3 frames, recoil backward, flash white"
  "death: 4 frames, stumble forward, fall to knees, collapse"
)

for ANIM in "${ANIMATIONS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Generate a pixel art sprite sheet: $CHARACTER. $ANIM. Frames in a horizontal strip.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Inconsistent character across frames** — the biggest challenge. Describe the character identically and reference earlier frames if using conversation history.
- **Frame count too high** — more than 8 frames in one image reduces per-frame quality. Keep it to 4-8.
- **Missing size specification** — always state pixel dimensions per frame.
- **No layout description** — without "horizontal strip" or "grid", frames may be randomly arranged.
- **Mixed perspectives** — do not mix side-view and top-down in one sheet. Be explicit about perspective.

## Related Skills

- [AI Game Asset](../ai-game-asset/SKILL.md) — Item and prop assets
- [AI Character Design](../ai-character-design/SKILL.md) — Character concept art
- [AI Game Environment](../ai-game-environment/SKILL.md) — Level backgrounds
- [AI Game UI](../ai-game-ui/SKILL.md) — Interface elements

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
