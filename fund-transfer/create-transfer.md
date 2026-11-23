# Create Transfer

> **Example only:** This API operation is fictional and is not a real banking endpoint.

## Overview

Creates a transfer request between a source account and a destination account. The example response uses a `PENDING` state to illustrate an accepted processing outcome. A real API's processing semantics must be confirmed with its API owner.

## Endpoint

```http
POST https://api.example.com/v1/transfers
```

## Authentication

Send an access token using the HTTP Bearer authentication scheme.

```http
Authorization: Bearer <ACCESS_TOKEN>
```

Use a placeholder only. Never publish a real access token.

## Request headers

| Header | Required | Description |
|---|---:|---|
| `Authorization` | Yes | Bearer access token. |
| `Content-Type` | Yes | Set to `application/json`. |
| `Accept` | Recommended | Set to `application/json`. |

## Request body

Example:

```json
{
  "sourceAccount": "SOURCE-ACCOUNT-001",
  "destinationAccount": "DESTINATION-ACCOUNT-002",
  "amount": 500.00,
  "currency": "MYR",
  "description": "Example transfer"
}
```

All account references above are fictional placeholders and must not be interpreted as real account numbers.

## Request fields

| Field | Type | Required in this example | Description |
|---|---|---:|---|
| `sourceAccount` | string | Yes | Identifier of the account from which funds are to be transferred. |
| `destinationAccount` | string | Yes | Identifier of the receiving account. |
| `amount` | number | Yes | Amount requested for transfer. |
| `currency` | string | Yes | Three-letter currency code. This example uses `MYR`. |
| `description` | string | No | Optional human-readable transfer description. |

The requiredness and constraints in this table are assumptions for this fictional example, not verified business rules.

## Example success response

Illustrative status: `201 Created`

```json
{
  "transferId": "TRF-EXAMPLE-10001",
  "status": "PENDING",
  "amount": 500.00,
  "currency": "MYR",
  "message": "Transfer request accepted for processing"
}
```

## Response fields

| Field | Type | Description |
|---|---|---|
| `transferId` | string | Example identifier assigned to the transfer request. |
| `status` | string | Example processing state. |
| `amount` | number | Requested transfer amount. |
| `currency` | string | Currency code associated with the amount. |
| `message` | string | Human-readable result message. |

## cURL example

```bash
curl --request POST \
  --url https://api.example.com/v1/transfers \
  --header "Authorization: Bearer <ACCESS_TOKEN>" \
  --header "Content-Type: application/json" \
  --header "Accept: application/json" \
  --data '{
    "sourceAccount": "SOURCE-ACCOUNT-001",
    "destinationAccount": "DESTINATION-ACCOUNT-002",
    "amount": 500.00,
    "currency": "MYR",
    "description": "Example transfer"
  }'
```

## Validation checklist before using this pattern for a real API

- Confirm the endpoint, method, and base URL with the API owner.
- Confirm field names, data types, requiredness, formats, and length constraints.
- Confirm authentication and authorisation requirements.
- Confirm whether an idempotency key is required.
- Confirm response status codes, response schema, and processing states.
- Test examples in an approved non-production environment.
- Obtain technical and security review before publication.
