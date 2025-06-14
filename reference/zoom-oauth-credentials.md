---
title: "List Zoom OAuth Credential LogsMoon (Dark Mode)Sun (Light Mode)"
description: "Get a list of all Zoom OAuth Credential Logs. Any warnings or errors related to the OAuth Credential will be logged here, and this can be helpful for debugging. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom-oauth-credentials.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:07:19.737Z"
api_parameters_count: "10"
---
## GET https://us-east-1.recall.ai/api/v2/zoom-oauth-credential-logs/

Get a list of all Zoom OAuth Credential Logs. Any warnings or errors related to the OAuth Credential will be logged here, and this can be helpful for debugging

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see:
- [Recall-Managed OAuth](/docs/recall-managed-oauth#calling-the-recall-api.md)
- [Customer Managed OAuth](/docs/customer-managed-oauth#registering-the-callback-url-in-the-recall-api.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| created_at_after | date-time | No |  |
| created_at_before | date-time | No |  |
| credential | uuid | No |  |
| cursor | string | No | The pagination cursor value. |
| ordering | string | No | Which field to use when ordering the results. |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No |  |
| message | string | Yes |  |
| created_at | date-time | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/zoom-oauth-credential-logs/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "next": "string",
  "previous": "string",
  "results": [
    {
      "credential": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "message": "string",
      "created_at": "2025-06-10T19:07:11.140Z"
    }
  ]
}
```
