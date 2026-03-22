---
name: inworld-tts-1-5
description: "Inworld TTS 1.5. Convert text to speech using Inworld's text-to-speech engine. Triggers: tts, text to speech, inworld, voice, audio"
allowed-tools: Bash(curl *), WebFetch
---

# Inworld TTS 1.5

Convert text to speech using Inworld's TTS 1.5 engine.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "inworld-tts-1-5",
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
    "model": "inworld-tts-1-5",
    "version": "0.0.1",
    "input": {}
  }'
```

## Related Models

- [xai-grok-tts-text-to-speech](../xai-grok-tts-text-to-speech/) - xAI Grok text to speech with voice selection
- [google-text-to-speech](../google-text-to-speech/) - Google text to speech
- [mureka-create-speech](../mureka-create-speech/) - Mureka speech generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
