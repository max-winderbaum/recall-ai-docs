---
title: "Destroy Zoom OAuth AppMoon (Dark Mode)Sun (Light Mode)"
description: "Deletes a Zoom OAuth App. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom_oauth_apps_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:08:02.082Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/{id}/

Deletes a Zoom OAuth App

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Zoom OAuth Integration](/docs/zoom-oauth-integration.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this zoom o auth app. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/id/"
response = requests.delete(url)
print(response.text)
```
