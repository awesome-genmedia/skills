---
name: elevenlabs-text-to-dialogue
description: "Elevenlabs Text to Dialogue. Generate multi-speaker dialogue audio using Elevenlabs AI voices. Triggers: elevenlabs, text to speech, dialogue, multi-speaker, voice generation, tts"
allowed-tools: Bash(curl *), WebFetch
---

# Elevenlabs Text to Dialogue

Generate multi-speaker dialogue audio using Elevenlabs AI voices. Supports multiple input voices, text normalization, language control, and deterministic generation with seeds.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-text-to-dialogue",
    "version": "0.0.1",
    "input": {
      "inputs": [
        {"text": "Welcome to the show! Today we have a special guest.", "voice_id": "voice_1"},
        {"text": "Thanks for having me, it is great to be here.", "voice_id": "voice_2"}
      ],
      "model_id": "eleven_v3",
      "stability": 0.5,
      "apply_text_normalization": "auto"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| apply_text_normalization | string | auto | Text normalization mode. enum: auto, on, off |
| inputs | array | | Array of dialogue inputs with text and voice configuration |
| language_code | string | | Language code (ISO 639-1) for language enforcement and text normalization |
| model_id | string | eleven_v3 | Voice model. enum: eleven_v3 |
| seed | integer | | Random seed for deterministic generation |
| stability | number | 0.5 | Voice stability control |

## Examples

**Two-speaker podcast dialogue:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-text-to-dialogue",
    "version": "0.0.1",
    "input": {
      "inputs": [
        {"text": "So what are your thoughts on the latest developments in AI?", "voice_id": "host"},
        {"text": "I think we are seeing a fundamental shift in how people interact with technology.", "voice_id": "guest"},
        {"text": "That is a fascinating perspective. Can you elaborate?", "voice_id": "host"}
      ],
      "model_id": "eleven_v3",
      "stability": 0.6,
      "apply_text_normalization": "auto"
    }
  }'
```

**Multilingual dialogue with seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-text-to-dialogue",
    "version": "0.0.1",
    "input": {
      "inputs": [
        {"text": "Buenos dias, como estas?", "voice_id": "speaker_a"},
        {"text": "Muy bien, gracias. Y tu?", "voice_id": "speaker_b"}
      ],
      "model_id": "eleven_v3",
      "language_code": "es",
      "stability": 0.5,
      "seed": 12345
    }
  }'
```

## Related Models

- [elevenlabs-voice-design-v3](../elevenlabs-voice-design-v3/) - Design custom voices with Elevenlabs V3
- [elevenlabs-voice-design-v2](../elevenlabs-voice-design-v2/) - Design custom voices with Elevenlabs V2
- [chatterbox-speech-to-speech](../chatterbox-speech-to-speech/) - Speech to speech conversion

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
