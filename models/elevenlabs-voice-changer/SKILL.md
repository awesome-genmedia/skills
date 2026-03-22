---
name: elevenlabs-voice-changer
description: "ElevenLabs | Voice Changer. Change the voice in audio files using ElevenLabs AI voice cloning. Transform any voice to sound like a different speaker. Triggers: voice changer, change voice, elevenlabs voice, voice clone, voice swap, voice transformation, speech to speech"
allowed-tools: Bash(curl *), WebFetch
---

# ElevenLabs | Voice Changer

Change the voice in audio files using ElevenLabs AI. Upload audio and select a target voice to transform the speaker's voice while preserving the speech content, intonation, and emotion.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-voice-changer",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/speech-recording.mp3",
      "voice_id": "9BWtsMINqrJLrRacOk9x",
      "model_id": "eleven_english_sts_v2"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | - | URL of the audio file to transform |
| model_id | string | eleven_english_sts_v2 | Voice conversion model. Options: `eleven_english_sts_v2` |
| voice_id | string | - | Target voice ID. Available voices: Aria (`9BWtsMINqrJLrRacOk9x`), Roger (`CwhRBWXzGAHq8TQ4Fs17`), Sarah (`EXAVITQu4vr4xnSDxMaL`), Laura (`FGY2WhTYpPnrIDTdsKH5`), Charlie (`IKne3meq5aSn9XLyUdCD`), George (`JBFqnCBsd6RMkjVDRZzb`), Callum (`N2lVS1w4EtoT3dr4eOWO`), River (`SAz9YHcvj6GT2YYXdXww`), Liam (`TX3LPaxmHKxFdv7VOQHJ`), Charlotte (`XB0fDUnXU5powFXDhCwa`), Alice (`Xb7hH8MSUJpSbSDYk0k2`), Matilda (`XrExE9yKIg1WjnnlVkGX`), Will (`bIHbv24MWmeRgasZH58o`), Jessica (`cgSgspJ2msm6clMCkdW9`), Eric (`cjVigY5qzO86Huf0OWal`), Chris (`iP95p4xoKVk53GoZ742B`), Brian (`nPczCjzI2devNBz1zQrb`), Daniel (`onwK4e9ZLuTAKqWW03F9`), Lily (`pFZP5JQG7iQjIQuC4Bku`), Bill (`pqHfZKP75CvOlQylNhV4`) |

## Examples

**Change voice to Aria:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-voice-changer",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/podcast-clip.mp3",
      "voice_id": "9BWtsMINqrJLrRacOk9x"
    }
  }'
```

**Change voice to Brian:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "elevenlabs-voice-changer",
    "version": "0.0.1",
    "input": {
      "audio_url": "https://example.com/narration.wav",
      "voice_id": "nPczCjzI2devNBz1zQrb",
      "model_id": "eleven_english_sts_v2"
    }
  }'
```

## Related Models

- [ElevenLabs | Text to Speech](../elevenlabs-text-to-speech/) - Generate speech from text
- [ElevenLabs | Sound Effects](../elevenlabs-sound-effects/) - Generate sound effects
- [PixVerse | Lip Sync](../pixverse-lip-sync/) - Lip sync audio to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
