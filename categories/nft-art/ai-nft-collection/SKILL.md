---
name: ai-nft-collection
description: "Generate NFT collection artwork using each::sense AI. Create profile picture (PFP) collections, generative trait-based characters, 1-of-1 art pieces, and themed collection series with consistent styles. Use for: NFT collections, PFP projects, digital collectibles, generative art series, trait-based characters. Triggers: NFT collection, PFP, profile picture NFT, digital collectible, NFT art, generative collection, NFT series, collectible art, NFT character, trait-based NFT"
allowed-tools: Bash(curl *), WebFetch
---

# AI NFT Collection Generator

Generate NFT collection artwork and digital collectibles using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate an NFT profile picture of a cyberpunk ape wearing neon-rimmed sunglasses and a leather jacket, circuit board patterns on the skin, glowing teal eyes, dark urban background with holographic signs, PFP style, square format, vibrant digital art"
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
        "content": "Generate an NFT profile picture of a cyberpunk ape wearing neon-rimmed sunglasses and a leather jacket, circuit board patterns on the skin, glowing teal eyes, dark urban background with holographic signs, PFP style, square format, vibrant digital art"
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
        "content": "Create a new NFT character in the same art style as this reference: maintain the line weight, color palette, and shading approach, but create a completely new character with different traits — a fox with steampunk goggles and a top hat, same square PFP format"
      }
    ],
    "image_urls": ["https://example.com/collection-reference.png"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for NFT Collection Art

- **Define a consistent base style** — reuse exact style descriptions across all prompts for collection cohesion.
- **Vary traits systematically** — change accessories, colors, backgrounds, and expressions while keeping the base character.
- **Use square format cues** — NFT PFPs are typically 1:1 aspect ratio.
- **Describe rarity tiers** — "common," "rare," and "legendary" with increasing visual complexity.
- **Maintain a trait matrix** — list all possible traits (headwear, eyewear, background, clothing) and combine them.

## Examples

### PFP Character Variant

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "NFT PFP of a cartoon robot head with a friendly expression, antenna with a small star on top, pastel pink metallic body, wearing a tiny crown, soft gradient lavender background, clean vector art style, square format, collectible character design"
      }
    ],
    "stream": false
  }'
```

### 1-of-1 Art Piece

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A 1-of-1 NFT art piece: a surreal floating island with an ancient temple at the peak, waterfalls cascading into clouds below, bioluminescent plants glowing in twilight, a massive crescent moon behind, epic fantasy digital painting, highly detailed, rich colors, cinematic composition"
      }
    ],
    "stream": false
  }'
```

### Batch Collection Generation

```bash
# Generate trait variations for an NFT collection
TRAITS=(
  "NFT PFP of a samurai cat with a red headband, golden armor, cherry blossom background, anime style, square format"
  "NFT PFP of a samurai cat with an eye patch, silver armor, bamboo forest background, anime style, square format"
  "NFT PFP of a samurai cat with a straw hat, bronze armor, sunset mountain background, anime style, square format"
  "NFT PFP of a samurai cat with demon horns, obsidian armor, lightning storm background, anime style, square format, legendary rarity"
)

for TRAIT in "${TRAITS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$TRAIT\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Workflow: NFT Collection Pipeline

1. **Design the character concept** — Define the base character and art style.
2. **Create a trait matrix** — List all possible combinations of accessories, colors, and backgrounds.
3. **Generate base variants** — Produce the core character in different trait combinations.
4. **Create rarity tiers** — Generate common, rare, and legendary variants with increasing detail.
5. **Review for consistency** — Ensure all pieces feel like part of the same collection.
6. **Prepare metadata** — Pair each image with trait metadata for smart contracts.

## Related Skills

- [AI Pixel Art](../ai-pixel-art/SKILL.md) — Pixel art for NFTs and games
- [AI Generative Art](../ai-generative-art/SKILL.md) — Algorithmic art pieces
- [AI Abstract Art](../ai-abstract-art/SKILL.md) — Abstract digital artwork
- [Text to Image](../../image/text-to-image/SKILL.md) — General-purpose image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Premium quality character art
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative stylistic variety
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Rapid trait iteration

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
