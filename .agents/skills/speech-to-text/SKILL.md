---
name: speech-to-text
description: "Transcribe audio to text using each::sense AI. Convert speech from audio and video files into accurate text with punctuation, speaker detection, and timestamp support. Handles multiple languages, accents, and noisy environments. Use for: transcription, subtitles, meeting notes, interview transcripts, podcast show notes, accessibility, captioning. Triggers: speech to text, transcribe, transcription, audio to text, stt, voice to text, convert speech, dictation, subtitles, captions, whisper, transcribe audio"
allowed-tools: Bash(curl *), WebFetch
---

# Speech to Text

Transcribe audio and video into accurate text using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Transcribe this audio recording into text. Include punctuation and paragraph breaks."},
              {"type": "image_url", "image_url": {"url": "https://example.com/meeting-recording.mp3"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Using Python (OpenAI SDK)

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

response = client.chat.completions.create(
    model="eachsense/beta",
    messages=[{"role": "user", "content": "Transcribe this audio recording into text. Include punctuation and paragraph breaks."}],
    # Images are included in the message content array above
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Transcribe the speech in this video clip. Include timestamps for each sentence."},
              {"type": "image_url", "image_url": {"url": "https://example.com/presentation-video.mp4"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Transcription Capabilities

| Feature | Description | How to Request |
|---------|-------------|----------------|
| **Basic Transcription** | Plain text output with punctuation | "Transcribe this audio" |
| **Timestamps** | Time codes for each segment | "Transcribe with timestamps" |
| **Speaker Labels** | Identify different speakers | "Transcribe and label each speaker" |
| **Paragraph Breaks** | Logical text segmentation | "Transcribe with paragraph breaks" |
| **Language Detection** | Auto-detect spoken language | "Detect the language and transcribe" |
| **Translation** | Transcribe and translate | "Transcribe and translate to English" |
| **Summary** | Transcribe and summarize | "Transcribe and provide a summary" |
| **SRT Format** | Subtitle file format | "Transcribe in SRT subtitle format" |

## Supported Input Formats

| Type | Formats |
|------|---------|
| **Audio** | MP3, WAV, M4A, FLAC, OGG, AAC, WMA, WEBM |
| **Video** | MP4, MOV, AVI, MKV, WEBM |

## Prompt Tips

### Specify Output Format

Be explicit about how you want the transcription structured:

```
"Transcribe this audio verbatim, including filler words like
um and uh. Add timestamps every 30 seconds. Format as:
[00:00] Text here
[00:30] More text here"
```

### Request Speaker Identification

For multi-speaker audio:

```
"Transcribe this conversation and label each speaker as
Speaker 1, Speaker 2, etc. Start a new line when the
speaker changes."
```

### Clean Transcription vs. Verbatim

```
# Verbatim (includes everything)
"Transcribe exactly as spoken, including filler words, false starts, and repetitions"

# Clean (polished)
"Transcribe cleanly, removing filler words and false starts. Fix grammar for readability."
```

### Specify Language

For non-English audio or to guide recognition:

```
"This audio is in German. Transcribe it in German."
"This audio is in Japanese. Transcribe in Japanese and provide an English translation."
```

## Examples

### Meeting Transcription

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Transcribe this meeting recording. Label each speaker (Speaker 1, Speaker 2, etc.). Add timestamps at the start of each speaker turn. Include a brief summary of key decisions and action items at the end."},
              {"type": "image_url", "image_url": {"url": "https://example.com/team-meeting.mp3"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Subtitle Generation (SRT Format)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Transcribe this video into SRT subtitle format. Each subtitle should be 1-2 lines, maximum 42 characters per line. Format:\n\n1\n00:00:01,000 --> 00:00:04,000\nSubtitle text here\n\n2\n00:00:04,500 --> 00:00:08,000\nNext subtitle here"},
              {"type": "image_url", "image_url": {"url": "https://example.com/tutorial-video.mp4"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Interview Transcript

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Transcribe this interview recording. Format as a clean Q&A transcript with the interviewer questions in bold and interviewee answers in regular text. Remove filler words and false starts. Add paragraph breaks for readability."},
              {"type": "image_url", "image_url": {"url": "https://example.com/interview.mp3"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Multilingual Transcription with Translation

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "This audio is a Spanish-language podcast episode. Transcribe it in the original Spanish, then provide a complete English translation below. Maintain paragraph structure in both versions."},
              {"type": "image_url", "image_url": {"url": "https://example.com/spanish-podcast.mp3"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Podcast Show Notes

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Transcribe this podcast episode and generate structured show notes. Include: 1) Episode summary (2-3 sentences), 2) Key topics discussed with timestamps, 3) Notable quotes, 4) Any resources or links mentioned, 5) Full transcript with speaker labels and timestamps."},
              {"type": "image_url", "image_url": {"url": "https://example.com/podcast-episode.mp3"}}
            ]
          }
    ],
    "stream": false
  }'
```

## Batch Transcription

```bash
# Transcribe multiple audio files
AUDIO_FILES=(
  "https://example.com/recording-1.mp3"
  "https://example.com/recording-2.mp3"
  "https://example.com/recording-3.mp3"
)

for AUDIO in "${AUDIO_FILES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Transcribe this audio with timestamps and speaker labels. Clean transcription, no filler words.\"}],
      \"image_urls\": [\"$AUDIO\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Transcription Quality Tips

- **Clean audio** produces far better results. Remove background noise when possible before transcribing.
- **Specify the language** if it is not English to improve accuracy.
- **Shorter segments** (under 30 minutes) transcribe more reliably than very long recordings.
- **Single speaker** audio is easiest; multi-speaker requires explicit labeling instructions.
- **Technical jargon** can be specified: "This is a medical lecture; expect terminology like..." to improve accuracy.
- **Accented speech** is handled well, but mentioning the accent helps: "The speaker has a Scottish accent."

## Common Pitfalls

- **No format instructions** produces a wall of text. Specify paragraphs, timestamps, or speakers.
- **Expecting perfect verbatim** from noisy audio is unrealistic. Clean audio gives clean transcripts.
- **Very long audio** without chunking may hit limits. For hour-long recordings, consider splitting into segments.
- **Overlapping speakers** are hard for any system. Minimize crosstalk in source recordings.
- **Background music** competing with speech reduces accuracy. Voice-isolated audio works best.

## Related Skills

- [Text to Speech](../text-to-speech/SKILL.md) — Convert transcripts back to speech
- [Voice Generation](../voice-generation/SKILL.md) — Generate new voice audio from text
- [Video Generation](../video-generation/SKILL.md) — Create videos to pair with transcripts
- [Lyrics Generation](../lyrics-generation/SKILL.md) — Transcribe song lyrics from audio

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
