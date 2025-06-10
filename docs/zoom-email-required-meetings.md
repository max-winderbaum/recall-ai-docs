---
title: "Email Required MeetingsMoon (Dark Mode)Sun (Light Mode)"
description: "Enable bots to join email-required Zoom meetings and webinars."
source_file: "docs/zoom-email-required-meetings.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.854Z"
api_parameters_count: "0"
---
Certain Zoom meetings and webinars require an email in order to join.

If a Zoom bot attempts to join one of these calls and isn't configured with an email, it will produce a `fatal` error with the following sub code: `zoom_email_required`.

## Configuring an email

[](#configuring-an-email)

To enable bots to join email-required meetings and webinars, you can provide a `user_email` in the `zoom` configuration object of your [Create Bot](/reference/bot_create.md) request:

JSON

```
{
  "zoom": {
    "user_email": "john@email.com"
  },
}

```

If the meeting or webinar requires [registration](/docs/registration-required-meetings-webinars.md), this email does *not* have to match the email of the user that registered. You can use any email address.



## Bot Support

[](#bot-support)

| Bot type | Supported? |
| --- | --- |
| Zoom Web (default) | ✅ |
| Zoom Native | ❌ |
