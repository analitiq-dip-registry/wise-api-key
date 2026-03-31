---
name: Wise
description: >
  API connector for Wise (formerly TransferWise) international money transfer and multi-currency account platform
type: api
---

# Wise

International money transfer and multi-currency account platform (formerly TransferWise). Provides access to profiles, transfers, balances, exchange rates, and recipient data via a REST API.

## Authentication

### API Key (Deprecated Personal Token)
- Client app required: no
- Header format: `Authorization: Bearer ${api_key}`
- Deprecation note: Wise has published a migration guide from personal API tokens to OAuth2 + mTLS. Personal tokens will be deprecated after successful migration (no fixed absolute date). Tokens still work as of today.

## Post-Auth Steps

After authentication, the user must select a profile:

1. **Select Profile** -- Call `GET /v2/profiles` to list available personal and business profiles. The selected `profile_id` (from the `id` field) is required by most subsequent API endpoints.

## Available Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/v1/profiles` | GET | List user profiles (personal and/or business) |
| `/v1/transfers` | GET | List transfers for a profile |
| `/v1/accounts` | GET | List recipient (beneficiary) accounts for a profile |

## Rate Limits

- 1000 requests per 60 seconds

## Caveats

- The personal API token auth method is deprecated. Wise is migrating to OAuth2 + mTLS. Tokens continue to work but may be disabled in the future.
- Most API endpoints require a `profile_id` parameter, which is obtained via the post-auth step.
- Sandbox environment available at `https://api.wise-sandbox.com` for testing.
