---
name: minimax-music-v2
description: "Minimax Music v2. Generate music and songs with lyrics from text descriptions. Triggers: music generation, minimax, song creation, audio, lyrics"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Music v2

Generate music and songs from text descriptions with optional lyrics. Specify style, mood, and scenario to create custom music tracks with structured lyrics support.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-music-v2",
    "version": "0.0.1",
    "input": {
      "prompt": "upbeat pop song, cheerful mood, summer vibes",
      "lyrics_prompt": "[Verse]\nSunshine on my face today\nFeeling good in every way\n[Chorus]\nLet the music play all night\nEverything is gonna be alright"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_setting | object | | Audio configuration settings. |
| lyrics_prompt | string | | Lyrics of the song. Use newlines to separate lines. May include structure tags like [Intro], [Verse], [Chorus], [Bridge], [Outro]. |
| prompt | string | | A description of the music, specifying style, mood, and scenario. 10-300 characters. |

## Examples

**Instrumental track:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-music-v2",
    "version": "0.0.1",
    "input": {
      "prompt": "calm lo-fi hip hop instrumental, rainy day cafe atmosphere, relaxing beats"
    }
  }'
```

**Full song with lyrics:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-music-v2",
    "version": "0.0.1",
    "input": {
      "prompt": "emotional ballad, piano and strings, slow tempo, heartfelt",
      "lyrics_prompt": "[Intro]\n(Soft piano)\n[Verse 1]\nIn the quiet of the night\nI remember how you smiled\n[Chorus]\nAnd I will always carry you\nIn the spaces between the stars"
    }
  }'
```

## Related Models

- [Minimax Music v1.5](../minimax-music-v1-5/) - Previous version music generation
- [Stable Audio 2.5 | Text to Audio](../stable-audio-2-5-text-to-audio/) - Alternative audio generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
