---
name: elevenlabs-voice-design-v3
description: "Elevenlabs Voice Design V3. Design custom AI voices from text descriptions or reference audio using Elevenlabs V3. Triggers: elevenlabs, voice design, custom voice, voice creation, voice clone, tts"
allowed-tools: Bash(curl *), WebFetch
---

# Elevenlabs Voice Design V3

Design custom AI voices from text descriptions or reference audio using Elevenlabs Voice Design V3. Control voice characteristics with guidance scale, loudness, and prompt strength for precise voice creation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-voice-design-v3",
    "version": "0.0.1",
    "input": {
      "voice_description": "A warm, friendly male voice with a slight British accent, suitable for audiobook narration",
      "text": "The morning sun cast long shadows across the cobblestone street as the baker opened his shop for another day. The aroma of fresh bread filled the air.",
      "model_id": "eleven_ttv_v3",
      "guidance_scale": 5,
      "loudness": 0.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| auto_generate_text | boolean | false | Whether to automatically generate text suitable for the voice description |
| guidance_scale | integer | 5 | Controls how closely the AI follows the prompt. Lower = more freedom |
| loudness | number | 0.5 | Volume level of the generated voice (-1 quietest, 1 loudest) |
| model_id | string | eleven_ttv_v3 | Voice model. enum: eleven_ttv_v3 |
| prompt_strength | number | 0 | Balance of prompt versus reference audio (0 = prompt only) |
| reference_audio_url | string | | URL of reference audio for voice cloning |
| seed | integer | | Random seed for reproducible generation |
| text | string | | Text to generate (100-1000 characters) |
| voice_description | string | | Description of the desired voice characteristics |

## Examples

**Voice from description:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-voice-design-v3",
    "version": "0.0.1",
    "input": {
      "voice_description": "A deep, authoritative female voice with clear enunciation, suitable for documentary narration",
      "text": "In the depths of the Pacific Ocean, a world of wonder exists beyond the reach of sunlight. Here, strange creatures glow with their own ethereal light.",
      "model_id": "eleven_ttv_v3",
      "guidance_scale": 7,
      "loudness": 0.6
    }
  }'
```

**Voice from reference audio with auto text:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-voice-design-v3",
    "version": "0.0.1",
    "input": {
      "reference_audio_url": "https://example.com/voice-sample.mp3",
      "voice_description": "Match the warmth and tone of the reference audio",
      "auto_generate_text": true,
      "model_id": "eleven_ttv_v3",
      "prompt_strength": 0.5,
      "seed": 42
    }
  }'
```

## Related Models

- [elevenlabs-voice-design-v2](../elevenlabs-voice-design-v2/) - Voice design with Elevenlabs V2
- [elevenlabs-text-to-dialogue](../elevenlabs-text-to-dialogue/) - Multi-speaker dialogue generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
