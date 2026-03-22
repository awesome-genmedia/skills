---
name: elevenlabs-text-to-speech
description: "ElevenLabs | Text to Speech. Generate natural-sounding speech from text using ElevenLabs AI voices. High-quality TTS with multiple voices and models. Triggers: text to speech, tts, generate speech, elevenlabs tts, ai voice, voice synthesis, speech generation, read aloud"
allowed-tools: Bash(curl *), WebFetch
---

# ElevenLabs | Text to Speech

Generate natural-sounding speech from text using ElevenLabs AI. Choose from multiple voice models, 20 built-in voices, and fine-tune stability, similarity, and style parameters for precise control over the output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-text-to-speech",
    "version": "0.0.1",
    "input": {
      "text": "Welcome to the future of AI-powered voice synthesis. This is a demonstration of natural speech generation.",
      "voice_id": "9BWtsMINqrJLrRacOk9x",
      "model_id": "eleven_v3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| model_id | string | eleven_v3 | Voice model. Options: `eleven_multilingual_v2`, `eleven_flash_v2_5`, `eleven_turbo_v2_5`, `eleven_turbo_v2`, `eleven_flash_v2`, `eleven_monolingual_v1`, `eleven_multilingual_v1`, `eleven_v3` |
| seed | integer | - | Seed for deterministic generation |
| similarity_boost | number | 0.7 | Voice clarity and target speaker similarity. Very high values can cause artifacts |
| stability | number | 0.5 | Voice consistency between re-generations. Higher values are more consistent but less expressive |
| style | number | 0 | Style exaggeration. High values are recommended for exaggerated speech style |
| text | string | - | Text to convert to speech |
| use_speaker_boost | boolean | false | Boost voice similarity at the cost of some generation speed |
| voice_id | string | - | Target voice. Available voices: Aria (`9BWtsMINqrJLrRacOk9x`), Roger (`CwhRBWXzGAHq8TQ4Fs17`), Sarah (`EXAVITQu4vr4xnSDxMaL`), Laura (`FGY2WhTYpPnrIDTdsKH5`), Charlie (`IKne3meq5aSn9XLyUdCD`), George (`JBFqnCBsd6RMkjVDRZzb`), Callum (`N2lVS1w4EtoT3dr4eOWO`), River (`SAz9YHcvj6GT2YYXdXww`), Liam (`TX3LPaxmHKxFdv7VOQHJ`), Charlotte (`XB0fDUnXU5powFXDhCwa`), Alice (`Xb7hH8MSUJpSbSDYk0k2`), Matilda (`XrExE9yKIg1WjnnlVkGX`), Will (`bIHbv24MWmeRgasZH58o`), Jessica (`cgSgspJ2msm6clMCkdW9`), Eric (`cjVigY5qzO86Huf0OWal`), Chris (`iP95p4xoKVk53GoZ742B`), Brian (`nPczCjzI2devNBz1zQrb`), Daniel (`onwK4e9ZLuTAKqWW03F9`), Lily (`pFZP5JQG7iQjIQuC4Bku`), Bill (`pqHfZKP75CvOlQylNhV4`) |

## Examples

**Narration with Brian voice:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-text-to-speech",
    "version": "0.0.1",
    "input": {
      "text": "In the beginning, there was silence. Then the first star ignited, and the universe was forever changed.",
      "voice_id": "nPczCjzI2devNBz1zQrb",
      "model_id": "eleven_v3",
      "stability": 0.6,
      "similarity_boost": 0.8
    }
  }'
```

**Expressive multilingual speech:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-text-to-speech",
    "version": "0.0.1",
    "input": {
      "text": "Bonjour! Bienvenue dans notre boutique. Nous avons les meilleurs produits pour vous.",
      "voice_id": "pFZP5JQG7iQjIQuC4Bku",
      "model_id": "eleven_multilingual_v2",
      "style": 0.3,
      "stability": 0.4
    }
  }'
```

**Fast turbo generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-text-to-speech",
    "version": "0.0.1",
    "input": {
      "text": "This order has been confirmed and will ship within two business days.",
      "voice_id": "EXAVITQu4vr4xnSDxMaL",
      "model_id": "eleven_turbo_v2_5"
    }
  }'
```

## Related Models

- [ElevenLabs | Voice Changer](../elevenlabs-voice-changer/) - Change voices in existing audio
- [ElevenLabs | Sound Effects](../elevenlabs-sound-effects/) - Generate sound effects from text
- [ElevenLabs | Speech to Text](../elevenlabs-speech-to-text/) - Transcribe audio to text

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
