---
name: "Minimax Music V1.5"
description: "Generate music with lyrics using Minimax Music V1.5. Trigger: Use when the user wants to create music, generate a song, or requests 'minimax music', 'AI music generation', or 'create a song with lyrics'."
allowed-tools: ["Bash"]
---

# Minimax Music | V1.5

Generate music tracks with customizable lyrics and style. Supports structured lyrics with sections like intro, verse, chorus, bridge, and outro.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-music-v1-5",
    "version": "0.0.1",
    "input": {
      "prompt": "[verse]Walking down the city streets at night[chorus]Feel the rhythm of the light",
      "lyrics_prompt": "An upbeat pop song with electronic elements and a catchy melody"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `lyrics_prompt` | string | (empty) | Control music generation. 10-3000 characters |
| `prompt` | string | (empty) | Lyrics with section tags: `[intro]`, `[verse]`, `[chorus]`, `[bridge]`, `[outro]`. 10-600 characters |

## Output

- **Type:** audio

## Examples

### Pop Song
```json
{
  "model": "minimax-music-v1-5",
  "version": "0.0.1",
  "input": {
    "prompt": "[intro][verse]Sunlight breaking through the clouds today[chorus]We are alive, we are free, come what may",
    "lyrics_prompt": "A cheerful pop song with piano and acoustic guitar, upbeat tempo"
  }
}
```

### Ambient Instrumental
```json
{
  "model": "minimax-music-v1-5",
  "version": "0.0.1",
  "input": {
    "prompt": "[intro][verse]Gentle waves upon the shore[outro]",
    "lyrics_prompt": "A calm ambient track with soft synthesizers and nature sounds, slow tempo, relaxing mood"
  }
}
```

## Related Models

- [Stable Audio 2.5 Text to Audio](../stable-audio-2-5-text-to-audio/SKILL.md) - Text-driven audio and sound generation
- [Stable Audio 2.5 Audio to Audio](../stable-audio-2-5-audio-to-audio/SKILL.md) - Transform existing audio clips

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
