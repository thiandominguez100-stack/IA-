# NEXUS AI

NEXUS AI is a multi-provider group chat where a human moderator can direct a conversation among real models from OpenAI, Anthropic, Google, xAI and DeepSeek.

## Current status

Initial scaffold. The web interface and orchestration API are being built. Real model responses require provider API keys; no model is simulated.

## Requirements

- Node.js 20+
- API keys for whichever providers you enable

## Run locally

1. Copy `.env.example` to `.env`.
2. Add API keys for the providers you want to use.
3. Run `npm install`.
4. Run `npm start`.
5. Open http://localhost:3000.

Never put API keys in frontend code or commit your `.env` file.

## Providers

- OpenAI: Responses API
- Anthropic: Messages API
- Google: Gemini generateContent API
- xAI: OpenAI-compatible chat completions endpoint
- DeepSeek: OpenAI-compatible chat completions endpoint

Model IDs are configurable through environment variables because availability and names can change.

## Safety and cost controls

NEXUS sends only the conversation context needed for each turn. Configure a maximum number of rounds and output tokens. Provider billing and rate limits still apply. A local turn cap is not a spending guarantee; set provider-side budgets and alerts too.

## Architecture

- `server.js`: backend, provider adapters, round-robin orchestration and server-side key handling.
- `public/index.html`: moderator chat interface.
- `.env.example`: configuration template.
