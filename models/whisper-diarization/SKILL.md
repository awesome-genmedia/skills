---
name: whisper-diarization
description: "Whisper Diarization. Transcribe audio with speaker identification and diarization. Triggers: transcription, speech to text, speaker diarization, multi-speaker, whisper"
allowed-tools: Bash(curl *), WebFetch
---

# Whisper Diarization

Transcribe audio files with speaker diarization, identifying and labeling different speakers in the audio. Supports speaker grouping, translation, and vocabulary prompts for improved accuracy.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "whisper-diarization",
    "version": "0.0.1",
    "input": {
      "file_url": "https://example.com/interview.mp3",
      "num_speakers": 2,
      "language": "en",
      "group_segments": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| file | string | - | An audio file (direct upload). |
| file_string | string | - | Base64 encoded audio file. |
| file_url | string | - | A direct audio file URL. |
| group_segments | boolean | true | Group segments of same speaker shorter apart than 2 seconds. |
| language | string | en | Language of the spoken words as a language code. Leave empty to auto detect. |
| num_speakers | integer | 2 | Number of speakers. Leave empty to autodetect. |
| prompt | string | - | Vocabulary: provide names, acronyms and loanwords in a list. Use punctuation for clarity. |
| translate | boolean | false | Translate the speech into English. |

## Examples

**Basic diarization:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "whisper-diarization",
    "version": "0.0.1",
    "input": {
      "file_url": "https://example.com/podcast-episode.mp3"
    }
  }'
```

**Multi-speaker meeting with vocabulary hints:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "whisper-diarization",
    "version": "0.0.1",
    "input": {
      "file_url": "https://example.com/board-meeting.mp3",
      "num_speakers": 5,
      "language": "en",
      "prompt": "Acme Corp, Q4 earnings, EBITDA, revenue forecast",
      "group_segments": true
    }
  }'
```

**Foreign language with translation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "whisper-diarization",
    "version": "0.0.1",
    "input": {
      "file_url": "https://example.com/spanish-debate.mp3",
      "language": "es",
      "num_speakers": 3,
      "translate": true
    }
  }'
```

## Related Models

- [Whisper](../whisper/) - Standard transcription without diarization
- [Wizper with Timestamp](../wizper-with-timestamp/) - Transcription with timestamps

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
