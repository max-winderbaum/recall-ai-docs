---
title: "Calendar Integration FAQMoon (Dark Mode)Sun (Light Mode)"
description: "Calendar Integration FAQ"
source_file: "docs/calendar-integration-faq.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:14.830Z"
api_parameters_count: "0"
---
# How far into the future are calendar events synced in the API?

[](#how-far-into-the-future-are-calendar-events-synced-in-the-api)

4 weeks.

# How long does Recall store calendar data?

[](#how-long-does-recall-store-calendar-data)

Recall will retain calendar data up to 60 days in the past for both Calendar V1 & V2 integrations. Calendar events past 60 days are automatically removed and not available via the API.

# How do I add a bot to a calendar event via email?

[](#how-do-i-add-a-bot-to-a-calendar-event-via-email)

You may prefer a user flow where you can invite an email (eg. [notetaker@yourdomain.com](mailto:notetaker@yourdomain.com)) to any meeting, and the bot will join.

You can accomplish this with the Recall Calendar Integration by:

1.  Creating an email on your end (e.g. [notetaker@yourdomain.com](mailto:notetaker@yourdomain.com))
2.  Connecting that user to the [Recall calendar integration](/reference/calendar-integration.md)
3.  Setting the calendar integration to automatically record every meeting on the calendar

This will assign a meeting bot to all events that your chosen email address is invited to.

# Does the calendar integration support team/shared calendars?

[](#does-the-calendar-integration-support-teamshared-calendars)

Currently only the primary calendar of connected users are supported.

# Are Microsoft Exchange On-premise Calendars supported?

[](#are-microsoft-exchange-on-premise-calendars-supported)

Currently Microsoft Exchange On-premise calendars are not supported.

# Troubleshooting

[](#troubleshooting)
- * *

## `invalid_scope` error

[](#invalid_scope-error)

Even after setting up your OAuth client and successfully integrating calendars, you may see an `invalid_scope` error:

```
"invalid_scope(detail: None of the supported calendar scopes(['https://www.googleapis.com/auth/calendar.events.readonly', 'https://www.googleapis.com/auth/calendar.readonly', 'https://www.googleapis.com/auth/calendar.events', 'https://www.googleapis.com/auth/calendar']) present in response(['https://www.googleapis.com/auth/userinfo.email', 'openid']).)"

```



This happens when the user is connecting their calendar for the first time, and doesn't select the checkbox to allow your app to view their calendar events.

![](https://files.readme.io/a0491cd-invalid_scope.png)

To resolve this, they should reconnect their calendar while ensuring to check this box.
