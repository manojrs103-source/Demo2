# Fund Transfer API — Examples

> **Example only:** All data, identifiers, hosts, and responses in this page are fictional.

## Successful request

```http
POST /v1/transfers HTTP/1.1
Host: api.example.com
Authorization: Bearer <ACCESS_TOKEN>
Content-Type: application/json
Accept: application/json
```

```json
{
  "sourceAccount": "SOURCE-ACCOUNT-001",
  "destinationAccount": "DESTINATION-ACCOUNT-002",
  "amount": 500.00,
  "currency": "MYR",
  "description": "Example transfer"
}
```

## Example accepted response

```http
HTTP/1.1 201 Created
Content-Type: application/json
```

```json
{
  "transferId": "TRF-EXAMPLE-10001",
  "status": "PENDING",
  "amount": 500.00,
  "currency": "MYR",
  "message": "Transfer request accepted for processing"
}
```

## Example validation error

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json
```

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "The request contains an invalid field.",
    "details": [
      {
        "field": "amount",
        "reason": "The value must be greater than zero."
      }
    ],
    "correlationId": "CORR-EXAMPLE-001"
  }
}
```

## Testing notes

- Use only an approved sandbox and test credentials when validating a real API.
- Do not use real customer account details.
- Confirm every example against the current API implementation or an approved API specification.
- Do not infer that a `201 Created` response means funds have settled. Document the actual business meaning of each processing state.
