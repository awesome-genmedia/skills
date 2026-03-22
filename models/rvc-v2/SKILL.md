---
name: rvc-v2
description: "Rvc v2. Convert voices using RVC v2 models with pitch control and custom models. Triggers: voice conversion, rvc, voice changer, voice clone, ai voice"
allowed-tools: Bash(curl *), WebFetch
---

# Rvc v2

Convert voices using RVC (Retrieval-based Voice Conversion) v2. Apply pre-trained or custom voice models to audio with fine-grained control over pitch, accent blending, and output quality.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "rvc-v2",
    "version": "0.0.1",
    "input": {
      "input_audio": "https://example.com/original-vocals.wav",
      "rvc_model": "Obama",
      "f0_method": "rmvpe",
      "pitch_change": 0,
      "output_format": "wav"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| crepe_hop_length | integer | 128 | When f0_method is mangio-crepe, controls how often it checks for pitch changes. |
| custom_rvc_model_download_url | string | - | URL to download a custom RVC model. If provided, the model will be downloaded. |
| f0_method | string | rmvpe | Pitch detection method. Options: `rmvpe`, `mangio-crepe` |
| filter_radius | integer | 3 | If >=3, apply median filtering to the harvested pitch results. |
| index_rate | number | 0.5 | Control how much of the AI's accent to leave in the vocals. |
| input_audio | string | - | URL of the audio file to convert. |
| output_format | string | wav | Output format. Options: `mp3`, `wav` |
| pitch_change | number | 0 | Adjust pitch of AI vocals in semitones. Positive to increase, negative to decrease. |
| protect | number | 0.33 | Control how much of the original vocals' breath and voiceless consonants to leave. |
| rms_mix_rate | number | 0.25 | Control how much to use the original vocal's loudness (0) or a fixed loudness (1). |
| rvc_model | string | CUSTOM | Voice model to use. Options: `Obama`, `Trump`, `Sandy`, `Rogan`, `CUSTOM` |

## Examples

**Using a built-in model:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "rvc-v2",
    "version": "0.0.1",
    "input": {
      "input_audio": "https://example.com/singing.wav",
      "rvc_model": "Trump",
      "pitch_change": -2,
      "output_format": "mp3"
    }
  }'
```

**Using a custom model with fine-tuned settings:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "rvc-v2",
    "version": "0.0.1",
    "input": {
      "input_audio": "https://example.com/vocals.wav",
      "rvc_model": "CUSTOM",
      "custom_rvc_model_download_url": "https://example.com/my-trained-model.zip",
      "f0_method": "rmvpe",
      "index_rate": 0.7,
      "pitch_change": 3,
      "protect": 0.4,
      "rms_mix_rate": 0.3,
      "output_format": "wav"
    }
  }'
```

## Related Models

- [Train Rvc](../train-rvc/) - Train a custom RVC model from audio datasets
- [Realistic Voice Cloning](../realistic-voice-cloning/) - Clone voices from audio samples
- [ElevenLabs | Voice Changer](../elevenlabs-voice-changer/) - ElevenLabs voice changing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
