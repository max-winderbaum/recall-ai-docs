---
title: "Integration GuideMoon (Dark Mode)Sun (Light Mode)"
description: "The calendar integration allows every unique user in your app to connect their Google/Microsoft calendars and have Recall bots join their meetings automatically. Integrate Recall APIs directly into your Web/Mobile applications. Refer to our demo app for an example integration ( source code here ) Th..."
source_file: "docs/calendar-v1-integration-guide.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:10.824Z"
api_parameters_count: "0"
---
The calendar integration allows every unique user in your app to connect their Google/Microsoft calendars and have Recall bots join their meetings automatically.

Integrate Recall APIs directly into your Web/Mobile applications. Refer to our [demo app](https://recall-calendar-integration.pages.dev/) for an example integration ([source code here](https://github.com/recallai/calendar-integration-demo/tree/master/v1-demo))

The following steps are needed for a unique user to connect their calendar and being auto-recording their meetings.

# Generate a calendar auth token

[](#generate-a-calendar-auth-token)

This token is used as authentication for all subsequent calls made to the calendar integration API endpoints. You can generate one using [this endpoint](/reference/calendar_authenticate_create.md). The token is stateless, has an expiry of 1 day and can be generated multiple times for a user. Few things to note are:

1.  The `user_id` field should remain consistent for a specific user across multiple calls, failure to do so can result in duplicate calendar users and multiple bots joining the calls.
2.  We recommend implementing a proxy endpoint on your servers for token generation (see e.g [here](https://github.com/recallai/calendar-integration-demo/tree/master/worker)). This ensures you do not expose your Recall API Key on the client.

# Initiate calendar connection

[](#initiate-calendar-connection)

Setup OAuth clients on the calendar platforms(see [Google Calendar Setup](/reference/calendar-v1-google-calendar.md), [Microsoft Outlook Calendar Setup](/reference/calendar-v1-microsoft-outlook.md)\] for details) and redirect user to calendar connection URLs ([code example here](https://github.com/recallai/calendar-integration-demo/blob/master/v1-demo/client/src/containers/Home/RecallCalendar/hooks/useRecallCalendar/index.ts)).

# Fetch Upcoming Meetings

[](#fetch-upcoming-meetings)

Once a user's calendar is successfully connected. You can retrieve their upcoming meetings via [List Calendar Meetings](/reference/calendar_meetings_list.md) by passing the calendar auth token as `x-recallcalendarauthtoken` header in the request. The calendar integration automatically syncs updates to calendar events in near real-time, so every subsequent request to the list endpoint should give you the latest data.

For meetings that will be recorded by Recall, the meeting object would have `bot_id` attribute populated with the bot scheduled to join the meeting.

# Update recording preferences

[](#update-recording-preferences)

Allow user to [Update Their Recording Preferences](/reference/calendar_user_update.md). See [Auto Recording Logic & Preferences](/reference/calendar-v1-recording-preferences.md) for more details

# Configuring Calendar Bots

[](#configuring-calendar-bots)

> **CALLOUT**:

## 📘

Updating your configuration

To update your Calendar V1 bot configuration, reach out to our team in Slack and include the JSON you'd like to update the configuration to.

Bots scheduled via the calendar integration derive their configuration from a pre-populated preset. Bots will join 2 minutes before the scheduled start time of the meeting.

**All options available in [Create Bot](/reference/bot_create.md) endpoint are supported here.**

Here are a few examples for reference:

*Settings transcription provider for calendar bots*

JSON

```
{
  "recording_config": {
  	"transcript": {
    	"provider": {
      	"meeting_captions": {}
      }
    }
  },
}

```

*Enabling real time transcription for calendar bots*

JSON

```
{
  "recording_config": {
  	"transcript": {
    	"provider": {
      	"meeting_captions": {}
      }
    },
    realtime_endpoints: [
    	{
      	"type": "webhook",
        "events": ["transcript.data"],
        "url": "..."
      }
    ]
  },
}

```

**Note: These apply to all calendar bots, incase you need more granular control over configuration(e.g per user/per event) please checkout Calendar V2 API**

> **CALLOUT**:

## ❗️

Patching not supported

Since Calendar V1 bots get their configuration from this preset as they join meetings, Patch requests to [Update Scheduled Bot](/reference/bot_partial_update.md) won't have an effect on the bot configuration.
