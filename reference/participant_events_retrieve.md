---
title: "Retrieve Participant EventsMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/participant_events_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:14.613Z"
api_parameters_count: "12"
---
## GET https://us-east-1.recall.ai/api/v1/participant_events/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this participant events artifact. |
| recording | object | Yes |  |
| metadata | object \| null | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| code | string | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| data | object | Yes | Download all participant events for the recording. See response format here |
| participant_events_download_url | uri \| null | Yes | Download all participant events for the recording. See response format here |
| speaker_timeline_download_url | uri \| null | Yes | Download speaker timeline for the recording. See response format here |
| participants_download_url | uri \| null | Yes | Download all participants for the recording. See response format here |
