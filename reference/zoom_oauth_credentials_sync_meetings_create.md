---
title: "Manually Resync MeetingsMoon (Dark Mode)Sun (Light Mode)"
description: "Manually re-sync meetings accessible from these credentials. This operation is asynchronous, and may take some time to complete.Use the meeting_sync_status field on the credential object to check status of sync.This is ONLY useful for debugging, and should not be called on a regular basis. Meetings ..."
source_file: "reference/zoom_oauth_credentials_sync_meetings_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:15.915Z"
api_parameters_count: "1"
---
## POST https://us-east-1.recall.ai/api/v2/zoom-oauth-credentials/{id}/sync-meetings/

Manually re-sync meetings accessible from these credentials. This operation is asynchronous, and may take some time to complete.Use the meeting_sync_status field on the credential object to check status of sync.This is ONLY useful for debugging, and should not be called on a regular basis. Meetings ...

> **CALLOUT**:

## 📘

For more information, see [Zoom OAuth Integration](/docs/zoom-oauth-integration)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this zoom o auth credential. |
