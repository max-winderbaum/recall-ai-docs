---
title: "Get Access TokenMoon (Dark Mode)Sun (Light Mode)"
description: "Get the OAuth access token for this calendar account. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/calendar_accounts_access_token_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:13.113Z"
api_parameters_count: "4"
---
## GET https://us-east-1.recall.ai/api/v2/calendar-accounts/{uuid}/access_token/

Get the OAuth access token for this calendar account

> **Rate Limiting**: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| uuid | string | Yes |  |
| access_token | string | Yes |  |
| code | string | Yes | no_oauth_credentials - no_oauth_credentials bad_refresh_token - bad_refresh_token error - error  no_oauth_credentials bad_refresh_token error |
| message | string | Yes |  |
