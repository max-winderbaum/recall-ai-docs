---
title: "Retrieve Realtime EndpointsMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/realtime_endpoint_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:14.733Z"
api_parameters_count: "11"
---
## GET https://us-east-1.recall.ai/api/v1/realtime_endpoint/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this realtime endpoint. |
| created_at | date-time | Yes |  |
| recording | object | Yes |  |
| metadata | object \| null | Yes |  |
| type | string | Yes |  |
| status | object | Yes | running - Running done - Done failed - Failed deleted - Deleted  running done failed deleted |
| code | string | Yes | running - Running done - Done failed - Failed deleted - Deleted  running done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| url | uri | Yes |  |
| events | array of strings | Yes |  |
