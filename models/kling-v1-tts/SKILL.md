---
name: "Kling V1 Text to Speech"
description: "Convert text to speech using Kling V1 TTS with multiple voice options. Trigger: Use when the user wants to generate speech audio from text, or requests 'kling tts', 'text to speech', or 'generate voice from text'."
allowed-tools: ["Bash"]
---

# Kling V1 | Text to Speech

Convert text into natural-sounding speech with a wide selection of voice styles. Supports multiple character voices and adjustable speech rate.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-tts",
    "version": "0.0.1",
    "input": {
      "text": "Hello, welcome to our product demonstration.",
      "voice_id": "oversea_male1",
      "voice_speed": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `text` | string | (empty) | The text to be converted to speech. Max 120 characters |
| `voice_id` | string | `genshin_vindi2` | The voice ID for speech synthesis. Options: `genshin_vindi2`, `zhinen_xuesheng`, `AOT`, `ai_shatang`, `genshin_klee2`, `genshin_kirara`, `ai_kaiya`, `oversea_male1`, `ai_chenjiahao_712`, `girlfriend_4_speech02`, `chat1_female_new-3`, `chat_0407_5-1`, `cartoon-boy-07`, `uk_boy1`, `cartoon-girl-01`, `PeppaPig_platform`, `ai_huangzhong_712`, `ai_huangyaoshi_712`, `ai_laoguowang_712`, `chengshu_jiejie`, `you_pingjing`, `calm_story1`, `uk_man2`, `laopopo_speech02`, `heainainai_speech02`, `reader_en_m-v1`, `commercial_lady_en_f-v1`, `tiyuxi_xuedi`, `tiexin_nanyou`, `girlfriend_1_speech02`, `girlfriend_2_speech02`, `zhuxi_speech02`, `uk_oldman3`, `dongbeilaotie_speech02`, `chongqingxiaohuo_speech02`, `chuanmeizi_speech02`, `chaoshandashu_speech02`, `ai_taiwan_man2_speech02`, `xianzhanggui_speech02`, `tianjinjiejie_speech02`, `diyinnansang_DB_CN_M_04-v2`, `yizhipiannan-v1`, `guanxiaofang-v2`, `tianmeixuemei-v1`, `daopianyansang-v1`, `mengwa-v1` |
| `voice_speed` | number | `1` | Rate of speech |

## Output

- **Type:** audio

## Examples

### English Male Narration
```json
{
  "model": "kling-v1-tts",
  "version": "0.0.1",
  "input": {
    "text": "Welcome to today's product overview.",
    "voice_id": "oversea_male1",
    "voice_speed": 0.9
  }
}
```

### Female Commercial Voice
```json
{
  "model": "kling-v1-tts",
  "version": "0.0.1",
  "input": {
    "text": "Discover the future of AI technology.",
    "voice_id": "commercial_lady_en_f-v1",
    "voice_speed": 1
  }
}
```

### Character Voice
```json
{
  "model": "kling-v1-tts",
  "version": "0.0.1",
  "input": {
    "text": "Let me tell you a wonderful story!",
    "voice_id": "genshin_klee2",
    "voice_speed": 1.1
  }
}
```

## Related Models

- [ElevenLabs Voice Clone](../elevenlabs-voice-clone/SKILL.md) - Clone and generate custom voices
- [Kling V1 Pro AI Avatar](../kling-v1-pro-ai-avatar/SKILL.md) - Combine generated speech with avatar video

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
