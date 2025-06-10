---
title: "Delete Slack TeamMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/slack_teams_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:03:39.694Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v2/slack-teams/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

> **CALLOUT**:

## 📘

Relevant Links

[Slack Huddles Overview](/docs/slack-huddles.md)

[Slack Bot Setup](/docs/slack-bot-setup.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | string | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/slack-teams/id/"
response = requests.delete(url)
print(response.text)
```
