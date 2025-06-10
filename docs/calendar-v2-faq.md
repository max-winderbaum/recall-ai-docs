---
title: "Calendar V2 FAQMoon (Dark Mode)Sun (Light Mode)"
description: "Calendar V2 FAQ"
source_file: "docs/calendar-v2-faq.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:14.917Z"
api_parameters_count: "0"
---
# Grouping recurring calendar events

[](#grouping-recurring-calendar-events)

You may want to group all instances of a recurring event for tracking and applying recording preferences on these events.

If you're using the Calendar V2 integration, we recommend using these fields to group instances of a recurring events:
- `seriesMasterId` - Microsoft Outlook
- `recurringEventId` - Google Calendar

Since these are calendar platform-specific, you can find them in the `raw` attribute of the calendar event object.

# What if multiple bots from different apps using Recall try to join the same meeting?

[](#what-if-multiple-bots-from-different-apps-using-recall-try-to-join-the-same-meeting)

Deduplication keys are scoped to a given Recall account. This means that multiple bots should have no trouble joining the same meeting, even if both companies are using the same deduplication key scheme.

# Why is the `platform_email` `null` when I create the calendar?

[](#why-is-the-platform_email-null-when-i-create-the-calendar)

The `​platform­_email​` may be ​null​ briefly when you create the calendar. This is because the calendar sync (which populates the `​platform­_email​`) happens asynchronously after the calendar is created.

If you need the email immediately, we'd recommend using the OAuth token to call the calendar platform (Google or Microsoft) APIs directly to retrieve the user email.

# Why did a calendar fail to connect with an `invalid_scope` error?

[](#why-did-a-calendar-fail-to-connect-with-an-invalid_scope-error)

Calendars can fail to connect due to `invalid_scope` for one of two reasons:

1.  The OAuth client is setup incorrectly (e.g. missing necessary scopes in the OAuth client setup)
2.  The end user did not grant the necessary permissions when connecting their account. This can happen when they forget to click a checkbox during the OAuth flow.

![If a user doesn't click the highlighted checkbox, this can result in an `invalid_scope` error on their calendar.](https://files.readme.io/ecdc43a-calendar-integraiton-checkbox.png)

If a user doesn't click the highlighted checkbox, this can result in an `invalid_scope` error on their calendar.



To resolve this, the user should reconnect their calendar while ensuring to check the checkbox.



# AADSTS7000215 Error

[](#aadsts7000215-error)

This indicates something is wrong with your OAuth client secret, for instance:
- **The secret expired**: In this case, you should [generate a new secret](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/create-or-update-client-ids-and-secrets#update-the-client-secret-associated-with-your-client-id), and [update](/reference/calendars_partial_update.md) any outlook calendars with the new secret value.
- **You've regenerated the secret, and haven't updated calendars in Recall:** In this case, you should [update](/reference/calendars_partial_update.md) any calendars with the new secret value.

*In both scenarios, updating the calendars' `client_secret` will kick off a reconnection.*

# Why did the Calendar ID Associated with an Event ID Change?

[](#why-did-the-calendar-id-associated-with-an-event-id-change)

Calendar events can have their calendar IDs changed on rare occasions due to a process called [event ownership transfer](https://support.google.com/calendar/answer/78739?hl=en&co=GENIE.Platform%3DDesktop). This happens when the ownership of an event is moved from one calendar to another, resulting in the same event ID being linked to a new calendar ID.

Such changes can occur unexpectedly, especially when events are managed by users within the same organization. If your system depends on a stable calendar ID, you may need to account for this scenario in your workflows.



# Why is the `onlineMeeting.joinUrl` populated on an event, but the `meeting_url` is not?

[](#why-is-the-onlinemeetingjoinurl-populated-on-an-event-but-the-meeting_url-is-not)

This can happen when the meeting URL is a wrapped link or is a link to a meeting on an unsupported platform.



# My Microsoft OAuth client secret is expiring. How do I migrate to a new secret?

[](#my-microsoft-oauth-client-secret-is-expiring-how-do-i-migrate-to-a-new-secret)

Refresh tokens from Microsoft OAuth are not tied to specific client secrets.

This means that you can safely [update](/reference/calendars_partial_update.md) any calendars with the new secret, and Recall will automatically start using the new secret. End users do not need to reconnect.

In other words, you just need to:
- [Generate](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/recommendation-renew-expiring-application-credential?tabs=microsoft-entra-admin-center#action-plan) a new OAuth secret
- [Update](/reference/calendars_partial_update.md) any calendars with the new `oauth_client_secret` value

Recall will automatically handle the rest, no end user action required.



# Why is the attendees field missing on the calendar event?

[](#why-is-the-attendees-field-missing-on-the-calendar-event)

This happens when there are no attendees on the calendar event so the meeting platform omits it



# Why are there missing attendees on the calendar event?

[](#why-are-there-missing-attendees-on-the-calendar-event)

This happens when the host unchecks the `Guest Permissions` > `See guest list` checkbox

![](https://files.readme.io/feebf9e92a3e774cf827e7bb982ea94c35b5eb76e63207c8370e4c66cd06e340-CleanShot_2025-05-19_at_10.35.412x.png)
