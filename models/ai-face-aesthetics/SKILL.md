---
name: "AI Face Aesthetics"
description: "Apply facial aesthetic adjustments to face images. Trigger: Use when the user wants to adjust facial features, or requests 'face aesthetics', 'slim face', 'big eyes', 'face reshape', or 'facial enhancement'."
allowed-tools: ["Bash"]
---

# AI Face Aesthetics

Apply aesthetic adjustments to facial features in images. Supports a wide variety of shape types including face slimming, eye enlargement, nose adjustments, lip modifications, and more.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ai-face-aesthetics",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/face-photo.jpg",
      "shape_type": "slim_face",
      "strength": 0.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `image_url` | string | `false` | Upload your face image |
| `shape_type` | string | `slim_face` | Shape type. Options: `cheekbone`, `cut_face`, `slim_face`, `long_face`, `chin_shortening`, `chin_lengthening`, `slim_chin`, `slim_jaw`, `big_eyes`, `eye_angle_1`, `eye_distance`, `widen_eye_distance`, `eye_angle_2`, `eye_height`, `slim_nose`, `nose_wing`, `nose_length`, `nose_length_2`, `lip_width`, `lip_size`, `lip_height`, `human_middle` |
| `strength` | number | `0.5` | Strength of the effect to apply to the face |

## Output

- **Type:** image

## Examples

### Slim Face
```json
{
  "model": "ai-face-aesthetics",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/portrait.jpg",
    "shape_type": "slim_face",
    "strength": 0.6
  }
}
```

### Enlarge Eyes
```json
{
  "model": "ai-face-aesthetics",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/headshot.jpg",
    "shape_type": "big_eyes",
    "strength": 0.4
  }
}
```

### Slim Nose
```json
{
  "model": "ai-face-aesthetics",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/face-close-up.jpg",
    "shape_type": "slim_nose",
    "strength": 0.3
  }
}
```

## Related Models

- [Kling 1.5 Kolors Virtual Try On](../kling-v1-5-kolors-virtual-try-on/SKILL.md) - Virtual garment try-on
- [Remove Background Enhance](../rembg-enhance/SKILL.md) - Remove backgrounds
- [Luma Dream Machine Reframe Image](../reframe-image/SKILL.md) - Reframe and expand images

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
