---
title: "Get UsageMoon (Dark Mode)Sun (Light Mode)"
description: "Get bot usage statistics This endpoint is rate limited to: 5 requests per min per workspace"
source_file: "reference/billing.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:48:58.118Z"
api_parameters_count: "3"
---
## GET https://us-east-1.recall.ai/api/v1/billing/usage/

Get bot usage statistics This endpoint is rate limited to: 5 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| end | date-time | No |  |
| start | date-time | No |  |
| bot_total | double | Yes | The total amount of time, in seconds, of bots used. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/billing/usage/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "bot_total": 0
}
```
