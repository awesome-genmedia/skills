---
name: xai-grok-tts-text-to-speech
description: "xAI | Grok TTS | Text to Speech. Convert text to speech with multiple voice options and audio format controls. Triggers: tts, text to speech, grok, xai, voice, audio"
allowed-tools: Bash(curl *), WebFetch
---

# xAI | Grok TTS | Text to Speech

Convert text to speech using xAI's Grok TTS engine with 5 voice options, multiple audio codecs, and configurable sample rates. Supports 20+ languages with automatic detection.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-tts-text-to-speech",
    "version": "0.0.1",
    "input": {
      "text": "Hello! Welcome to our product demonstration. Let me walk you through the key features.",
      "voice_id": "eve",
      "output_format": "mp3",
      "sample_rate": 24000
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| bit_rate | integer | 128000 | MP3 bit rate in bps (MP3 codec only). 32000: low/small file. 128000: standard. |
| output_format | string | mp3 | Audio codec. mp3: general use. wav: lossless. enum: mp3, wav, pcm, mulaw, alaw |
| sample_rate | integer | 24000 | Audio sample rate in Hz. 8000: narrowband. 16000: wideband. 22050/24000: standard. |
| text | string | | Text to convert to speech. Maximum 15000 characters. Supports 20+ languages. |
| voice_id | string | eve | Voice selection. eve: energetic/upbeat. ara, rex, sal, leo also available. enum: eve, ara, rex, sal, leo |

## Examples

**Standard MP3 with Eve voice:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-tts-text-to-speech",
    "version": "0.0.1",
    "input": {
      "text": "The future of artificial intelligence is both exciting and full of possibilities.",
      "voice_id": "eve",
      "output_format": "mp3"
    }
  }'
```

**High-quality WAV with Rex voice:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-tts-text-to-speech",
    "version": "0.0.1",
    "input": {
      "text": "Breaking news: Scientists have made a groundbreaking discovery in renewable energy technology.",
      "voice_id": "rex",
      "output_format": "wav",
      "sample_rate": 24000
    }
  }'
```

**Low bit-rate MP3 for telephony:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-tts-text-to-speech",
    "version": "0.0.1",
    "input": {
      "text": "Your appointment is confirmed for tomorrow at 3 PM. Press 1 to confirm or 2 to reschedule.",
      "voice_id": "sal",
      "output_format": "mulaw",
      "sample_rate": 8000
    }
  }'
```

## Related Models

- [google-text-to-speech](../google-text-to-speech/) - Google text to speech
- [mureka-create-speech](../mureka-create-speech/) - Mureka speech generation with voice cloning
- [inworld-tts-1-5](../inworld-tts-1-5/) - Inworld text to speech

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
