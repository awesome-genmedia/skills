---
name: train-rvc
description: "Train Rvc. Train a custom RVC voice model from audio datasets. Triggers: voice training, rvc train, voice model, custom voice, voice cloning"
allowed-tools: Bash(curl *), WebFetch
---

# Train Rvc

Train a custom RVC (Retrieval-based Voice Conversion) model from an audio dataset. Upload a zip file containing audio splits and configure training parameters like batch size, epochs, and pitch detection method.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "train-rvc",
    "version": "0.0.1",
    "input": {
      "dataset_zip": "https://example.com/voice-dataset.zip",
      "epoch": 10,
      "batch_size": "7",
      "sample_rate": "48k",
      "f0method": "rmvpe_gpu",
      "version": "v2"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| batch_size | string | 7 | Batch size for training. |
| dataset_zip | string | - | Upload dataset zip. Zip should contain `dataset/<rvc_name>/split_<i>.wav`. |
| epoch | integer | 10 | Number of training epochs. |
| f0method | string | rmvpe_gpu | Pitch detection method. Options: `pm`, `dio`, `harvest`, `rmvpe`, `rmvpe_gpu` |
| sample_rate | string | 48k | Audio sample rate. Options: `40k`, `48k` |
| version | string | v2 | Model version. Options: `v1`, `v2` |

## Examples

**Basic training with defaults:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "train-rvc",
    "version": "0.0.1",
    "input": {
      "dataset_zip": "https://example.com/my-voice-samples.zip",
      "epoch": 15
    }
  }'
```

**Extended training with specific settings:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "train-rvc",
    "version": "0.0.1",
    "input": {
      "dataset_zip": "https://example.com/singer-dataset.zip",
      "epoch": 25,
      "batch_size": "12",
      "sample_rate": "48k",
      "f0method": "harvest",
      "version": "v2"
    }
  }'
```

## Related Models

- [Rvc v2](../rvc-v2/) - Use a trained RVC model for voice conversion
- [Realistic Voice Cloning](../realistic-voice-cloning/) - Clone voices from audio samples

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
