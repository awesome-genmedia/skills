---
name: openai-chat-completion
description: "OpenAI Chat Completion. Run OpenAI chat models including GPT-4o, GPT-5, and o3-mini. Triggers: chat, gpt, openai, text generation, llm, completion"
allowed-tools: Bash(curl *), WebFetch
---

# OpenAI Chat Completion

Run OpenAI chat completion models through each::labs. Supports multiple model variants including GPT-4o, GPT-5, and o3-mini with optional image input and system prompts.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-chat-completion",
    "version": "0.0.1",
    "input": {
      "model": "gpt-4o",
      "user_prompt": "Explain quantum computing in simple terms",
      "system_prompt": "You are a helpful science teacher"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | | Optional image URL for multimodal input. |
| max_tokens | integer | | Maximum number of tokens in the response. |
| model | string | gpt-4o | Model to use. enum: gpt-4.1, gpt-4.1-mini, gpt-4.1-nano, gpt-4o-mini, gpt-4o, gpt-5.1, gpt-5, gpt-5-mini, gpt-5-nano, o3-mini |
| system_prompt | string | | System prompt to set the model's behavior. |
| user_prompt | string | | The user's message to the model. |

## Examples

**Vision-enabled query:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-chat-completion",
    "version": "0.0.1",
    "input": {
      "model": "gpt-4o",
      "user_prompt": "Describe what you see in this image and identify the main objects",
      "image_url": "https://example.com/photo.jpg",
      "max_tokens": 500
    }
  }'
```

**Reasoning with o3-mini:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-chat-completion",
    "version": "0.0.1",
    "input": {
      "model": "o3-mini",
      "user_prompt": "Solve this step by step: If a train travels at 60mph for 2.5 hours, then at 80mph for 1.5 hours, what is the total distance?",
      "system_prompt": "Show your work step by step"
    }
  }'
```

## Related Models

- [OpenAI ChatGPT](../openai-chatgpt-5/) - Alternative OpenAI chat model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
