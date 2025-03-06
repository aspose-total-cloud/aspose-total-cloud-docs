---
title: "Rate Limits"
type: docs
url: /rate-limits/
weight: 1
---
# Rate Limits

This page provides information about Aspose.Cloud API rate limits.

## Overview

Aspose.Cloud implements rate limiting to ensure the stability and availability of our services. Rate limits specify the maximum number of requests a client can make to our API within a given time period.

## Current Rate Limits

Currently, rate limits are applied to the following endpoint:

| Endpoint | Method | Rate Limit | Cooldown Period |
|----------|--------|------------|-----------------|
| `/connect/token` | POST | 20 failed requests per minute | 10 minutes |

## Rate Limiter Behavior

If a user exceeds the rate limit (more than 20 failed requests to POST `/connect/token` within a minute), they will be temporarily blocked from accessing the endpoint for a cooldown period of 10 minutes.

During the cooldown period, requests to the rate-limited endpoint will receive an HTTP 429 (Too Many Requests) response.

## Best Practices

To avoid hitting rate limits, we recommend:

1. **Implement exponential backoff**: When encountering authentication failures, increase the time between retry attempts.
2. **Cache authentication tokens**: Store valid tokens and reuse them until they expire rather than requesting new tokens for each API call.
3. **Validate credentials**: Ensure that client credentials are correct before making requests to avoid repeated failed authentication attempts.
4. **Monitor response codes**: Watch for HTTP 429 responses which indicate you've reached a rate limit.

## Future Updates

As our API evolves, additional endpoints may become subject to rate limiting. This documentation will be updated to reflect any changes to our rate limiting policy.
