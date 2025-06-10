---
title: "Retrieve Bot ScreenshotMoon (Dark Mode)Sun (Light Mode)"
description: "Get a bot screenshot instance. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/bot_screenshots_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:13.299Z"
api_parameters_count: "4"
---
## GET https://us-east-1.recall.ai/api/v1/bot/{bot_id}/screenshots/{id}/

Get a bot screenshot instance

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

Screenshots do not include participant video

Bot screenshots are primarily a debugging tool, and aren't meant to be used for user-facing features.

Because of this, screenshots do not include participant video.

[More info](https://recallai.readme.io/docs/debugging-bots#bot-screenshots)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this bot screenshot. |
| bot_id | uuid | Yes | The ID of the bot for which to retrieve the screenshot |
| recorded_at | date-time | Yes |  |
| url | uri | Yes |  |
