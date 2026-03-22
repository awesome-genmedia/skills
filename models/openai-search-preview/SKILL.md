---
name: openai-search-preview
description: "OpenAI Search Preview. Search the web and get AI-summarized answers using OpenAI Search. Real-time web search with AI-powered responses. Triggers: openai search, web search ai, search preview, ai search, real-time search, openai web search, search the web"
allowed-tools: Bash(curl *), WebFetch
---

# OpenAI Search Preview

Search the web and get AI-summarized answers using OpenAI Search Preview. Provide a query and optionally specify a geographic location for localized results. Returns structured, AI-processed search results.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-search-preview",
    "version": "0.0.1",
    "input": {
      "prompt": "What are the latest developments in AI video generation?",
      "search_context_size": "medium"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| city | string | - | City for localized search results |
| country_iso_code | string | - | ISO country code for localized results |
| prompt | string | What was a positive news story from today? | Search query |
| region | string | - | Region for localized search results |
| search_context_size | string | - | Amount of search context. Options: `low`, `medium`, `high` |

## Examples

**Search for tech news:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-search-preview",
    "version": "0.0.1",
    "input": {
      "prompt": "What are the top trending AI tools released this week?",
      "search_context_size": "high"
    }
  }'
```

**Localized search:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-search-preview",
    "version": "0.0.1",
    "input": {
      "prompt": "Best restaurants open tonight",
      "city": "San Francisco",
      "region": "California",
      "country_iso_code": "US",
      "search_context_size": "medium"
    }
  }'
```

## Related Models

- [ElevenLabs | Speech to Text](../elevenlabs-speech-to-text/) - Transcribe audio content
- [ElevenLabs | Text to Speech](../elevenlabs-text-to-speech/) - Convert search results to audio
- [Qwen Image](../qwen-image/) - Generate images from search findings

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
