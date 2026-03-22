---
name: google-text-to-speech
description: "Google | Text to Speech. Convert text to natural-sounding audio using Google TTS. Triggers: tts, text to speech, google, voice, audio, speak"
allowed-tools: Bash(curl *), WebFetch
---

# Google | Text to Speech

Convert text to natural-sounding speech audio using Google's text-to-speech engine.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "google-text-to-speech",
    "version": "0.0.1",
    "input": {}
  }'
```

## Parameters

This model has no documented parameters. Refer to the API documentation for usage details.

## Examples

**Basic text to speech:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "google-text-to-speech",
    "version": "0.0.1",
    "input": {}
  }'
```

## Related Models

- [xai-grok-tts-text-to-speech](../xai-grok-tts-text-to-speech/) - xAI Grok text to speech with voice selection
- [mureka-create-speech](../mureka-create-speech/) - Mureka speech generation
- [inworld-tts-1-5](../inworld-tts-1-5/) - Inworld text to speech

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
