---
name: elevenlabs-voice-design-v2
description: "Elevenlabs Voice Design V2. Design custom multilingual AI voices from text descriptions using Elevenlabs V2. Triggers: elevenlabs, voice design, custom voice, voice creation, multilingual voice, tts"
allowed-tools: Bash(curl *), WebFetch
---

# Elevenlabs Voice Design V2

Design custom multilingual AI voices from text descriptions using Elevenlabs Voice Design V2. Control voice characteristics with guidance scale, loudness, and quality settings.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-voice-design-v2",
    "version": "0.0.1",
    "input": {
      "voice_description": "A cheerful young female voice with a French accent, perfect for language learning content",
      "text": "Bonjour et bienvenue! Today we will learn about the most beautiful places to visit in Paris. Let us begin our journey through the City of Light.",
      "model_id": "eleven_multilingual_ttv_v2",
      "guidance_scale": 5,
      "loudness": 0.5,
      "quality": 0
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| auto_generate_text | boolean | false | Whether to automatically generate text suitable for the voice description |
| guidance_scale | integer | 5 | Controls how closely the AI follows the prompt. Lower = more freedom |
| loudness | number | 0.5 | Volume level of the generated voice (-1 quietest, 1 loudest) |
| model_id | string | eleven_multilingual_ttv_v2 | Voice model. enum: eleven_multilingual_ttv_v2 |
| quality | number | 0 | Higher quality = better output but less variety |
| seed | integer | | Random seed for reproducible generation |
| text | string | | Text to generate (100-1000 characters) |
| voice_description | string | | Description of the desired voice characteristics |

## Examples

**Narrator voice with high guidance:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-voice-design-v2",
    "version": "0.0.1",
    "input": {
      "voice_description": "A deep, calm male voice with gravelly undertones, ideal for thriller audiobook narration",
      "text": "The shadows lengthened as night fell over the abandoned warehouse district. Detective Morgan pulled his coat tighter, knowing that somewhere in the darkness, the truth was waiting to be found.",
      "model_id": "eleven_multilingual_ttv_v2",
      "guidance_scale": 8,
      "loudness": 0.4,
      "quality": 0.5
    }
  }'
```

**Auto-generated text with seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-voice-design-v2",
    "version": "0.0.1",
    "input": {
      "voice_description": "A warm, energetic female sports commentator voice",
      "auto_generate_text": true,
      "model_id": "eleven_multilingual_ttv_v2",
      "guidance_scale": 5,
      "loudness": 0.7,
      "seed": 42
    }
  }'
```

## Related Models

- [elevenlabs-voice-design-v3](../elevenlabs-voice-design-v3/) - Voice design with Elevenlabs V3
- [elevenlabs-text-to-dialogue](../elevenlabs-text-to-dialogue/) - Multi-speaker dialogue generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
