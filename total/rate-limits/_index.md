---
title: "Rate Limits"
type: docs
url: /rate-limits/
weight: 1
---

This page provides information about Aspose.Cloud API rate limits.

## Overview

Aspose.Cloud implements rate limiting to ensure the stability and availability of our services. Rate limits specify the maximum number of requests a client can make to our API within a given time period.

## Current Rate Limits

Currently, rate limits are applied to the following endpoint:

| Endpoint | Method | Rate Limit | Cooldown Period |
|----------|--------|------------|-----------------|
| `/connect/token` | POST | 5 failed requests | 10 minutes (600 seconds) |

## Rate Limiter Behavior

Our rate limiting system works as follows:

- Rate limits are based on client credentials (`client_id` and `client_secret` combination), not IP addresses
- When a request to `/connect/token` returns a 400 status code (indicating invalid credentials), a counter for that specific credential pair is incremented
- Once a credential pair exceeds 5 failed requests, subsequent requests from those credentials will receive an HTTP 429 (Too Many Requests) response with a `Retry-After: 600` header
- The cooldown period for rate-limited credentials is 10 minutes (600 seconds)
- If a user changes either their `client_id` or `client_secret`, they will be unbanned immediately as this creates a new credential pair in the system

## Best Practices

To avoid hitting rate limits, we recommend:

1. **Validate credentials before use**: Ensure that client credentials are correct before making requests to avoid repeated failed authentication attempts
2. **Securely store credentials**: Implement proper credential management to prevent typos or corruption of stored credentials
3. **Implement exponential backoff**: When encountering authentication failures, increase the time between retry attempts
4. **Cache authentication tokens**: Store valid tokens and reuse them until they expire rather than requesting new tokens for each API call
5. **Monitor response codes**: Watch for HTTP 429 responses which indicate you've reached a rate limit

## Future Updates

As our API evolves, additional endpoints may become subject to rate limiting. This documentation will be updated to reflect any changes to our rate limiting policy.
