---
title: "Refresh Calendar MeetingsMoon (Dark Mode)Sun (Light Mode)"
description: "Resync the calendar meetings for the user. This endpoint is rate limited to: 120 requests per min per calendar_user"
source_file: "reference/calendar_meetings_refresh_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:55:03.905Z"
api_parameters_count: "28"
---
## POST https://us-east-1.recall.ai/api/v1/calendar/meetings/refresh/

Resync the calendar meetings for the user

> **Rate Limiting**: 120 requests per min per calendar_user

> **CALLOUT**:

## 📘

Recall keeps calendars in sync for you and you do not need to call this endpoint in order to get the most up-to-date version of users' calendars.

For more information, see [Calendar V1](/docs/calendar-v1-faq#when-do-i-have-to-call-the-refresh-calendar-meetings-endpoint.md).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes |  |
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
| teams_invite | object | Yes |  |
| meet_invite | object | Yes |  |
| webex_invite | object | Yes |  |
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
url = "https://us-east-1.recall.ai/api/v1/calendar/meetings/refresh/"
headers = {"accept": "application/json"}
response = requests.post(url, headers = headers)
print(response.text)
```

## Sample Response

```json
[
  {
    "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "override_should_record": true,
    "title": "string",
    "will_record": true,
    "will_record_reason": "string",
    "start_time": "2025-06-10T18:54:55.192Z",
    "end_time": "2025-06-10T18:54:55.192Z",
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
]
```
