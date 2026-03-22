---
name: deepgram-nova-3-speech-to-text
description: "Deepgram | Nova-3 | Speech to Text. Transcribe audio to text with speaker diarization and smart formatting. Triggers: transcribe, speech to text, stt, deepgram, nova, audio"
allowed-tools: Bash(curl *), WebFetch
---

# Deepgram | Nova-3 | Speech to Text

Transcribe audio files to text using Deepgram Nova-3 with speaker diarization, punctuation, and smart formatting for 47+ languages.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "deepgram-nova-3-speech-to-text",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/interview.mp3",
      "model": "nova-3",
      "language_code": "en",
      "diarize": true,
      "punctuate": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| diarize | boolean | true | Identify different speakers in the audio. Each word includes speaker ID and confidence. |
| language_code | string | auto | Language of the audio (BCP-47 code). auto: automatic detection. multi: multilingual. enum: auto, multi, tr, ur, en, nl, uk, es, ar, de, fr, it, ja, ko, pt, ru, zh, hi, and more |
| media_url | string | | Audio file URL to transcribe. Supports mp3, wav, m4a, flac, ogg, webm, mp4. |
| model | string | nova-3 | Deepgram speech recognition model. nova-3: latest, best accuracy. nova-2: previous generation. enum: nova-3, nova-2 |
| multichannel | boolean | false | Transcribe each audio channel independently. Enable when each channel has a different speaker. |
| punctuate | boolean | true | Add punctuation marks and capitalization to the transcript. |
| smart_format | boolean | true | Auto-format currency amounts, phone numbers, email addresses, and dates. |

## Examples

**Basic English transcription:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "deepgram-nova-3-speech-to-text",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/podcast-episode.mp3",
      "model": "nova-3",
      "language_code": "en",
      "diarize": true
    }
  }'
```

**Japanese audio with smart formatting:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "deepgram-nova-3-speech-to-text",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/japanese-audio.wav",
      "language_code": "ja",
      "smart_format": true,
      "punctuate": true
    }
  }'
```

**Multi-channel call center recording:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "deepgram-nova-3-speech-to-text",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/call-recording.wav",
      "model": "nova-3",
      "multichannel": true,
      "diarize": true,
      "smart_format": true
    }
  }'
```

## Related Models

- [deepgram-nova-3-speech-to-text-pro](../deepgram-nova-3-speech-to-text-pro/) - Pro version with sentiment, entities, intents, and summarization
- [elevenlabs-speech-to-text-scribe-v2](../elevenlabs-speech-to-text-scribe-v2/) - ElevenLabs speech to text

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
