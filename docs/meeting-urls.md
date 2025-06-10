---
title: "Meeting URL'sMoon (Dark Mode)Sun (Light Mode)"
description: "🚧 API Reference under construction: We're working on fixing how meeting_url is documented in our API reference. In the meantime, here is a reference for the shapes of various platform meeting URL's. Zoom \"meeting_url\": { \"meeting_id\": string, \"meeting_password\": string | null, \"platform\": \"zoom\" } ..."
source_file: "docs/meeting-urls.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.310Z"
api_parameters_count: "0"
---
> **CALLOUT**:

## 🚧

API Reference under construction

We're working on fixing how `meeting_url` is documented in our API reference. In the meantime, here is a reference for the shapes of various platform meeting URL's.

## Zoom

[](#zoom)

```
"meeting_url": {
  "meeting_id": string,
  "meeting_password": string | null,
  "platform": "zoom"
}

```

## Google Meet

[](#google-meet)

```
"meeting_url": {
  "meeting_id": string,
  "platform": "google_meet"
}

```

## Microsoft Teams

[](#microsoft-teams)

```
"meeting_url": {
  "meeting_id": string | null,
  "meeting_password": string | null,
  "organizer_id": string | null,
  "tenant_id": string | null,
  "message_id": string | null,
  "thread_id": string | null,
  "business_meeting_id": string | null,
  "business_meeting_password": string | null,
  "platform": "microsoft_teams" | "microsoft_teams_live"
}

```

> **CALLOUT**:

## 📘

Microsoft Teams URL differences

Microsoft Teams meeting URL use different parameters depending on the Teams version being used.

The table below shows what you can expect for each Teams version meeting URL.

| Version | Base URL | Non-null Parameters |
| --- | --- | --- |
| Teams for Business | teams.microsoft.com | organizer_idtenant_idmessage_idthread_id |
| Teams for Personal use | teams.live.com | meeting_idmeeting_password |

## Webex

[](#webex)

```
"meeting_url": {
  "meeting_subdomain": string,
  "meeting_mtid": string,
  "meeting_path": string,
  "platform": "webex"
}

```

## GoTo

[](#goto)

```
  "meeting_url": {
    "meeting_id": "680504437",
    "platform": "goto_meeting"
  }

```
