---
name: ai-generative-art
description: "Generate algorithmic and generative art pieces using each::sense AI. Create mathematical art, fractal compositions, procedural patterns, data-driven visualizations, and code-inspired abstract works. Use for: generative art, algorithmic art, fractal art, mathematical visualization, procedural art, creative coding visuals. Triggers: generative art, algorithmic art, fractal, procedural art, mathematical art, code art, data art, parametric art, computational art, creative coding"
allowed-tools: Bash(curl *), WebFetch
---

# AI Generative Art Generator

Create algorithmic and generative art pieces using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a generative art piece: thousands of tiny colored particles flowing along invisible magnetic field lines, forming an organic spiral pattern, particles transition from deep crimson to bright gold along the flow path, dark background, mathematical beauty, high resolution digital art"
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
        "content": "Create a generative art piece: thousands of tiny colored particles flowing along invisible magnetic field lines, forming an organic spiral pattern, particles transition from deep crimson to bright gold along the flow path, dark background, mathematical beauty, high resolution digital art"
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Generative Art

- **Reference mathematical concepts** — "Fibonacci spiral," "Voronoi tessellation," "fractal branching," "Perlin noise."
- **Describe the algorithm metaphorically** — "particles following flow fields," "recursive subdivision," "cellular automaton."
- **Specify color mapping** — how colors change along gradients, by density, or by position.
- **Mention the scale** — "thousands of elements," "dense particle field," "sparse geometric network."
- **Include technical art references** — "Processing style," "creative coding," "generative design."

## Examples

### Fractal Composition

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A fractal art piece: a Mandelbrot-inspired deep zoom showing intricate spiraling patterns, electric blue and violet color palette with bright white hot spots at the deepest zoom levels, infinite complexity, mathematical beauty, ultra-detailed digital rendering"
      }
    ],
    "stream": false
  }'
```

### Flow Field Visualization

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A generative flow field artwork: hundreds of curved lines following Perlin noise patterns across the canvas, varying line thickness based on velocity, gradient from ocean blue at the edges to warm coral at the center, white canvas background, elegant and organic, creative coding aesthetic"
      }
    ],
    "stream": false
  }'
```

### Voronoi Pattern Art

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A Voronoi tessellation artwork: irregular polygonal cells covering the canvas, each cell filled with a unique color from a sunset palette of orange, pink, purple, and deep blue, thin white cell boundaries, some cells contain smaller nested Voronoi patterns creating depth, generative art style"
      }
    ],
    "stream": false
  }'
```

### Recursive Geometry

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A recursive geometric generative art piece: a large triangle subdivided into smaller triangles, each subdivision rotated slightly and filled with progressively warmer colors from cool teal at the outer edges to fiery orange at the center, Sierpinski triangle inspired, clean vector aesthetic, black background"
      }
    ],
    "stream": false
  }'
```

## Workflow: Generative Art Series

1. **Define the algorithm concept** — Flow fields, fractals, cellular automata, particle systems, or tessellations.
2. **Choose a color strategy** — Gradient mapping, random palette, data-driven, or position-based coloring.
3. **Generate the base piece** — Create the initial composition.
4. **Create variations** — Adjust parameters (density, color, scale) for series cohesion with individuality.
5. **Curate and mint** — Select the strongest pieces for publication or NFT minting.

## Related Skills

- [AI Abstract Art](../ai-abstract-art/SKILL.md) — Abstract digital artwork
- [AI NFT Collection](../ai-nft-collection/SKILL.md) — NFT collection generation
- [AI Pixel Art](../ai-pixel-art/SKILL.md) — Pixel-based art generation
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-resolution detailed art
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative artistic outputs
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast parameter exploration

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
