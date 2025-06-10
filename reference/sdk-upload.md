---
title: "List Desktop SDK UploadsMoon (Dark Mode)Sun (Light Mode)"
description: "Get a list of all Desktop SDK uploads This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/sdk-upload.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:14.890Z"
api_parameters_count: "6"
---
## GET https://us-east-1.recall.ai/api/v1/sdk-upload/

Get a list of all Desktop SDK uploads This endpoint is rate limited to: 60 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes |  |
| status | object | Yes |  |
| recording_id | string | Yes |  |
| upload_token | string | Yes |  |
| created_at | date-time | Yes |  |
| metadata | object | No |  |
