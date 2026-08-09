# GPT-5.6 API: runnable cURL and Node.js examples

[![PoYo model page](https://img.shields.io/badge/Try%20on%20PoYo-gpt--5--6--api-84cc16)](https://poyo.ai/models/gpt-5-6) [![API docs](https://img.shields.io/badge/API-docs-22d3ee)](https://docs.poyo.ai/api-manual/chat-series/responses) [![Check](https://github.com/PoyoAPI/gpt-5-6-api/actions/workflows/check.yml/badge.svg)](https://github.com/PoyoAPI/gpt-5-6-api/actions/workflows/check.yml)

Call GPT-5.6 Luna, Terra, or Sol through PoYo's Responses-compatible API with exact model IDs and a minimal Node.js example.

**Answer:** To use the GPT-5.6 API, send a server-side request to `POST https://api.poyo.ai/v1/responses` with model `gpt-5-6-luna`, `gpt-5-6-terra`, `gpt-5-6-sol` and a PoYo API key. The examples in this repository are runnable with Node.js 22+ or cURL.

Last verified against the live PoYo schema and pricing on **August 9, 2026**.

## Quickstart

1. Create a key in the [PoYo dashboard](https://poyo.ai/dashboard/api-key).
2. Copy `.env.example` to `.env` and replace the placeholder.
3. Run `node node/index.mjs`.

```dotenv
POYO_API_KEY=YOUR_POYO_API_KEY_HERE
POYO_BASE_URL=https://api.poyo.ai
```

The complete cURL request is in [curl/generate.md](curl/generate.md). The Node.js example prints the complete JSON response.

## Model IDs

- `gpt-5-6-luna`
- `gpt-5-6-terra`
- `gpt-5-6-sol`

Use the exact IDs above. Product names and API model IDs are not always identical.

## Request fields

| Field | Requirement | Meaning |
| --- | --- | --- |
| model | required | gpt-5-6-luna, gpt-5-6-terra, or gpt-5-6-sol. |
| input | required | String or Responses-style input items. |
| instructions | optional | High-level system instructions. |
| max_output_tokens | optional | Maximum output tokens. |
| reasoning | optional | Reasoning configuration for supported variants. |
| stream | optional | Enable streaming. |

## Pricing snapshot

| Usage | Price |
| --- | --- |
| GPT-5.6 Luna input | $0.056 per 1M tokens |
| GPT-5.6 Luna output | $0.336 per 1M tokens |
| GPT-5.6 Terra input | $0.56 per 1M tokens |
| GPT-5.6 Terra output | $3.36 per 1M tokens |
| GPT-5.6 Sol input | $1.40 per 1M tokens |
| GPT-5.6 Sol output | $8.40 per 1M tokens |

Pricing can change. Confirm the current amount on the [model page](https://poyo.ai/models/gpt-5-6) before a production rollout.

## Best for

- high-volume assistants
- reasoning and coding
- tool-using agents

## Important behavior

- There is no generic gpt-5-6 alias in this integration; choose Luna, Terra, or Sol explicitly.
- Start with Luna for low-cost workloads, Terra for balanced reasoning, and Sol for the highest-capability tier.
- Read generated text from the response output items or use your SDK's output-text helper.

## Production guidance

Set an application timeout, retry only transient failures, cap output size, and record token usage. Do not put `POYO_API_KEY` in browser or mobile client code.

## Repository map

- [`curl/generate.md`](curl/generate.md) — copy-paste request
- [`node/index.mjs`](node/index.mjs) — dependency-free Node.js example
- [`docs/production-notes.md`](docs/production-notes.md) — limits and rollout checklist

## Links

- [Try GPT-5.6 API on PoYo](https://poyo.ai/models/gpt-5-6)
- [API reference](https://docs.poyo.ai/api-manual/chat-series/responses)
- [All PoYo examples](https://github.com/PoyoAPI/poyo-examples)
- [PoYo model catalog](https://poyo.ai/models)

## License

MIT

