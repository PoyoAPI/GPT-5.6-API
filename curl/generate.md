# GPT-5.6 API: cURL quickstart

Call `/v1/responses` with model `gpt-5-6-luna`:

```bash
export POYO_API_KEY="your-api-key"
export POYO_BASE_URL="https://api.poyo.ai"

curl -X POST "$POYO_BASE_URL/v1/responses" \
  -H "Authorization: Bearer $POYO_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
  "model": "gpt-5-6-luna",
  "instructions": "Answer as a concise senior backend engineer.",
  "input": "Explain how to make webhook processing idempotent.",
  "max_output_tokens": 700
}'
```

Keep the API key on your server. Add timeouts, bounded retries, and usage logging before production.

See the [full README](../README.md) and [production notes](../docs/production-notes.md).

