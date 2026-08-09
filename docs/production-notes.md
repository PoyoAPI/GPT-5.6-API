# GPT-5.6 API production notes

## Confirmed contract

- Endpoint: `POST /v1/responses`
- Model IDs: `gpt-5-6-luna`, `gpt-5-6-terra`, `gpt-5-6-sol`
- Authentication: `Authorization: Bearer <POYO_API_KEY>`

## Input limits

| Field | Requirement | Constraint |
| --- | --- | --- |
| model | required | gpt-5-6-luna, gpt-5-6-terra, or gpt-5-6-sol. |
| input | required | String or Responses-style input items. |
| instructions | optional | High-level system instructions. |
| max_output_tokens | optional | Maximum output tokens. |
| reasoning | optional | Reasoning configuration for supported variants. |
| stream | optional | Enable streaming. |

## Operational checklist

- Keep API keys in a server-side secret manager.
- Validate user input before calling the API.
- Apply request timeouts and retry only rate limits or transient 5xx responses.
- Bound output tokens and log usage for cost control.
- Redact sensitive prompt and response content from logs.
- Recheck the live model page before hard-coding prices.

## Failure handling

Treat non-2xx HTTP responses and non-success API `code` values as errors. Preserve the HTTP status, API code, request ID when present, and a redacted response body for debugging.

Schema: [PoYo API documentation](https://docs.poyo.ai/api-manual/chat-series/responses)

