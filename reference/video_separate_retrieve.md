---
title: "Retrieve Video SeparateMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/video_separate_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:15.029Z"
api_parameters_count: "11"
---
## GET https://us-east-1.recall.ai/api/v1/video_separate/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this video separate artifact. |
| recording | object | Yes |  |
| metadata | object \| null | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| code | string | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| data | object | Yes | Download all video separate parts for the recording. See response format here |
| download_url | uri \| null | Yes | Download all video separate parts for the recording. See response format here |
| format | string | Yes | mp4 - Mp4  mp4 |
