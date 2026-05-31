# paperlesser

[![GitHub Stars](https://img.shields.io/github/stars/arturict/paperlesser)](https://github.com/arturict/paperlesser)
[![GitHub License](https://img.shields.io/github/license/arturict/paperlesser)](LICENSE)

`paperlesser` is a modernized fork of an older Paperless-ngx AI filing project, focused on cleaner filing workflows, current model selection, and a much better admin UI.

## What changed

- Clean provider and model selection
- OpenRouter first-class support with curated small-model presets
- Custom OpenRouter model slugs
- Local or remote Ollama with model discovery from the instance
- OpenAI-compatible API support for LM Studio, LiteLLM, vLLM, FastChat, and similar gateways
- Prompt editing removed from the UI
- Chat, RAG chat, and playground removed from the main product flow
- Improved dashboard, darker dark mode, and cleaner manual review
- Semantic versioning independent from upstream

## Recommended default

- Provider: `OpenRouter`
- Model: `openai/gpt-5.4-nano`

Other curated OpenRouter presets included by default:

- `openai/gpt-5.4-mini`
- `anthropic/claude-haiku-4.5`
- `google/gemini-3.1-flash-lite`
- `google/gemini-3-flash-preview`
- `minimax/minimax-m2.7`
- `google/gemma-4-31b-it`
- `qwen/qwen3.5-flash-02-23`
- `moonshotai/kimi-k2.6`

## Running with Docker

Use the included compose file as a starting point:

```bash
docker compose up -d
```

Default image reference in `docker-compose.yml`:

```yaml
image: ghcr.io/arturict/paperlesser:latest
```

## Upgrading from older Paperless-AI installs

1. Stop the old container.
2. Point your deployment to `ghcr.io/arturict/paperlesser:latest` or a tagged `4.x.y` release.
3. Keep your existing `/app/data` volume mounted.
4. Start the new container.
5. Open `/settings` and re-save your provider configuration once, especially if you want to move to OpenRouter.

## Publishing your own build

The GitHub workflows are already updated for `paperlesser` image names.

To publish from your fork, set these repository secrets:

- `DOCKER_USERNAME`
- `DOCKER_PASSWORD`
- `GHCR_PAT`

Then either:

- create a GitHub release for semver tags, or
- run the manual Docker workflow

## Development

```bash
npm install
npm run test
```

## Notes

- GPT-5 family models are kept on low reasoning effort by default.
- Token limit and custom prompt controls were intentionally removed from the UI.
- Manual review now supports editing title, tags, correspondent, document type, and owner assignment when available in Paperless.
