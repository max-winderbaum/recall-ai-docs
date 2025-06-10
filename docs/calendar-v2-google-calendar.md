---
title: "Google CalendarMoon (Dark Mode)Sun (Light Mode)"
description: "Setup OAuth 2.0 Client Create Google OAuth 2.0 client (skip if you already have one). Copy CLIENT_ID &amp; CLIENT_SECRET values. Ensure Google Calendar API is enabled for the project . Configure permission scopes to at least include calendar.events.readonly &amp; userinfo.email in OAuth Consent Scre..."
source_file: "docs/calendar-v2-google-calendar.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:11.247Z"
api_parameters_count: "0"
---
# Setup OAuth 2.0 Client

[](#setup-oauth-20-client)

1.  [Create Google OAuth 2.0 client](https://support.google.com/googleapi/answer/6158849?hl=en) (skip if you already have one). Copy `CLIENT_ID` & `CLIENT_SECRET` values.
2.  Ensure [Google Calendar API is enabled for the project](https://support.google.com/googleapi/answer/6158841).
3.  Configure permission scopes to at least include `calendar.events.readonly` & `userinfo.email` in **OAuth Consent Screen** section.
4.  Add **Authorized redirect URI** in the **Credentials** section. You should be able to verify ownership of this domain in order publish to production.

# Implement OAuth 2.0 Authorization Code Flow

[](#implement-oauth-20-authorization-code-flow)

[https://developers.google.com/identity/protocols/oauth2/web-server#obtainingaccesstokens](https://developers.google.com/identity/protocols/oauth2/web-server#obtainingaccesstokens)

Code samples from Calendar V2 Demo Repository:
- [https://github.com/recallai/calendar-integration-demo/blob/v2/v2-demo/logic/oauth.js](https://github.com/recallai/calendar-integration-demo/blob/v2/v2-demo/logic/oauth.js)
- [https://github.com/recallai/calendar-integration-demo/blob/v2/v2-demo/routes/oauth-callback/google-calendar.js#L27](https://github.com/recallai/calendar-integration-demo/blob/v2/v2-demo/routes/oauth-callback/google-calendar.js#L27)



# FAQ

[](#faq)
- * *

## Why did my calendar disconnect randomly all of a sudden with `invalid_grant`?

[](#why-did-my-calendar-disconnect-randomly-all-of-a-sudden-with-invalid_grant)

If your Google OAuth client is in "testing", any connections made automatically expire after 7 days. After the client has been published successfully, connections will stay connected indefinitely unless OAuth permissions are revoked, or a user changes their password.

More info on this [here](https://developers.google.com/identity/protocols/oauth2#expiration).

## When is the name of the invitee included on the calendar event?

[](#when-is-the-name-of-the-invitee-included-on-the-calendar-event)

For the organizer of the event (`self` = `true`) the Google Calendar API does not populate the `displayName`, presumably since the name is already known from their calendar connection or authentication to your platform.

For other attendees, this is more nuanced. By default, the displayName isn't populated, but Google has a few mechanisms to try to infer this by:

1.  Getting the name if the email belongs to the same Google workspace
2.  Getting the name from a Google Contact:
    1.  There are many ways a Google Contact is automatically created. One common example is that Google automatically creates a Google Contact for other gmail/Google Workspace users that you've had an email with.
