---
name: mureka-create-podcast
description: "Mureka | Create Podcast. Generate podcast audio with 2-speaker conversations. Triggers: podcast, mureka, audio, conversation, dialogue"
allowed-tools: Bash(curl *), WebFetch
---

# Mureka | Create Podcast

Generate podcast-style audio with exactly 2 speakers. Create conversational audio content from structured dialogue input.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-create-podcast",
    "version": "0.0.1",
    "input": {
      "conversations": [
        {"speaker": "voice_id_1", "text": "Welcome to the show! Today we are discussing AI in music."},
        {"speaker": "voice_id_2", "text": "Thanks for having me. This is such a fascinating topic."}
      ]
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| conversations | array | false | Speaker limit: exactly 2 speakers (two Voice IDs). Array of conversation turns. |

## Examples

**Two-speaker podcast:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-create-podcast",
    "version": "0.0.1",
    "input": {
      "conversations": [
        {"speaker": "voice_id_1", "text": "Welcome back to Tech Talk. Today we are exploring the future of generative AI."},
        {"speaker": "voice_id_2", "text": "Absolutely. The pace of innovation has been incredible this year."},
        {"speaker": "voice_id_1", "text": "Let us start with the biggest breakthroughs. What stands out to you?"},
        {"speaker": "voice_id_2", "text": "For me, it is the advancement in multimodal models that can handle text, images, and video."}
      ]
    }
  }'
```

**Short dialogue exchange:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-create-podcast",
    "version": "0.0.1",
    "input": {
      "conversations": [
        {"speaker": "voice_id_1", "text": "What is your favorite album of the year?"},
        {"speaker": "voice_id_2", "text": "I would have to say the new indie rock release from last month. The production quality is outstanding."}
      ]
    }
  }'
```

## Related Models

- [mureka-create-speech](../mureka-create-speech/) - Single-speaker speech generation
- [mureka-generate-lyrics](../mureka-generate-lyrics/) - Lyrics generation
- [mureka-generate-instrumental](../mureka-generate-instrumental/) - Instrumental music generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
