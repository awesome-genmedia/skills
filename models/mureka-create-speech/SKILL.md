---
name: mureka-create-speech
description: "Mureka | Create Speech. Generate speech audio with selectable voices or custom voice cloning. Triggers: speech, tts, mureka, voice, text to speech"
allowed-tools: Bash(curl *), WebFetch
---

# Mureka | Create Speech

Generate speech audio with built-in voice presets (Ethan, Victoria, Jake, Luna, Emma) or use a custom voice ID for voice cloning.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-create-speech",
    "version": "0.0.1",
    "input": {
      "text": "Hello! Welcome to our product demo. Let me show you the exciting new features.",
      "voice": "Victoria"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| text | string | false | Text to convert to speech. |
| voice | string | false | Voice preset to use. enum: Ethan, Victoria, Jake, Luna, Emma, Null |
| voice_id | string | false | Custom voice ID for cloned voice (from files/upload API). Overrides voice preset. |

## Examples

**Using a built-in voice:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-create-speech",
    "version": "0.0.1",
    "input": {
      "text": "The quarterly results exceeded all expectations, showing a 30 percent increase in revenue.",
      "voice": "Ethan"
    }
  }'
```

**Using a different voice preset:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-create-speech",
    "version": "0.0.1",
    "input": {
      "text": "Once upon a time, in a land far away, there lived a brave little fox who dreamed of seeing the ocean.",
      "voice": "Luna"
    }
  }'
```

**Using a custom cloned voice:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-create-speech",
    "version": "0.0.1",
    "input": {
      "text": "This is generated using my custom voice clone.",
      "voice_id": "custom-voice-id-from-upload"
    }
  }'
```

## Related Models

- [mureka-create-podcast](../mureka-create-podcast/) - Create podcast with 2 speakers
- [xai-grok-tts-text-to-speech](../xai-grok-tts-text-to-speech/) - Grok text to speech
- [mureka-upload-file](../mureka-upload-file/) - Upload files for voice cloning

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
