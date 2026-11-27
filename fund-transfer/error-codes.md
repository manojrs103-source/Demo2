# Fund Transfer API — Error Handling

> **Example only:** The status-code mapping and response body below are illustrative. A real API may use different status codes, error identifiers, and response schemas.

## HTTP status codes

| HTTP status | Example meaning | Suggested client action |
|---|---|---|
| `400 Bad Request` | Request syntax or validation failed. | Check the request fields and correct the invalid input. |
| `401 Unauthorized` | Authentication is missing or invalid. | Obtain a valid access token and retry according to the authentication flow. |
| `403 Forbidden` | The caller is authenticated but lacks permission. | Request the required permission from the service administrator. |
| `404 Not Found` | The requested resource does not exist or is unavailable. | Verify the resource identifier and endpoint. |
| `409 Conflict` | The request conflicts with the current resource state or a duplicate operation. | Check the resource state and the API's idempotency guidance. |
| `415 Unsupported Media Type` | The request uses an unsupported content type. | Send the content type documented by the API. |
| `429 Too Many Requests` | The caller exceeded a rate limit. | Respect any `Retry-After` guidance and apply backoff. |
| `500 Internal Server Error` | The service encountered an unexpected error. | Retry only when safe and according to the API's retry guidance; contact support with a correlation identifier if available. |
| `503 Service Unavailable` | The service is temporarily unavailable. | Retry according to the service's backoff and retry policy. |

## Example error response

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

The error structure and identifiers are illustrative and must not be assumed to match any real service.

## Error documentation checklist

For every documented error, confirm:

- HTTP status code.
- Stable machine-readable error code.
- Human-readable message.
- Field-level details, if applicable.
- Whether the client may retry.
- Whether the operation could already have been processed.
- Support or correlation identifier guidance.
- Any security considerations that affect the error message.

## Safe retry guidance

Do not advise clients to blindly retry a transfer request. A timeout can occur after the server has accepted or processed a request. The API owner must document the supported idempotency mechanism and the correct way to check the transfer status before a retry.
