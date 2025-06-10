---
title: "Manually Revalidate CredentialMoon (Dark Mode)Sun (Light Mode)"
description: "Manually check the validity of credentials, and re-enable them if they are functional. This can be useful if credentials are disabled due to repeated errors. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom_oauth_credentials_validate_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:15.473Z"
api_parameters_count: "1"
---
## POST https://us-east-1.recall.ai/api/v2/zoom-oauth-credentials/{id}/validate/

Manually check the validity of credentials, and re-enable them if they are functional. This can be useful if credentials are disabled due to repeated errors

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Zoom OAuth Integration](/docs/zoom-oauth-integration.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this zoom o auth credential. |
