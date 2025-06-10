---
title: "Delete Scheduled BotMoon (Dark Mode)Sun (Light Mode)"
description: "Deletes a bot. This can only be done on scheduled bots that have not yet joined a call. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/bot_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:49:53.956Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v1/bot/{id}/

Deletes a bot. This can only be done on scheduled bots that have not yet joined a call

> **Rate Limiting**: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this bot. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/bot/id/"
response = requests.delete(url)
print(response.text)
```
