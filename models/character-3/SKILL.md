---
name: "Character 3"
description: "Generate character videos driven by audio using Character 3. Trigger: Use when the user wants to animate a character with audio, or requests 'character 3', 'audio driven character', or 'talking character video'."
allowed-tools: ["Bash"]
---

# Character 3

Generate character animation videos driven by audio. Provide a character image and an audio file to create a video of the character speaking or performing.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "character-3",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/character-portrait.jpg",
      "audio_url": "https://example.com/dialogue.mp3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `audio_url` | string | `false` | The URL of the audio file. Audio must be under 30s long |
| `image_url` | string | `false` | The URL of the image used to generate the video |

## Output

- **Type:** video

## Examples

### Talking Character
```json
{
  "model": "character-3",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/business-person.jpg",
    "audio_url": "https://example.com/greeting.mp3"
  }
}
```

### Animated Character Speaking
```json
{
  "model": "character-3",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/cartoon-character.jpg",
    "audio_url": "https://example.com/character-voice.mp3"
  }
}
```

## Related Models

- [Bytedance OmniHuman](../bytedance-omnihuman/SKILL.md) - Alternative audio-driven character animation
- [EchoMimic V3](../echomimic-v3/SKILL.md) - Talking head with more controls
- [Kling V1 Pro AI Avatar](../kling-v1-pro-ai-avatar/SKILL.md) - Pro-quality avatar generation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
