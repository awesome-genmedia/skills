---
name: openai-chatgpt-5
description: "OpenAI ChatGPT. Run ChatGPT models with vision support. Triggers: chat, chatgpt, openai, text generation, llm, gpt"
allowed-tools: Bash(curl *), WebFetch
---

# OpenAI ChatGPT

Run OpenAI ChatGPT through each::labs with optional image input and system prompt for multimodal conversations.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-chatgpt-5",
    "version": "0.0.1",
    "input": {
      "user_prompt": "Write a short poem about the ocean",
      "system_prompt": "You are a creative poet"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | | Optional image URL for multimodal input. |
| max_output_tokens | integer | | Maximum number of tokens in the response. |
| system_prompt | string | | System prompt to set the model's behavior. |
| user_prompt | string | | The user's message to the model. |

## Examples

**Image analysis:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-chatgpt-5",
    "version": "0.0.1",
    "input": {
      "user_prompt": "What ingredients can you identify in this dish?",
      "image_url": "https://example.com/food.jpg",
      "max_output_tokens": 300
    }
  }'
```

**Code generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-chatgpt-5",
    "version": "0.0.1",
    "input": {
      "user_prompt": "Write a Python function that finds the longest palindrome in a string",
      "system_prompt": "You are an expert Python programmer. Write clean, efficient code with comments.",
      "max_output_tokens": 1000
    }
  }'
```

## Related Models

- [OpenAI Chat Completion](../openai-chat-completion/) - OpenAI completion with model selection

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
