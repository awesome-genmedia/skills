---
name: ai-game-environment
description: "Generate game environment and level backgrounds using each::sense AI. Create landscapes, dungeons, cityscapes, interiors, and biomes for 2D and 3D games. Supports pixel art, painted, photorealistic, and stylized renders for any genre. Use for: level design concepts, background art, world building, game backdrops, parallax layers, environment concept art. Triggers: game environment, level background, game landscape, game world, dungeon art, game biome, level art, game backdrop, environment concept, game scenery"
allowed-tools: Bash(curl *), WebFetch
---

# AI Game Environment

Generate game environment art, level backgrounds, and world concepts using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a fantasy game environment: a vast underground cavern with bioluminescent mushrooms casting teal and violet light on crystal formations, an ancient stone bridge crossing a chasm, and a distant glowing portal. Painted concept art style, wide panoramic composition, rich atmospheric depth, game environment art"
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
        "content": "Generate a fantasy game environment: a vast underground cavern with bioluminescent mushrooms casting teal and violet light on crystal formations, an ancient stone bridge crossing a chasm, and a distant glowing portal. Painted concept art style, wide panoramic composition, rich atmospheric depth, game environment art"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide a mood board or rough sketch to guide the environment:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a game environment based on this mood reference. Match the color palette and atmosphere. A frozen lakeside village with wooden longhouses, ice-covered docks, and mountains in the distance. Painted concept art, wide composition."
      }
    ],
    "image_urls": ["https://example.com/mood-reference.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Environment Types

| Biome / Setting | Key Elements | Mood |
|----------------|--------------|------|
| **Enchanted Forest** | giant trees, glowing flora, fairy lights, moss | mystical, serene |
| **Volcanic Wasteland** | lava rivers, obsidian, ash clouds, cracked earth | hostile, dramatic |
| **Underwater City** | coral architecture, bioluminescence, kelp, bubbles | alien, tranquil |
| **Cyberpunk City** | neon, holograms, rain, skyscrapers, flying cars | gritty, electric |
| **Desert Ruins** | sandstone temples, dunes, oasis, buried statues | ancient, desolate |
| **Space Station** | metal corridors, viewports, stars, zero-gravity | isolated, futuristic |
| **Medieval Village** | thatched roofs, cobblestone, market, castle | warm, welcoming |
| **Frozen Tundra** | ice, aurora, snow drifts, frozen waterfalls | harsh, beautiful |

## Prompt Engineering Tips

### Prompt Structure

```
"Generate a [genre] game environment:" + [setting description] + [key landmarks] + [atmospheric details] + [lighting] + [art style] + [composition]
```

### Depth and Scale

Use layering language for depth:
```
foreground: [close objects, framing elements]
midground: [main subject, playable area]
background: [distant scenery, sky, atmosphere]
```

### Lighting Keywords

```
golden hour, blue hour, overcast diffused, harsh noon sun,
moonlit, torchlit, bioluminescent glow, neon-lit,
volumetric fog, god rays, rim lighting, campfire warmth
```

## Examples

### 2D Platformer — Parallax Layers

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 2D side-scrolling game background for a haunted graveyard level with parallax depth layers: foreground with crooked iron fence and dead tree silhouettes, midground with crumbling tombstones and a mausoleum, background with a full moon behind wispy clouds and a distant hilltop castle. Spooky purple and grey palette, hand-painted style, horizontal panoramic format."
      }
    ],
    "stream": false
  }'
```

### Top-Down RPG Overworld

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a top-down game map view of a fantasy kingdom: a winding river cutting through green farmland, a walled city in the center with a castle, dark forests to the north, mountains to the east, a coastal port town to the south, and swampland to the west. Hand-drawn illustrated map style, parchment-colored background, labeled regions, RPG world map aesthetic."
      }
    ],
    "stream": false
  }'
```

### Sci-Fi Interior Level

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a sci-fi game environment: the interior of a derelict space station. Flickering emergency red lights, broken pipes venting steam, floating debris in low gravity, a shattered observation window revealing stars and a nebula outside. Photorealistic rendering, first-person perspective looking down a long corridor, horror atmosphere, volumetric lighting."
      }
    ],
    "stream": false
  }'
```

### Pixel Art Dungeon

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a pixel art dungeon room for a roguelike game: a torchlit stone chamber with a treasure chest in the center, scattered bones on the floor, cracked pillars, a locked iron door on the far wall, and cobwebs in the corners. 32-bit pixel art, top-down three-quarter view, warm torchlight against cold stone blue, retro game aesthetic."
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: World Biomes

```bash
STYLE="painted concept art, wide panoramic, rich atmospheric depth, game environment"

BIOMES=(
  "Enchanted forest: towering ancient trees with glowing sap veins, carpet of luminous flowers, gentle fog, firefly particles, twilight sky"
  "Volcanic badlands: jagged obsidian formations, rivers of flowing lava, ash falling like snow, smoke plumes, angry red sky"
  "Crystal caves: enormous crystalline formations in amethyst and quartz, reflecting pools, prismatic light refractions, underground waterfalls"
  "Floating islands: chunks of earth suspended in the sky connected by rope bridges, waterfalls falling into the void, clouds drifting between islands, sunset"
)

for BIOME in "${BIOMES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Generate a fantasy game environment: $BIOME. $STYLE\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **No sense of scale** — include a reference object (a small figure, a bridge, a doorway) to communicate the environment's size.
- **Flat composition** — use foreground, midground, and background layers for visual depth.
- **Missing atmosphere** — fog, particles, light rays, and haze sell believability. Do not skip them.
- **Inconsistent perspective** — specify "side view", "top-down", "first-person", or "isometric" explicitly.
- **Over-detailed backgrounds** — for playable levels, the background should not overwhelm foreground gameplay elements.

## Related Skills

- [AI Game Asset](../ai-game-asset/SKILL.md) — Props and items for environments
- [AI Character Design](../ai-character-design/SKILL.md) — Characters to populate worlds
- [AI Sprite Generator](../ai-sprite-generator/SKILL.md) — 2D animated sprites
- [AI Game UI](../ai-game-ui/SKILL.md) — HUD overlays for levels

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
