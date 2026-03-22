---
name: ai-game-asset
description: "Generate game art assets using each::sense AI. Create sprites, icons, items, weapons, props, tilesets, and UI elements for 2D and 3D games. Supports pixel art, hand-painted, stylized, and photorealistic styles across all game genres. Use for: indie game development, game jams, prototyping, asset libraries, mobile games, RPG items. Triggers: game asset, game art, game icon, game item, weapon art, game prop, tileset, game sprite, game graphics, item icon"
allowed-tools: Bash(curl *), WebFetch
---

# AI Game Asset

Generate game art assets, sprites, icons, and props using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a set of fantasy RPG item icons: a glowing blue health potion in a glass vial, a golden shield with a lion emblem, a flaming sword with a ruby pommel, and a leather satchel with enchanted runes. Each icon on a transparent background, hand-painted style, 64x64 pixel grid layout, game-ready"
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
        "content": "Generate a set of fantasy RPG item icons: a glowing blue health potion in a glass vial, a golden shield with a lion emblem, a flaming sword with a ruby pommel, and a leather satchel with enchanted runes. Each icon on a transparent background, hand-painted style, 64x64 pixel grid layout, game-ready"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Match the art style of your existing assets:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create new game item icons matching the art style of these reference icons. Generate: a frost staff, a poison dagger, a healing amulet, and a scroll of teleportation. Same visual style, color palette, and icon size as the reference."
      }
    ],
    "image_urls": ["https://example.com/existing-game-icons.png"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Asset Categories

| Category | Examples | Common Styles |
|----------|----------|---------------|
| **Item Icons** | potions, weapons, armor, food, gems | hand-painted, flat, pixel art |
| **Props** | barrels, crates, torches, signs, treasure chests | stylized 3D, painted, isometric |
| **Tilesets** | grass, stone, water, lava, dungeon floor | pixel art, painted, seamless |
| **Weapons** | swords, bows, staves, guns, hammers | concept art, icon, sprite |
| **Collectibles** | coins, stars, hearts, keys, orbs | vector, pixel, cartoon |
| **Obstacles** | spikes, walls, pits, barriers, traps | side-view, top-down, isometric |

## Prompt Engineering Tips

### Prompt Structure

```
"Generate [asset type] for a [game genre] game:" + [specific items] + [art style] + [background] + [size/layout] + "game-ready"
```

### Art Style Keywords

```
pixel art 16-bit, pixel art 32-bit, hand-painted digital,
cel-shaded, flat vector, isometric, low-poly 3D render,
anime style, comic book style, photorealistic PBR,
retro 8-bit, watercolor game art
```

### Background Keywords

```
transparent background, solid black background,
dark gradient background, clean white background,
game UI slot background
```

## Examples

### Pixel Art Tileset

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a pixel art tileset for a 2D platformer forest level: grass tiles, dirt tiles, stone path, tree trunk, leafy canopy, bush, flower, mushroom, wooden bridge plank, and water surface. 16x16 pixel tiles arranged in a sprite sheet grid. Earthy green and brown palette, retro 16-bit style, seamless edges."
      }
    ],
    "stream": false
  }'
```

### Sci-Fi Weapon Set

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a sci-fi weapon icon set for a space shooter game: plasma rifle with blue energy glow, laser pistol with red beam indicator, EMP grenade with electric arcs, rocket launcher with orange exhaust, and an energy shield generator. Side-view perspective, clean dark background, glowing neon accents, digital illustration style, game UI ready."
      }
    ],
    "stream": false
  }'
```

### Isometric Props

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate isometric game props for a medieval town: a wooden market stall with hanging meats, a stone well with bucket, a hay cart, a blacksmith anvil with hammer, a street lamp with flame, and a wooden barrel stack. Isometric 45-degree perspective, warm hand-painted style, transparent background, game-ready assets."
      }
    ],
    "stream": false
  }'
```

### Mobile Game Collectibles

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate collectible icons for a casual mobile puzzle game: a sparkling diamond, a ruby gem, an emerald gem, a sapphire gem, a gold coin, and a silver coin. Bright glossy cartoon style with soft highlights and shadows, each on a transparent background, round icon format suitable for match-3 game grid."
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Item Rarity Tiers

```bash
ITEM="a longsword"
TIERS=(
  "common: plain iron with leather grip, dull grey metal, no effects"
  "uncommon: steel with blue gem in the crossguard, slight magical shimmer"
  "rare: enchanted silver with glowing purple runes along the blade"
  "epic: crystalline blade radiating golden light, ornate golden hilt"
  "legendary: ethereal flame sword, blazing with white-hot fire, divine radiance"
)

for TIER in "${TIERS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Generate a game icon of $ITEM — $TIER. Hand-painted fantasy RPG style, dark gradient background, centered composition, game-ready icon.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Inconsistent style across assets** — describe the art style identically in every prompt or provide a reference image.
- **Transparent background requests** may not always yield true transparency (AI generates images, not PNGs with alpha). Plan for post-processing.
- **Too many items in one image** — more than 6-8 items per sheet leads to reduced quality per item.
- **Ignoring game perspective** — specify "side view", "top-down", "isometric", or "front-facing" to match your game camera.

## Related Skills

- [AI Character Design](../ai-character-design/SKILL.md) — Game character concepts
- [AI Game Environment](../ai-game-environment/SKILL.md) — Level backgrounds
- [AI Sprite Generator](../ai-sprite-generator/SKILL.md) — 2D sprite sheets
- [AI Game UI](../ai-game-ui/SKILL.md) — HUD and menu elements

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
