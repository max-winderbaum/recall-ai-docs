---
title: "Start ScreenshareMoon (Dark Mode)Sun (Light Mode)"
description: "Causes the bot to start screensharing. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/bot_output_screenshare_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:51:07.220Z"
api_parameters_count: "1"
---
## POST https://us-east-1.recall.ai/api/v1/bot/{id}/output_screenshare/

Causes the bot to start screensharing

> **Rate Limiting**: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this bot. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/bot/id/output_screenshare/"
response = requests.delete(url)
print(response.text)
```
