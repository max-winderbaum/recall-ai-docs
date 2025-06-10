---
title: "Registration-Required Meetings & WebinarsMoon (Dark Mode)Sun (Light Mode)"
description: "Send bots to Zoom registration-required meetings and webinars."
source_file: "docs/registration-required-meetings-webinars.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.574Z"
api_parameters_count: "0"
---
> **CALLOUT**:

## 📘

Registration-required meetings & webinars are supported by **web bots** only.

Recall supports sending bots to registration-required Zoom meetings and webinars.

For a bot to join a registration-required meeting, there are two things required:

1.  A `tk` parameter in the meeting URL
2.  \*An email address

*\*For Zoom webinars, the bot **must** be added as a panelist.*

## `tk` query parameter

[](#tk-query-parameter)

Once a user registers for the meeting or webinar, they will receive a meeting URL from Zoom containing a `tk` query parameter.

When calling [Create Bot](/reference/bot_create.md), you should ensure that the `meeting_url` contains this.

## `user_email`

[](#user_email)

If registration is required for a meeting or webinar, Zoom requires an email in the join request.

This should be provided in the `zoom.user_email` parameter in the [Create Bot](/reference/bot_create.md) request:

JSON

```
{
  "zoom": {
    "user_email": "john@email.com"
  },
}

```

> **CALLOUT**:

## 📘

This email does *not* have to match the email that was registered for the event. For simplicity's sake, you can provide a hard-coded email address such as `bot@yourcompany.com`.

This can be provided regardless of whether the meeting is a registration-required Zoom meeting or not.
