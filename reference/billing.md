---
title: "Get UsageMoon (Dark Mode)Sun (Light Mode)"
description: "Get bot usage statistics This endpoint is rate limited to: 5 requests per min per workspace"
source_file: "reference/billing.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:12.643Z"
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
