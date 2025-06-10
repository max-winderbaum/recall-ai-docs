---
title: "Update Meeting MetadataMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/meeting_metadata_partial_update.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:14.487Z"
api_parameters_count: "11"
---
## PATCH https://us-east-1.recall.ai/api/v1/meeting_metadata/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this meeting metadata artifact. |
| metadata | object | No |  |
| recording | object | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| code | string | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| data | object | Yes |  |
| title | string \| null | Yes |  |
| zoom | object \| null | Yes |  |
