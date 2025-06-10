---
title: "Update Calendar MeetingMoon (Dark Mode)Sun (Light Mode)"
description: "Use this endpoint to update override_should_record property of the meeting. This endpoint is rate limited to: 120 requests per min per calendar_user"
source_file: "reference/calendar_meetings_update.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:55:24.356Z"
api_parameters_count: "38"
---
## PATCH https://us-east-1.recall.ai/api/v1/calendar/meetings/{id}/

Use this endpoint to update override_should_record property of the meeting

> **Rate Limiting**: 120 requests per min per calendar_user

> **CALLOUT**:

## 📘

For more information, see [Calendar V1](/docs/calendar-v1-1.md).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this calendar meeting. |
| override_should_record | boolean \| null | No |  |
| title | string | Yes |  |
| will_record | boolean | Yes |  |
| will_record_reason | string | Yes |  |
| start_time | date-time | Yes |  |
| end_time | date-time | Yes |  |
| platform | string | Yes |  |
| platform_id | string | Yes |  |
| meeting_platform | string | Yes |  |
| calendar_platform | string | Yes |  |
| zoom_invite | object | Yes |  |
| meeting_id | string | Yes |  |
| meeting_password | string | No |  |
| teams_invite | object | Yes |  |
| organizer_id | string | Yes |  |
| tenant_id | string | Yes |  |
| message_id | string | Yes |  |
| thread_id | string | Yes |  |
| meet_invite | object | Yes |  |
| webex_invite | object | Yes | This value is available only for Scheduled Webex meetings. |
| meeting_subdomain | string | Yes |  |
| meeting_path | string | No | This value is available only for Scheduled Webex meetings. |
| meeting_mtid | string | No | This value is available only for Scheduled Webex meetings. |
| meeting_personal_room_id | string | No | This value is available only for Personal room Webex meetings. |
| bot_id | uuid \| null | Yes |  |
| is_external | boolean | Yes |  |
| is_hosted_by_me | boolean | Yes |  |
| is_recurring | boolean | Yes |  |
| organizer_email | string | Yes |  |
| attendee_emails | array of strings | Yes |  |
| attendees | array of objects | Yes | accepted - accepted declined - declined tentative - tentative not_available - not_available  accepted declined tentative not_available |
| name | string | Yes |  |
| email | string | Yes |  |
| is_organizer | boolean | Yes |  |
| status | string | Yes | accepted - accepted declined - declined tentative - tentative not_available - not_available  accepted declined tentative not_available |
| ical_uid | string | Yes |  |
| visibility | string | Yes | For Google calendar meetings('default' \| 'public' \| 'private' \| 'confidential').         For Microsoft Outlook('normal' \| 'personal' \| 'private' \| 'confidential').         Additionally, this field may contain 'null' value. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/calendar/meetings/id/"
payload = { "override_should_record": True"
}
headers = {
"accept": "application/json",
"content-type": "application/json"
}
response = requests.put(url, json = payload, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "override_should_record": true,
  "title": "string",
  "will_record": true,
  "will_record_reason": "string",
  "start_time": "2025-06-10T18:55:13.603Z",
  "end_time": "2025-06-10T18:55:13.603Z",
  "platform": "string",
  "platform_id": "string",
  "meeting_platform": "string",
  "calendar_platform": "string",
  "zoom_invite": {
    "meeting_id": "string",
    "meeting_password": "string"
  },
  "teams_invite": {
    "organizer_id": "string",
    "tenant_id": "string",
    "message_id": "string",
    "thread_id": "string"
  },
  "meet_invite": {
    "meeting_id": "string"
  },
  "webex_invite": {
    "meeting_subdomain": "string",
    "meeting_path": "string",
    "meeting_mtid": "string",
    "meeting_personal_room_id": "string"
  },
  "bot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "is_external": true,
  "is_hosted_by_me": true,
  "is_recurring": true,
  "organizer_email": "string",
  "attendee_emails": [
    "string"
  ],
  "attendees": [
    {
      "name": "string",
      "email": "string",
      "is_organizer": true,
      "status": "accepted"
    }
  ],
  "ical_uid": "string",
  "visibility": "string"
}
```
