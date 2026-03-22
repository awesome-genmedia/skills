---
name: deepgram-nova-3-speech-to-text-pro
description: "Deepgram | Nova-3 | Speech to Text Pro. Advanced speech transcription with diarization, sentiment, entities, intents, and summarization. Triggers: transcribe, speech to text, stt, deepgram, nova, diarize, sentiment"
allowed-tools: Bash(curl *), WebFetch
---

# Deepgram | Nova-3 | Speech to Text Pro

Advanced speech-to-text transcription powered by Deepgram Nova-3 with speaker diarization, named entity detection, intent classification, sentiment analysis, topic detection, and automatic summarization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "deepgram-nova-3-speech-to-text-pro",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/meeting-recording.mp3",
      "model": "nova-3",
      "language_code": "en",
      "diarize": true,
      "summarize": true,
      "sentiment": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| detect_entities | boolean | true | Extract named entities: persons, organizations, locations, dates, ordinals. |
| diarize | boolean | true | Identify different speakers. Each word includes speaker ID and confidence score. |
| filler_words | boolean | true | Include filler words (uh, um) in transcript. |
| intents | boolean | true | Detect speaker intents. Returns intent labels with confidence scores per segment. |
| language_code | string | auto | Language of the audio (BCP-47). auto: automatic detection. multi: multilingual. enum: auto, multi, tr, ur, en, nl, uk, es, ar, de, fr, it, ja, ko, pt, ru, zh, hi, and more |
| media_url | string | | Audio file URL to transcribe. Supports mp3, wav, m4a, flac, ogg, webm, mp4. |
| model | string | nova-3 | Deepgram model. nova-3: latest, best accuracy. nova-2: previous generation. enum: nova-3, nova-2 |
| multichannel | boolean | false | Transcribe each audio channel independently. Max 5 channels. |
| numerals | boolean | false | Convert spoken numbers to digits (e.g., three hundred to 300). |
| paragraphs | boolean | true | Split transcript into paragraphs with sentences. Requires punctuate=true. |
| profanity_filter | boolean | false | Replace profanity with asterisks in transcript. |
| punctuate | boolean | true | Add punctuation and capitalization to transcript. |
| redact | string | false | Redact sensitive info. false: none. pci: credit cards. pii: SSN/phone/email. enum: false, pci, pii, numbers |
| sentiment | boolean | true | Analyze sentiment per segment and overall. |
| smart_format | boolean | true | Auto-format currency, phone numbers, emails, dates for readability. |
| summarize | boolean | true | Generate a short text summary of the transcript content. |
| topics | boolean | true | Detect topics discussed. Returns topic labels with confidence scores. |
| utt_split | number | 0.8 | Seconds of silence to split utterances. Lower = more splits. |
| utterances | boolean | true | Segment speech into semantic units with start/end times and speaker info. |

## Examples

**Full meeting transcription with all features:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "deepgram-nova-3-speech-to-text-pro",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/team-meeting.mp3",
      "model": "nova-3",
      "language_code": "en",
      "diarize": true,
      "summarize": true,
      "sentiment": true,
      "detect_entities": true,
      "intents": true,
      "topics": true,
      "paragraphs": true
    }
  }'
```

**Simple transcription with PII redaction:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "deepgram-nova-3-speech-to-text-pro",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/customer-call.wav",
      "model": "nova-3",
      "redact": "pii",
      "profanity_filter": true,
      "numerals": true
    }
  }'
```

**Multilingual transcription:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "deepgram-nova-3-speech-to-text-pro",
    "version": "0.0.1",
    "input": {
      "media_url": "https://example.com/multilingual-podcast.mp3",
      "language_code": "multi",
      "diarize": true,
      "filler_words": false,
      "smart_format": true
    }
  }'
```

## Related Models

- [deepgram-nova-3-speech-to-text](../deepgram-nova-3-speech-to-text/) - Standard Deepgram Nova-3 transcription
- [elevenlabs-speech-to-text-scribe-v2](../elevenlabs-speech-to-text-scribe-v2/) - ElevenLabs speech to text

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
