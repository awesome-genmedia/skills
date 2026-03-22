---
name: ai-character-design
description: "Generate game character concepts and design sheets using each::sense AI. Create heroes, villains, NPCs, creatures, and monsters with detailed concept art, turnaround sheets, expression sheets, and action poses. Supports fantasy, sci-fi, anime, cartoon, and realistic styles. Use for: game character art, concept art, character sheets, NPC design, creature design, boss design. Triggers: character design, game character, character concept, character sheet, npc design, creature design, boss design, hero design, villain design, character turnaround"
allowed-tools: Bash(curl *), WebFetch
---

# AI Character Design

Generate game character concepts, turnaround sheets, and design art using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Design a fantasy RPG rogue character: a lithe elven woman with short silver hair and violet eyes, wearing dark leather armor with buckles and straps, a hooded cloak, twin daggers at her belt, and soft boots. Character concept art, full body front view, neutral A-pose, detailed clothing design, digital painting, dark moody background"
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
        "content": "Design a fantasy RPG rogue character: a lithe elven woman with short silver hair and violet eyes, wearing dark leather armor with buckles and straps, a hooded cloak, twin daggers at her belt, and soft boots. Character concept art, full body front view, neutral A-pose, detailed clothing design, digital painting, dark moody background"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide existing art as style or design reference:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a new character in the same art style as this reference. Create a male warrior version: heavy plate armor, greataxe, battle scars, braided red beard. Same visual style, line weight, and color approach as the reference image. Full body concept art."
      }
    ],
    "image_urls": ["https://example.com/existing-character-style.png"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Character Design Types

| Type | Description | Use Case |
|------|-------------|----------|
| **Concept Art** | single detailed illustration | early design exploration |
| **Turnaround Sheet** | front, side, back views | 3D modeler reference |
| **Expression Sheet** | face with multiple emotions | animator reference |
| **Action Pose** | dynamic combat or ability pose | marketing, key art |
| **Silhouette Study** | black silhouette shapes | readability testing |
| **Color Variations** | same design, different palettes | skin/outfit unlocks |

## Prompt Engineering Tips

### Prompt Structure

```
"Design a [genre] [class/role] character:" + [physical description] + [clothing/armor] + [weapons/accessories] + [pose] + [art style] + [background]
```

### Physical Description Order

```
race/species → build → height → hair → face → distinguishing marks
```

### Armor and Clothing Detail

```
material (leather, plate, cloth, chainmail)
condition (pristine, battle-worn, patched, enchanted)
color scheme (dark earth tones, bright primary, monochrome)
accessories (belts, pouches, cloaks, jewelry, trophies)
```

### Art Style Keywords

```
concept art, character design sheet, digital painting,
cel-shaded, anime style, Pixar style, dark fantasy,
hand-painted, semi-realistic, stylized cartoon,
League of Legends style, Genshin Impact style
```

## Examples

### Sci-Fi Pilot Turnaround

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Character turnaround sheet for a sci-fi starship pilot: a young man with an undercut hairstyle and cybernetic left eye, wearing a fitted flight suit in dark grey with orange accent panels, utility harness with data pads, magnetic boots. Show front view, three-quarter view, side view, and back view in a single image. Clean light grey background, character concept art style, full body."
      }
    ],
    "stream": false
  }'
```

### Creature Design — Boss Monster

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a boss creature for a dark fantasy action game: a massive corrupted tree guardian, 30 feet tall, trunk-like body covered in cracked bark and glowing fungal veins, twisted branch arms ending in claw-like roots, a face formed from a hollow knot in the trunk with glowing amber eyes, moss and dead vines hanging from its limbs. Menacing idle pose, dark forest background, dramatic back-lighting, concept art, painterly digital style."
      }
    ],
    "stream": false
  }'
```

### Cartoon Mascot Character

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a cute mascot character for a mobile platformer: a small round fox with oversized ears and big sparkly eyes, wearing a tiny adventurer backpack and a leaf-shaped bandana. Short stubby legs, fluffy tail. Cheerful expression, jumping pose with one paw raised. Bright colorful cartoon style, thick outlines, clean vector look, white background."
      }
    ],
    "stream": false
  }'
```

### Expression Sheet

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a character expression sheet: a grizzled dwarven blacksmith with a thick braided brown beard, bushy eyebrows, and a burn scar on the left cheek. Show 6 head portraits in a grid: neutral, angry, laughing, suspicious, surprised, and sad. Consistent character design across all expressions. Hand-painted fantasy game art style, clean background."
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Party of Characters

```bash
STYLE="fantasy RPG digital painting, full body front view, detailed concept art, dark parchment background"

CHARACTERS=(
  "Human paladin: tall muscular man in gleaming silver plate armor, blue tabard with sun emblem, longsword and kite shield, close-cropped blond hair, stern expression"
  "Halfling bard: small cheerful woman with curly auburn hair, wearing a green vest and patchwork traveling clothes, carrying a lute, rosy cheeks, mischievous grin"
  "Tiefling warlock: tall figure with crimson skin, curved horns, glowing yellow eyes, black robes with arcane symbols, holding a tome in one hand and dark energy in the other"
  "Orc ranger: scarred female orc with green skin and one tusk, practical leather and fur armor, longbow across the back, war paint on cheeks, braided black hair"
)

for CHAR in "${CHARACTERS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Design a $CHAR. $STYLE\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Vague body types** — "strong warrior" is ambiguous. Specify build, height, and proportions.
- **Style inconsistency** — use identical style keywords across all characters for a cohesive cast.
- **Overcrowded turnaround sheets** — four views maximum per image. More than that reduces quality.
- **Hands and fingers** are still challenging for AI. For detailed hand poses, plan for touch-up.
- **Text on clothing/armor** will not render reliably. Describe symbols or patterns instead of words.

## Related Skills

- [AI Game Asset](../ai-game-asset/SKILL.md) — Items, weapons, and props
- [AI Sprite Generator](../ai-sprite-generator/SKILL.md) — Animated sprite sheets
- [AI Game Environment](../ai-game-environment/SKILL.md) — Level backgrounds
- [AI Game UI](../ai-game-ui/SKILL.md) — HUD and menu elements

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
