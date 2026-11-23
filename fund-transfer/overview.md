# Fund Transfer API — Overview

> **Example only:** This document describes a fictional API for learning and portfolio demonstration. It does not describe an actual Maybank service.

## Purpose

The Fund Transfer API example illustrates how an application could submit a request to transfer a specified amount from a source account to a destination account.

## Intended audience

- Application developers
- Integration engineers
- QA engineers
- Technical support teams

## Example workflow

1. The client application obtains an access token from its authorised identity provider.
2. The client submits a transfer request.
3. The API validates the request and applicable business rules.
4. The API returns a transfer identifier and processing status, or an error response.

## Base URL

```text
https://api.example.com
```

The hostname is reserved for examples. Replace it only when documenting an approved service.

## API operation

| Operation | Method | Path | Purpose |
|---|---|---|---|
| Create transfer | POST | `/v1/transfers` | Submit a transfer request |

## Authentication

The illustrative operation uses an HTTP Bearer access token.

Do not include real tokens in documentation, examples, screenshots, source control, or support tickets.

## Important implementation notes

The actual API owner must confirm authentication, authorisation, idempotency, transfer limits, currency support, account validation, processing states, and error semantics before this example is adapted for a real service.
