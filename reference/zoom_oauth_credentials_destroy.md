---
title: "Destroy Zoom OAuth CredentialMoon (Dark Mode)Sun (Light Mode)"
description: "Deletes a Zoom OAuth Credential. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom_oauth_credentials_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:09:06.800Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v2/zoom-oauth-credentials/{id}/

Deletes a Zoom OAuth Credential

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see:
- [Recall-Managed OAuth](/docs/recall-managed-oauth#calling-the-recall-api.md)
- [Customer Managed OAuth](/docs/customer-managed-oauth#registering-the-callback-url-in-the-recall-api.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this zoom o auth credential. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/zoom-oauth-credentials/id/"
response = requests.delete(url)
print(response.text)
```
