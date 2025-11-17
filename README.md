# Selinia AI API Documentation

Build intelligent applications with our comprehensive AI assistant API. Access conversational chat, code generation, and text-to-speech capabilities powered by advanced language models.

## Table of Contents

- [Introduction](#introduction)
- [Getting Started](#getting-started)
- [Authentication](#authentication)
- [Rate Limits](#rate-limits)
- [Chat API](#chat-api)
- [Code Generation API](#code-generation-api)
- [Text-to-Speech API](#text-to-speech-api)
- [Resources](#resources)

## Introduction

The Selinia AI API provides developers with direct access to our intelligent assistant infrastructure. Powered by GPT-4o and ElevenLabs, Selinia can engage in natural conversations, generate production-ready code, and provide high-quality voice synthesis.

**Base URL:** `https://selinia.onrender.com`

### Features

- Natural language chat with context-aware responses
- Professional code generation (HTML/CSS/JavaScript)
- High-quality text-to-speech with ElevenLabs
- Dual-mode operation (Chat & Code)
- Conversation history support
- Low latency responses

## Getting Started

To get started with the Selinia AI API:

1. Review the documentation for your desired endpoints
2. Test the public endpoints without authentication
3. For production usage, configure your environment
4. Integrate the API into your application

### Quick Example

```bash
curl -X POST https://selinia.onrender.com/api/chat \
  -H "Content-Type: application/json" \
  -d '{
    "message": "Hello, who are you?",
    "conversationHistory": [],
    "mode": "chat"
  }'
```

## Authentication

Currently, all endpoints are public and don't require authentication for development purposes. For production deployments, you'll need to implement your own authentication layer.

### CORS Configuration

The API accepts requests from:
- `https://selinia.xyz`
- `https://www.selinia.xyz`
- `http://localhost:3000` (for development)

## Rate Limits

API rate limits help ensure fair usage:

| Environment | Requests per minute | Requirements |
|-------------|---------------------|--------------|
| Development | Unlimited | Localhost only |
| Production | As configured | Backend rate limiting |

## Chat API

### POST /api/chat

Engage in natural conversations with Selinia AI assistant.

**Request Body:**

```json
{
  "message": "What is your purpose?",
  "conversationHistory": [
    { "role": "user", "content": "Hello" },
    { "role": "assistant", "content": "Hi! How can I help you?" }
  ],
  "mode": "chat"
}
```

**Response:**

```json
{
  "response": "I'm Selinia, a friendly AI assistant created to help you...",
  "usage": {
    "prompt_tokens": 45,
    "completion_tokens": 120,
    "total_tokens": 165
  }
}
```

[**Full Chat API Documentation →**](./CHAT_API.md)

## Code Generation API

### POST /api/generate-code

Generate production-ready HTML, CSS, and JavaScript code.

**Request Body:**

```json
{
  "prompt": "Create a responsive navbar",
  "conversationHistory": [],
  "language": "html/css/javascript",
  "mode": "code"
}
```

**Response:**

```json
{
  "code": "```html\n<!DOCTYPE html>\n...\n```",
  "usage": {
    "prompt_tokens": 123,
    "completion_tokens": 890,
    "total_tokens": 1013
  }
}
```

[**Full Code Generation API Documentation →**](./CODE_API.md)

## Text-to-Speech API

### POST /api/tts

Convert text to high-quality speech using ElevenLabs.

**Request Body:**

```json
{
  "text": "Hello, I'm Selinia!"
}
```

**Response:**

```
Content-Type: audio/mpeg
<audio stream>
```

[**Full TTS API Documentation →**](./TTS_API.md)

## Error Responses

All endpoints may return error responses in the following format:

```json
{
  "error": "Message is required"
}
```

### HTTP Status Codes

| Status Code | Description |
|-------------|-------------|
| 200 | Success |
| 400 | Bad Request - Invalid parameters |
| 500 | Internal Server Error |

## Best Practices

1. Keep conversation history limited (last 10 exchanges recommended)
2. Handle errors gracefully and provide user feedback
3. Implement proper timeout handling
4. Cache responses when appropriate
5. Use streaming for long responses when available
6. Monitor token usage for cost optimization

## SDKs and Libraries

Coming soon! We're working on official SDKs for:
- JavaScript/TypeScript
- Python
- Go

## Resources

- **Website:** [https://selinia.xyz](https://selinia.xyz)
- **GitHub:** [https://github.com/SeliniaModel/Selinia-API](https://github.com/SeliniaModel/Selinia-API)
- **Twitter:** [https://x.com/SeliniaModel](https://x.com/SeliniaModel)
- **Health Check:** [https://selinia.onrender.com/health](https://selinia.onrender.com/health)

## Support

For support, questions, or feature requests:

- Open an issue on [GitHub](https://github.com/SeliniaModel/Selinia-API)
- Follow us on [Twitter](https://x.com/SeliniaModel)
- Visit our website at [selinia.xyz](https://selinia.xyz)

## Changelog

### v1.0.0 (2024-11-13)
- Initial release
- Chat API endpoint
- Code Generation API endpoint
- Text-to-Speech API endpoint
- CORS configuration for production
