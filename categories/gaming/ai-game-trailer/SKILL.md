---
name: ai-game-trailer
description: "Create game promotional trailers using each::sense AI. Generate cinematic game trailer clips, teaser sequences, and gameplay-style footage for marketing, crowdfunding, and social media. Supports fantasy, sci-fi, horror, casual, and action game genres. Use for: game marketing, Steam trailer, crowdfunding video, social media teaser, game announcement, indie game promotion. Triggers: game trailer, game teaser, game promo video, game cinematic, game announcement video, game marketing video, indie game trailer, gameplay trailer, game reveal, promotional video"
allowed-tools: Bash(curl *), WebFetch
---

# AI Game Trailer

Create cinematic game promotional trailers and teaser clips using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a cinematic game trailer clip: a lone warrior in dark armor walks through a burning medieval village at night, embers floating upward, camera slowly tracking alongside them. The warrior draws a glowing runic sword as a massive dragon shadow passes overhead. Dark fantasy, cinematic widescreen, dramatic orchestral mood, 4K quality"
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
        "content": "Generate a cinematic game trailer clip: a lone warrior in dark armor walks through a burning medieval village at night, embers floating upward, camera slowly tracking alongside them. The warrior draws a glowing runic sword as a massive dragon shadow passes overhead. Dark fantasy, cinematic widescreen, dramatic orchestral mood, 4K quality"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide concept art or a game screenshot to generate a trailer from that visual:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Generate a cinematic game trailer clip based on this concept art. Bring the scene to life: add slow camera movement pushing forward, atmospheric particle effects, subtle character motion, and dramatic lighting. Cinematic widescreen format, game trailer quality."},
              {"type": "image_url", "image_url": {"url": "https://example.com/game-concept-art.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Trailer Shot Types

| Shot | Camera | Purpose |
|------|--------|---------|
| **Establishing** | slow aerial or wide static | set the world and tone |
| **Character Reveal** | low angle, push-in | introduce the protagonist |
| **Action** | tracking, handheld feel | show combat or gameplay |
| **Environmental Detail** | slow pan or dolly | highlight world-building |
| **Dramatic Moment** | close-up, slow motion | emotional beat or turning point |
| **Title Card** | static or subtle zoom | branding (add text in post) |
| **Stinger / Final Shot** | sudden cut or reveal | cliffhanger ending |

## Prompt Engineering Tips

### Prompt Structure

```
"Generate a cinematic game trailer clip:" + [scene description] + [character actions] + [camera movement] + [atmosphere and effects] + [genre and mood] + [quality keywords]
```

### Camera Movement Language

```
slow dolly push-in, lateral tracking, aerial descent,
orbit around character, whip pan, handheld shake,
crane up, low-angle looking up, over-the-shoulder
```

### Atmosphere and VFX Keywords

```
volumetric fog, lens flare, particle effects, rain,
floating embers, dust motes, god rays, motion blur,
depth of field, chromatic aberration, film grain
```

## Examples

### Sci-Fi Reveal Trailer

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a sci-fi game trailer clip: camera slowly descends through clouds to reveal a massive alien megastructure floating above a ruined Earth city. Tiny human ships approach it cautiously. Scale is enormous. Overcast sky, blue bioluminescent patterns on the alien structure, atmospheric haze, cinematic widescreen, Interstellar-level epic scale, 4K."
      }
    ],
    "stream": false
  }'
```

### Horror Game Teaser

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a horror game teaser clip: first-person POV walking down a dark hospital corridor, flickering fluorescent lights, peeling wallpaper, a wheelchair slowly rolling on its own in the distance. Camera creeps forward hesitantly. Something dark darts across the hallway at the far end. Found-footage grain, desaturated cold tones, survival horror atmosphere, unsettling mood."
      }
    ],
    "stream": false
  }'
```

### Indie Platformer Showcase

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate an indie platformer game trailer clip: a small fox character dashes through a vibrant hand-painted forest, jumping between platforms over a sparkling river, collecting glowing orbs. Side-scrolling view, camera tracking the character. Colorful watercolor art style, cheerful and whimsical atmosphere, smooth fluid animation, bright daylight, indie game aesthetic."
      }
    ],
    "stream": false
  }'
```

### Boss Fight Moment

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate an epic boss fight trailer clip: a small armored knight faces off against a towering stone golem in a crumbling colosseum. The golem raises its fist and slams down, creating a shockwave of debris. The knight rolls to the side and strikes the golem leg with a lightning-charged sword. Low-angle dramatic shot, slow motion impact, dust and sparks flying, dark fantasy action game, cinematic widescreen."
      }
    ],
    "stream": false
  }'
```

## Multi-Shot Trailer Workflow

```bash
GAME_STYLE="dark fantasy action RPG, cinematic widescreen, film grain, orchestral mood, 4K"

SHOTS=(
  "Shot 1 — Establishing: aerial camera slowly descends over a fog-covered cursed kingdom with twisted black towers, dead forests, and a blood-red moon"
  "Shot 2 — Character reveal: a cloaked figure stands at the edge of a cliff, wind blowing their cloak, camera pushes in from behind to reveal a scarred face and glowing eyes"
  "Shot 3 — Action montage: rapid sequence of sword clashes, dodge rolls, magic spells detonating, and enemies being launched, fast-paced cuts"
  "Shot 4 — Emotional beat: the character kneels before a fallen companion in a rainy battlefield, slow motion raindrops, close-up on clenched fist"
  "Shot 5 — Boss reveal: camera tilts up from ground level to show an enormous demon lord wreathed in black flame, towering over the hero, dramatic back-lighting"
  "Shot 6 — Final stinger: the hero charges forward with sword drawn, screen smashes to black just before impact"
)

for SHOT in "${SHOTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Generate a game trailer clip: $SHOT. $GAME_STYLE\"}],
      \"stream\": false
    }"
  echo "=== $SHOT ==="
done
```

## Post-Production Notes

AI-generated trailer clips are individual scenes. To create a full trailer:

1. **Generate individual clips** — one scene per API call
2. **Edit in video software** — sequence clips, add transitions, adjust pacing
3. **Add title cards and text** — game title, release date (AI text is unreliable)
4. **Layer audio** — music, sound effects, voice-over
5. **Color grade** — unify the look across all clips

## Common Pitfalls

- **Too much action in one clip** — each generation is a short clip. One focused action per scene works best.
- **Text and logos** will not render reliably. Add titles in post-production.
- **Character consistency** — the same character may look different across clips. Describe them identically each time.
- **Audio** is not generated. Plan for separate music and sound design.
- **Pacing** — AI generates at a constant tempo. Fast-paced montages need to be assembled from separate short clips in editing.

## Related Skills

- [AI Game Environment](../ai-game-environment/SKILL.md) — Backdrop concepts for trailer scenes
- [AI Character Design](../ai-character-design/SKILL.md) — Character references for consistency
- [AI Game Asset](../ai-game-asset/SKILL.md) — Props and items featured in trailers
- [AI Product Video Ad](../../ecommerce/ai-product-video-ad/SKILL.md) — Video ad techniques

## Related Models

- [wan-2-1](../../../models/wan-2-1/SKILL.md) — High quality video generation
- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image stills
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
