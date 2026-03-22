---
name: mureka-generate-song
description: "Mureka | Generate Song. Generate songs with AI using lyrics, melody, and voice references. Triggers: music generation, ai song, create song, mureka, ai music"
allowed-tools: Bash(curl *), WebFetch
---

# Mureka | Generate Song

Generate AI-powered songs with customizable lyrics, melody references, and vocal styles. Supports multiple model versions and can produce up to 3 song variations per request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-song",
    "version": "0.0.1",
    "input": {
      "prompt": "An upbeat pop song about summer adventures with friends",
      "lyrics": "Sunshine on my face, wind in my hair\nDriving down the coast without a care\nFriends by my side, music up loud\nWe are young and free and proud",
      "model": "auto",
      "n": 2
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| lyrics | string | - | The lyrics for the song. |
| melody_id | string | - | Control music generation by melody idea, generated through the files/upload API. |
| model | string | auto | Model version to use. Options: `auto`, `mureka-7.5`, `mureka-7.6`, `mureka-o2`, `mureka-8` |
| n | integer | 2 | How many songs to generate for each request. Defaults to 2, maximum 3. |
| prompt | string | - | Text prompt describing the desired song style and mood. |
| reference_id | string | - | Control music generation by referencing music, generated through the files/upload API. |
| vocal_id | string | - | Control music generation by any voice you like, generated through the files/upload API. |

## Examples

**Simple song from prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-song",
    "version": "0.0.1",
    "input": {
      "prompt": "A melancholic acoustic ballad about lost love",
      "n": 1
    }
  }'
```

**Song with lyrics and specific model:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-song",
    "version": "0.0.1",
    "input": {
      "prompt": "Energetic electronic dance track with heavy bass",
      "lyrics": "Feel the beat drop, hands up high\nLights are flashing, touch the sky\nLost in the rhythm, lose control\nLet the music fill your soul",
      "model": "mureka-8",
      "n": 3
    }
  }'
```

**Song with reference material:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-song",
    "version": "0.0.1",
    "input": {
      "prompt": "A jazz-inspired vocal track with smooth saxophone",
      "reference_id": "your-reference-id-here",
      "vocal_id": "your-vocal-id-here",
      "n": 2
    }
  }'
```

## Related Models

- [Mureka | Describe Song](../mureka-describe-song/) - Describe and analyze an existing song
- [Mureka | Generate Instrumental](../mureka-generate-instrumental/) - Generate instrumental music
- [Mureka | Extend Song](../mureka-extend-song/) - Extend an existing song
- [Mureka | Generate Lyrics](../mureka-generate-lyrics/) - Generate lyrics for a song

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
