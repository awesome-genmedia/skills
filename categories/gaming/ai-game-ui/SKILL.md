---
name: ai-game-ui
description: "Generate game UI elements using each::sense AI. Create HUD designs, menu screens, health bars, inventory panels, dialog boxes, loading screens, and button sets for mobile, PC, and console games. Supports fantasy, sci-fi, cartoon, minimalist, and skeuomorphic styles. Use for: game interface design, HUD mockups, menu design, UI kit creation, game UX prototyping, mobile game UI. Triggers: game ui, game hud, game menu, health bar, inventory ui, game interface, game buttons, dialog box, game screen, loading screen"
allowed-tools: Bash(curl *), WebFetch
---

# AI Game UI

Generate game UI elements, HUD designs, and menu screens using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Design a fantasy RPG game HUD overlay: health bar in red with an ornate gold frame in the top-left, mana bar in blue below it, a circular minimap in the top-right with a stone border, a row of 6 skill slots along the bottom center with gem-encrusted frames, and a gold coin counter. Dark transparent overlay style, 16:9 aspect ratio, game UI design."
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
        "content": "Design a fantasy RPG game HUD overlay: health bar in red with an ornate gold frame in the top-left, mana bar in blue below it, a circular minimap in the top-right with a stone border, a row of 6 skill slots along the bottom center with gem-encrusted frames, and a gold coin counter. Dark transparent overlay style, 16:9 aspect ratio, game UI design."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Match the UI style of an existing game:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Design a game settings menu screen matching the UI style of this reference. Include: volume slider, graphics quality dropdown, control remapping section, and save/cancel buttons. Same visual theme, border style, and color palette as the reference."},
              {"type": "image_url", "image_url": {"url": "https://example.com/existing-game-ui.png"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## UI Element Categories

| Category | Elements | Placement |
|----------|----------|-----------|
| **HUD** | health bar, mana bar, stamina, ammo, minimap, score | screen edges |
| **Menus** | main menu, pause menu, settings, level select | full screen or centered panel |
| **Inventory** | item grid, equipment slots, character stats | panel overlay |
| **Dialog** | speech bubbles, dialog boxes, choice buttons | lower third |
| **Notifications** | popups, achievements, loot drops, damage numbers | floating/temporary |
| **Buttons** | play, pause, settings cog, arrows, close | contextual |
| **Loading** | progress bar, spinner, tips screen | full screen |

## UI Style Reference

| Style | Characteristics | Genre Match |
|-------|----------------|-------------|
| **Ornate Fantasy** | gold borders, stone textures, runes, scrollwork | RPG, MMORPG |
| **Sci-Fi Holographic** | blue glow, thin lines, hexagons, translucent panels | space, cyberpunk |
| **Clean Minimalist** | flat colors, thin borders, sans-serif text areas | indie, puzzle |
| **Cartoon / Casual** | rounded corners, bright colors, thick outlines, bouncy | mobile, casual |
| **Military Tactical** | dark green, angular, radar-style elements, stencil | FPS, strategy |
| **Pixel / Retro** | pixel-art borders, 8-bit icons, chunky elements | retro, roguelike |

## Examples

### Sci-Fi Shooter HUD

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a sci-fi FPS game HUD: holographic transparent elements, a circular crosshair in the center, health and shield bars in the bottom-left as thin horizontal neon lines (green for health, blue for shield), ammo counter in the bottom-right showing 24/120 in a digital font, a radar minimap in the top-right corner with a hex-grid pattern, and a subtle compass bar along the top edge. Cyan and white color scheme on transparent dark background, 16:9, futuristic military UI."
      }
    ],
    "stream": false
  }'
```

### Mobile Game Main Menu

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a main menu screen for a casual mobile puzzle game. Bright cheerful background with soft clouds and a rainbow. Large round Play button in green at the center, smaller round buttons for Settings (gear icon), Leaderboard (trophy), and Shop (cart) arranged below in a row. Game title area at the top. Cartoon style with thick outlines, glossy button effects, 9:16 portrait mobile format."
      }
    ],
    "stream": false
  }'
```

### RPG Inventory Panel

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design an RPG inventory screen UI: a central character silhouette with 6 equipment slots around it (head, chest, legs, weapon, shield, ring), a 5x4 grid of inventory bag slots on the right side, character stats panel on the left showing STR, DEX, INT, VIT with numerical values, and a gold/weight counter at the bottom. Medieval parchment and dark wood theme with iron rivets, warm candlelit ambiance, 16:9 game UI design."
      }
    ],
    "stream": false
  }'
```

### Dialog System

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a game dialog box UI for a visual novel: a semi-transparent dark panel spanning the bottom third of the screen, a character name tag in an accent-colored tab on the upper-left of the panel, placeholder text lines for dialog, a small character portrait frame on the left edge, and a flashing triangle indicator in the bottom-right to advance text. Three choice buttons stacked on the right side. Clean anime-style UI with soft rounded corners, pastel accent colors, 16:9 format."
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Complete UI Kit

```bash
STYLE="fantasy RPG, ornate gold and stone borders, parchment texture, warm tones, game UI design"

ELEMENTS=(
  "Main menu screen: title area, Play button, Options button, Credits button, dark castle background"
  "HUD overlay: health bar top-left, mana bar below health, minimap top-right, 6 action slots bottom center, 16:9"
  "Inventory panel: 6x5 item grid, equipment slots, character stats, gold counter, close button"
  "Dialog box: bottom panel with character portrait frame, name tag, text area, choice buttons"
  "Pause menu: centered panel with Resume, Settings, Save, Quit buttons, blurred background overlay"
  "Loading screen: full screen with ornate progress bar at bottom, tip text area, background illustration frame"
)

for ELEMENT in "${ELEMENTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Design a game $ELEMENT. $STYLE\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Text rendering** is unreliable in AI images. UI text will appear garbled. Use the generated image as a visual layout reference and add real text programmatically.
- **Aspect ratio mismatch** — specify 16:9 for PC/console, 9:16 for mobile portrait, or 4:3 for tablets.
- **Too many elements** in one image become cluttered and small. Focus on one screen or panel at a time.
- **Ignoring readability** — high-contrast elements on semi-transparent backgrounds work best. Specify contrast.
- **Inconsistent style** across screens — use the same style description for every UI element in the kit.

## Related Skills

- [AI Game Asset](../ai-game-asset/SKILL.md) — Icons for inventory and abilities
- [AI Character Design](../ai-character-design/SKILL.md) — Character portraits for UI
- [AI Game Environment](../ai-game-environment/SKILL.md) — Background art for menus
- [AI Sprite Generator](../ai-sprite-generator/SKILL.md) — Animated UI elements

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
