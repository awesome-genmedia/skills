---
name: mureka-extend-lyrics
description: "Mureka | Extend Lyrics. Continue and extend existing song lyrics. Triggers: lyrics, extend, mureka, songwriting, continue"
allowed-tools: Bash(curl *), WebFetch
---

# Mureka | Extend Lyrics

Continue and extend existing song lyrics by providing the beginning of the lyrics to be continued.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-extend-lyrics",
    "version": "0.0.1",
    "input": {
      "lyrics": "Walking through the city lights\nSearching for a sign tonight\nEvery shadow tells a story\nEvery star reflects the glory"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| lyrics | string | false | Lyrics to be continued. |

## Examples

**Extend a verse:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-extend-lyrics",
    "version": "0.0.1",
    "input": {
      "lyrics": "Verse 1:\nThe morning sun breaks through the haze\nAnother chapter, brand new days\n\nChorus:\nWe rise above the noise and fear"
    }
  }'
```

**Continue a chorus:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-extend-lyrics",
    "version": "0.0.1",
    "input": {
      "lyrics": "Hold my hand and do not let go\nThrough the fire and through the snow\nWe will find our way back home"
    }
  }'
```

## Related Models

- [mureka-generate-lyrics](../mureka-generate-lyrics/) - Generate lyrics from a prompt
- [mureka-extend-song](../mureka-extend-song/) - Extend a song with new audio
- [mureka-generate-instrumental](../mureka-generate-instrumental/) - Generate instrumental music

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
