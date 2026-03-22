---
name: auto-subtitle
description: "Auto Subtitle. Automatically add animated karaoke-style subtitles to videos. Triggers: subtitles, captions, transcription, video editing, karaoke, TikTok"
allowed-tools: Bash(curl *), WebFetch
---

# Auto Subtitle

Automatically transcribe and add animated karaoke-style subtitles to videos. Supports multiple languages, customizable fonts from Google Fonts, and TikTok-style word highlighting.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "auto-subtitle",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/talking-head.mp4",
      "language": "en",
      "font_name": "Montserrat",
      "font_size": 100,
      "highlight_color": "purple"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| background_color | string | none | Background color behind text. enum: black, white, red, green, blue, yellow, orange, purple, pink, brown, gray, cyan, magenta, none, transparent |
| background_opacity | number | 0 | Background opacity (0.0 = fully transparent, 1.0 = fully opaque). |
| enable_animation | boolean | true | Enable animation effects for subtitles (bounce style entrance). |
| font_color | string | white | Subtitle text color for non-active words. enum: white, black, red, green, blue, yellow, orange, purple, pink, brown, gray, cyan, magenta |
| font_name | string | Montserrat | Any Google Font name from fonts.google.com. |
| font_size | integer | 100 | Font size for subtitles. |
| font_weight | string | bold | Font weight. enum: normal, bold, black |
| highlight_color | string | purple | Color for the currently speaking word (karaoke-style). enum: white, black, red, green, blue, yellow, orange, purple, pink, brown, gray, cyan, magenta |
| language | string | en | Language code for transcription (e.g., en, es, fr, de). |
| position | string | bottom | Vertical position of subtitles. enum: top, center, bottom |
| stroke_color | string | black | Text stroke/outline color. enum: black, white, red, green, blue, yellow, orange, purple, pink, brown, gray, cyan, magenta |
| stroke_width | integer | 3 | Text stroke/outline width in pixels (0 for no stroke). |
| video_url | string | | URL of the video file to add subtitles to. |
| words_per_subtitle | integer | 3 | Maximum number of words per subtitle segment. Use 1 for single-word display. |
| y_offset | integer | 75 | Vertical offset in pixels (positive = move down, negative = move up). |

## Examples

**TikTok-style centered subtitles:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "auto-subtitle",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/tiktok-clip.mp4",
      "language": "en",
      "font_name": "Poppins",
      "font_size": 120,
      "font_weight": "black",
      "font_color": "white",
      "highlight_color": "yellow",
      "position": "center",
      "words_per_subtitle": 2,
      "enable_animation": true,
      "stroke_width": 4
    }
  }'
```

**Minimal subtitles with background:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "auto-subtitle",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/interview.mp4",
      "language": "en",
      "font_name": "Montserrat",
      "font_size": 80,
      "font_weight": "normal",
      "background_color": "black",
      "background_opacity": 0.7,
      "position": "bottom",
      "words_per_subtitle": 5,
      "enable_animation": false
    }
  }'
```

**Spanish subtitles:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "auto-subtitle",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/spanish-video.mp4",
      "language": "es",
      "font_name": "Roboto",
      "highlight_color": "red",
      "words_per_subtitle": 3
    }
  }'
```

## Related Models

- [Elevenlabs Speech to Text](../elevenlabs-speech-to-text/) - Speech transcription
- [Whisper](../whisper/) - Audio transcription

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
