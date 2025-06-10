---
title: "Identify Meeting Participants UniquelyMoon (Dark Mode)Sun (Light Mode)"
description: "Depending on your use case, you might want to be able to identify participants across meetings. Meeting platforms don't expose the email addresses of participants, though there are some some ways to achieve identify participants uniquely across meetings. Calendar integration If you're using the cale..."
source_file: "docs/identify-meeting-participants-uniquely.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.212Z"
api_parameters_count: "0"
---
Depending on your use case, you might want to be able to identify participants across meetings.

Meeting platforms don't expose the email addresses of participants, though there are some some ways to achieve identify participants uniquely across meetings.

## Calendar integration

[](#calendar-integration)

If you're using the calendar integration, you can map users to emails of calendar invites to get their emails.
- Fuzzy match on calendar event participants
- Use email address as ID

Benefit: Works across meeting platforms

Con: doesn't work 100% of the time

## Zoom: `user_conf_id`

[](#zoom-user_conf_id)

> **CALLOUT**:

## 📘

`conf_user_id` uniquely identifies participants across Zoom meetings

```
{
  "id": 16998240,
  "name": "John Smith",
  "is_host": true,
  "platform": "desktop",
  "extra_data": {
    "zoom": {
      "os": 2,
      "guest": false,
      "user_guid": "EF3AL77C-49AB-6F8A-A947-61C6AB57D6E6",
			"conf_user_id": "RiajKBaChMxzJAmuF90nln"
    }
  }
}

```
