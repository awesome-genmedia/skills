---
name: realistic-voice-cloning
description: "Voice Changer | RVC Voice Cloning and Changing. Change vocals in songs using RVC models with pitch control and reverb effects. Triggers: voice changer, voice cloning, rvc, voice swap, song voice change"
allowed-tools: Bash(curl *), WebFetch
---

# Voice Changer

Change vocals in songs using RVC (Retrieval-based Voice Conversion) models. Swap vocals with preset character voices or custom models, with pitch control, reverb, and volume adjustments.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realistic-voice-cloning",
    "version": "0.0.1",
    "input": {
      "song_input": "https://example.com/song.mp3",
      "rvc_model": "Drake",
      "pitch_change": "no-change",
      "output_format": "mp3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| backup_vocals_volume_change | number | 0 | Adjustment of backup vocals volume |
| crepe_hop_length | integer | 128 | Step size for pitch detection using CREPE |
| custom_rvc_model_download_url | string | - | URL to download a custom RVC model |
| filter_radius | integer | 3 | Range of frequencies affected by filter |
| index_rate | number | 0.5 | Frequency of indexing |
| instrumental_volume_change | number | 0 | Change in instrumental volume |
| main_vocals_volume_change | number | 0 | Adjustment of main vocals volume |
| output_format | string | mp3 | Output format. enum: mp3, wav |
| pitch_change | string | no-change | Pitch alteration. enum: no-change, male-to-female, female-to-male |
| pitch_change_all | number | 0 | Pitch modification for all elements |
| pitch_detection_algorithm | string | rmvpe | Pitch detection method. enum: rmvpe, mangio-crepe |
| protect | number | 0.33 | Safety for original audio |
| reverb_damping | number | 0.7 | Reduction of high frequencies in reverb |
| reverb_dryness | number | 0.8 | Amount of direct sound (dry signal) |
| reverb_size | number | 0.15 | Perceived size of reverb effect |
| reverb_wetness | number | 0.2 | Amount of reverb applied (wet signal) |
| rms_mix_rate | number | 0.25 | Ratio of RMS levels for mixing |
| rvc_model | string | Squidward | RVC model. enum: Squidward, MrKrabs, Plankton, Drake, Vader, Trump, Biden, Obama, Guitar, Voilin, CUSTOM |
| song_input | string | - | Original song file |

## Examples

**Voice change with pitch adjustment:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realistic-voice-cloning",
    "version": "0.0.1",
    "input": {
      "song_input": "https://example.com/pop-song.mp3",
      "rvc_model": "Obama",
      "pitch_change": "male-to-female",
      "reverb_size": 0.2,
      "reverb_wetness": 0.3,
      "output_format": "wav"
    }
  }'
```

**Custom RVC model with effects:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realistic-voice-cloning",
    "version": "0.0.1",
    "input": {
      "song_input": "https://example.com/karaoke.mp3",
      "rvc_model": "CUSTOM",
      "custom_rvc_model_download_url": "https://example.com/my-rvc-model.zip",
      "pitch_change": "no-change",
      "index_rate": 0.7,
      "main_vocals_volume_change": 2,
      "instrumental_volume_change": -1,
      "output_format": "mp3"
    }
  }'
```

## Related Models

- [openvoice](../openvoice/) - Voice cloning with language support
- [xtts-v2](../xtts-v2/) - Text-to-speech with voice cloning
- [incredibly-fast-whisper](../incredibly-fast-whisper/) - Audio transcription

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
