---
name: chatterbox-speech-to-speech
description: "Chatterbox | Speech to Speech. Convert speech audio to new speech with optional voice cloning using Chatterbox. Triggers: chatterbox, speech to speech, voice conversion, voice clone, audio transform"
allowed-tools: Bash(curl *), WebFetch
---

# Chatterbox | Speech to Speech

Convert speech audio to new speech with optional voice cloning using Chatterbox. Provide source audio and optionally a target voice reference to transform the speech output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "chatterbox-speech-to-speech",
    "version": "0.0.1",
    "input": {
      "source_audio_url": "https://example.com/original-speech.mp3",
      "target_voice_audio_url": "https://example.com/target-voice-sample.mp3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| source_audio_url | string | | URL of the source speech audio to convert |
| target_voice_audio_url | string | | Optional URL of reference audio for the target voice style |

## Examples

**Voice conversion with reference:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "chatterbox-speech-to-speech",
    "version": "0.0.1",
    "input": {
      "source_audio_url": "https://example.com/podcast-clip.mp3",
      "target_voice_audio_url": "https://example.com/narrator-voice.mp3"
    }
  }'
```

**Basic speech conversion:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "chatterbox-speech-to-speech",
    "version": "0.0.1",
    "input": {
      "source_audio_url": "https://example.com/meeting-recording.wav"
    }
  }'
```

## Related Models

- [elevenlabs-text-to-dialogue](../elevenlabs-text-to-dialogue/) - Text to dialogue audio
- [elevenlabs-voice-design-v3](../elevenlabs-voice-design-v3/) - Custom voice design
- [wizper](../wizper/) - Speech transcription

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
