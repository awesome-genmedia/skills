---
name: "Video Analyzer"
description: "Analyze video content using AI. Trigger: Use when the user wants to analyze a video, or requests 'video analyzer', 'analyze video', 'describe video', or 'what is in this video'."
allowed-tools: ["Bash"]
---

# Video Analyzer

Analyze video content using AI. Ask questions about the video or get a detailed description of what happens in it.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "video-analyzer",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/clip.mp4",
      "prompt": "Describe what happens in this video",
      "detailed_analysis": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `detailed_analysis` | boolean | `false` | Whether to request a more detailed analysis of the video |
| `prompt` | string | `false` | The question or prompt about the video content |
| `video_url` | string | `false` | URL of the video to analyze |

## Output

- **Type:** text

## Examples

### General Video Description
```json
{
  "model": "video-analyzer",
  "version": "0.0.1",
  "input": {
    "video_url": "https://example.com/nature-documentary.mp4",
    "prompt": "Describe the main events and subjects in this video",
    "detailed_analysis": true
  }
}
```

### Specific Question
```json
{
  "model": "video-analyzer",
  "version": "0.0.1",
  "input": {
    "video_url": "https://example.com/cooking-video.mp4",
    "prompt": "What ingredients are being used and what dish is being prepared?",
    "detailed_analysis": false
  }
}
```

## Related Models

- [Gemini 2.0 Flash Lite](../gemini-2-0-flash-lite/SKILL.md) - Multimodal AI for image and text analysis
- [PixVerse v5 Extend](../pixverse-v5-extend/SKILL.md) - Extend analyzed videos

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
