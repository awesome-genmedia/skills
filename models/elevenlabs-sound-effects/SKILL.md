---
name: elevenlabs-sound-effects
description: "ElevenLabs | Sound Effects. Generate sound effects from text descriptions using ElevenLabs AI. Create any sound effect from a text prompt. Triggers: sound effects, generate sound, sfx, audio effects, elevenlabs sound, create sound effect, foley"
allowed-tools: Bash(curl *), WebFetch
---

# ElevenLabs | Sound Effects

Generate sound effects from text descriptions using ElevenLabs AI. Describe any sound and the model produces a high-quality audio clip matching your description, with control over duration and prompt adherence.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-sound-effects",
    "version": "0.0.1",
    "input": {
      "text": "Thunder rumbling in the distance followed by heavy rain on a tin roof",
      "duration_seconds": 5,
      "prompt_influence": 0.3
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration_seconds | integer | 1 | Duration of the generated sound in seconds. Must be at least 0 |
| prompt_influence | number | 0.3 | How closely the generation follows the prompt. Higher values produce more literal results |
| text | string | - | Text description of the sound effect to generate |

## Examples

**Ambient forest sounds:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-sound-effects",
    "version": "0.0.1",
    "input": {
      "text": "Birds chirping in a peaceful forest with a gentle stream flowing nearby",
      "duration_seconds": 10,
      "prompt_influence": 0.4
    }
  }'
```

**Sci-fi laser effect:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-sound-effects",
    "version": "0.0.1",
    "input": {
      "text": "Futuristic laser gun firing three quick shots with electric crackling",
      "duration_seconds": 3,
      "prompt_influence": 0.5
    }
  }'
```

**Door creaking:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-sound-effects",
    "version": "0.0.1",
    "input": {
      "text": "Old wooden door slowly creaking open in a haunted house",
      "duration_seconds": 4,
      "prompt_influence": 0.3
    }
  }'
```

## Related Models

- [ElevenLabs | Text to Speech](../elevenlabs-text-to-speech/) - Generate speech from text
- [ElevenLabs | Voice Changer](../elevenlabs-voice-changer/) - Change voices in audio
- [ElevenLabs | Dubbing](../elevenlabs-dubbing/) - Dub audio/video to other languages

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
