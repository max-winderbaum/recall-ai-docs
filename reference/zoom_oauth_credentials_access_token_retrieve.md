---
title: "Get Access TokenMoon (Dark Mode)Sun (Light Mode)"
description: "Get the access token for these credentials. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom_oauth_credentials_access_token_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:15.349Z"
api_parameters_count: "3"
---
## GET https://us-east-1.recall.ai/api/v2/zoom-oauth-credentials/{id}/access-token/

Get the access token for these credentials

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Zoom OAuth Access Token](/docs/zoom-oauth-faq#will-we-be-able-to-get-the-customers-access-token-if-we-use-recall-managed-oauth.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this zoom o auth credential. |
| token | string | Yes |  |
| expires_at | date-time | Yes |  |
