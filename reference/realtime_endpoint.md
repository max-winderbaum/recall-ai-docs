---
title: "List Realtime EndpointsMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/realtime_endpoint.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:01:06.726Z"
api_parameters_count: "16"
---
## GET https://us-east-1.recall.ai/api/v1/realtime_endpoint/

This endpoint is rate limited to: 60 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| created_at_after | date-time | No |  |
| created_at_before | date-time | No |  |
| cursor | string | No | The pagination cursor value. |
| recording_id | uuid | No |  |
| status_code | string | No | running - Running done - Done failed - Failed |
| type | string | No | rtmp - Rtmp websocket - Websocket webhook - Webhook desktop-sdk-callback - Desktop Sdk Callback |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No |  |
| id | uuid | Yes |  |
| created_at | date-time | Yes |  |
| recording | object | Yes |  |
| metadata | object | Yes |  |
| status | object | Yes |  |
| url | uri | Yes |  |
| events | array of strings | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/realtime_endpoint/"
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
      "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "created_at": "2025-06-10T19:00:58.024Z",
      "recording": {
        "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "metadata": {
          "additionalProp": "string"
        }
      },
      "metadata": {
        "additionalProp": "string"
      },
      "type": "string",
      "status": {
        "code": "running",
        "sub_code": "string",
        "updated_at": "2025-06-10T19:00:58.024Z"
      },
      "url": "string",
      "events": [
        "string"
      ]
    }
  ]
}
```
