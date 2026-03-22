# awesome-genmedia/skills

> 562 generative media skills for AI agents, powered by [each::labs](https://eachlabs.ai).

Generate images, videos, audio, 3D models, and more using 431 AI models through a single API. Install as a Claude Code plugin and get instant access to every skill.

## Install

```bash
# Claude Code plugin
/plugin install awesome-genmedia

# Or add individual skills
npx skills add awesome-genmedia/skills@image-generation
npx skills add awesome-genmedia/skills@flux-2-max
npx skills add awesome-genmedia/skills@logo-design
```

## Setup

1. Sign up at [eachlabs.ai](https://eachlabs.ai)
2. Get your API key from Settings
3. Set environment variable:
   ```bash
   export EACHLABS_API_KEY="your-api-key"
   ```

## Quick Example

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a professional headshot, studio lighting, neutral background"}],
    "stream": false
  }'
```

## Default Skills (14)

Core generative media capabilities at the root level:

| Skill | Description |
|-------|-------------|
| [image-generation](image-generation/SKILL.md) | Generate images from text |
| [image-editing](image-editing/SKILL.md) | Edit images with natural language |
| [image-upscaling](image-upscaling/SKILL.md) | Enhance image resolution |
| [background-removal](background-removal/SKILL.md) | Remove image backgrounds |
| [face-swap](face-swap/SKILL.md) | Swap faces between photos |
| [video-generation](video-generation/SKILL.md) | Generate videos from text or images |
| [video-editing](video-editing/SKILL.md) | Edit videos with AI |
| [song-generation](song-generation/SKILL.md) | Generate songs with vocals |
| [music-generation](music-generation/SKILL.md) | Generate instrumental music |
| [lyrics-generation](lyrics-generation/SKILL.md) | Generate song lyrics |
| [voice-generation](voice-generation/SKILL.md) | Generate human-like voice audio |
| [text-to-speech](text-to-speech/SKILL.md) | Convert text to speech |
| [speech-to-text](speech-to-text/SKILL.md) | Transcribe audio to text |
| [sound-effects](sound-effects/SKILL.md) | Generate custom sound effects |

## Categories (117 skills)

Use-case specific skills organized by domain:

| Domain | Skills | Examples |
|--------|--------|----------|
| [Image](categories/image/) | 15 | Headshots, avatars, QR codes, patterns, tattoos |
| [Video](categories/video/) | 10 | Text/image-to-video, music videos, trailers, loops |
| [Audio](categories/audio/) | 6 | TTS, music, sound effects, voiceover, jingles |
| [Design](categories/design/) | 14 | Logos, thumbnails, posters, business cards, packaging |
| [Face & Portrait](categories/face-portrait/) | 7 | Face swap, aging, beauty, caricature, makeup |
| [Social Media](categories/social-media/) | 6 | Instagram, TikTok, Twitter, LinkedIn, Pinterest, YouTube |
| [E-commerce](categories/ecommerce/) | 5 | Product photos, mockups, lifestyle, video ads |
| [Marketing](categories/marketing/) | 5 | Ad creatives, brand kits, landing pages, campaigns |
| [Gaming](categories/gaming/) | 6 | Game assets, characters, environments, sprites, UI |
| [Fashion](categories/fashion/) | 5 | Fashion models, outfits, try-on, fabric patterns |
| [Real Estate](categories/real-estate/) | 5 | Virtual staging, interior design, floor plans |
| [Photography](categories/photography/) | 5 | Restoration, colorization, stock photos, HDR |
| [3D & AR](categories/3d-ar/) | 4 | 3D models, textures, image-to-3D, AR filters |
| [NFT & Art](categories/nft-art/) | 4 | NFT collections, pixel art, generative art |
| [Education](categories/education/) | 4 | Diagrams, flashcards, educational videos |
| [Architecture](categories/architecture/) | 3 | Building visualization, landscape, renders |
| [Food & Beverage](categories/food-beverage/) | 3 | Food photography, recipe visuals, menus |
| [Automotive](categories/automotive/) | 3 | Car configurator, vehicle wraps, auto ads |
| [NSFW](categories/nsfw/) | 2 | Adult image and video generation |
| [Workflows](categories/workflows/) | 5 | Multi-model pipelines and batch processing |

## Models (431)

Every AI model available on each::labs has its own skill under [`models/`](models/):

### Image Generation
`flux-2-max` · `flux-2-pro` · `flux-2` · `flux-kontext-pro` · `flux-kontext-max` · `nano-banana-pro` · `nano-banana-2-text-to-image` · `gemini-3-pro-image-preview` · `imagen-4-fast` · `imagen4-preview` · `bytedance-seedream-v4-5-text-to-image` · `bytedance-seedream-v5-lite-text-to-image` · `kling-v3-text-to-image` · `gpt-image-v1-5-text-to-image` · `xai-grok-imagine-text-to-image` · `reve-text-to-image` · `ideogram-v3-turbo` · `stable-diffusion-3-5-large` · [and more...](models/)

### Video Generation
`veo-3` · `veo3-1-text-to-video` · `veo3-1-text-to-video-fast` · `kling-o3-pro-text-to-video` · `kling-v3-pro-text-to-video` · `sora-2-text-to-video-pro` · `pixverse-v5-6-text-to-video` · `wan-v2-6-text-to-video` · `runway-gen4-aleph` · `pika-v2-2-text-to-video` · `seedance-v1-5-pro-text-to-video` · `minimax-hailuo-v2-3-pro-text-to-video` · [and more...](models/)

### Image Editing
`flux-2-edit` · `flux-2-max-edit` · `flux-fill-pro` · `eachlabs-bg-remover-v1` · `topaz-upscale-image` · `kling-face-swap` · `nano-banana-pro-edit` · `qwen-ai-image-edit` · `firered-image-edit-v1-1` · [and more...](models/)

### Audio & Music
`elevenlabs-text-to-speech` · `mureka-generate-song` · `mureka-generate-instrumental` · `mureka-generate-lyrics` · `stable-audio-2-5-text-to-audio` · `xai-grok-tts-text-to-speech` · `google-text-to-speech` · `deepgram-nova-3-speech-to-text` · `whisper` · [and more...](models/)

### Video Editing & Effects
`topaz-upscale-video` · `auto-subtitle` · `heygen-video-translate` · `pixverse-lip-sync` · `merge-videos` · `ffmpeg-api-merge-audio-video` · [and more...](models/)

### Talking Head & Avatar
`bytedance-omnihuman-v1-5` · `bytedance-dreamactor-v2` · `kling-avatar-v2-pro` · `sync-lipsync-v2-pro` · `infinitalk-image-to-video` · [and more...](models/)

[Browse all 431 models →](models/)

## API

### each::sense (for use-case skills)

OpenAI-compatible endpoint that auto-selects the best model:

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

response = client.chat.completions.create(
    model="eachsense/beta",
    messages=[{"role": "user", "content": "Generate a logo for a coffee brand"}]
)
```

### Prediction API (for specific models)

Direct model access:

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-max",
    "version": "0.0.1",
    "input": {
      "prompt": "A professional headshot, studio lighting",
      "aspect_ratio": "1:1"
    }
  }'
```

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [API Reference](https://docs.eachlabs.ai/api/overview)
- [Models Directory](https://docs.eachlabs.ai/models/overview)
- [Workflows](https://docs.eachlabs.ai/workflows/overview)

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

[MIT](LICENSE)
