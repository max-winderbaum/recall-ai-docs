---
title: "Retrieve RecordingMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/recording_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:14.870Z"
api_parameters_count: "18"
---
## GET https://us-east-1.recall.ai/api/v1/recording/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this recording. |
| created_at | date-time | Yes |  |
| started_at | date-time \| null | Yes |  |
| completed_at | date-time \| null | Yes |  |
| status | object | Yes | processing - Processing paused - Paused done - Done failed - Failed deleted - Deleted  processing paused done failed deleted |
| code | string | Yes | processing - Processing paused - Paused done - Done failed - Failed deleted - Deleted  processing paused done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| media_shortcuts | object | Yes |  |
| video_mixed | object \| null | Yes |  |
| transcript | object \| null | Yes |  |
| participant_events | object \| null | Yes |  |
| meeting_metadata | object \| null | Yes |  |
| realtime_endpoints | array of objects | Yes |  |
| metadata | object | Yes |  |
| bot | object \| null | Yes |  |
| desktop_sdk_upload | object \| null | Yes |  |
| expires_at | date-time | Yes |  |
