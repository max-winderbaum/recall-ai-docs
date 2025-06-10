---
title: "List Zoom Meeting to OAuth Credential MappingsMoon (Dark Mode)Sun (Light Mode)"
description: "Get a list of all mappings from Zoom Meeting ID to Zoom OAuth Credential. Recall uses mappings internally to determine which credential to use when automatically fetching join tokens for a meeting. Inspecting these mappings may be helpful when debugging bots that don't automatically record due to be..."
source_file: "reference/zoom-meetings-to-credentials.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:15.070Z"
api_parameters_count: "10"
---
## GET https://us-east-1.recall.ai/api/v2/zoom-meetings-to-credentials/

Get a list of all mappings from Zoom Meeting ID to Zoom OAuth Credential. Recall uses mappings internally to determine which credential to use when automatically fetching join tokens for a meeting. Inspecting these mappings may be helpful when debugging bots that don't automatically record due to be...

> **CALLOUT**:

## 📘

Recall uses mappings internally to determine which credential to use when automatically fetching join tokens for a meeting.

Inspecting these mappings may be helpful when debugging bots that don't automatically record due to being unable to fetch join tokens.

For more information, see [Testing Your Zoom OAuth Integration](/docs/zoom-oauth-sync-status-and-debugging.md).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| credential | uuid | No |  |
| cursor | string | No | The pagination cursor value. |
| meeting_id | integer | No |  |
| ordering | string | No | Which field to use when ordering the results. |
| synced_at_after | date-time | No |  |
| synced_at_before | date-time | No |  |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No |  |
| synced_at | date-time | Yes |  |
