---
title: "Calendar Event Platform DataMoon (Dark Mode)Sun (Light Mode)"
description: "Calendar event platform data for Calendar V2 events."
source_file: "reference/calendar-event-platform-data.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:13.049Z"
api_parameters_count: "0"
---
Calendar event platform data for Calendar V2 events.

> **CALLOUT**:

## 📘

For more info, see:
- [Calendar V2](/docs/v2.md)
- [List Calendar Events](/reference/calendar_events_list.md)

Examples of `raw` fields in calendar events for Outlook and Google Calendar

## Google Calendar

[](#google-calendar)

*For a full list of Google Calendar event properties, see \[here\]*([https://developers.google.com/calendar/api/v3/reference/events](https://developers.google.com/calendar/api/v3/reference/events)).

JSON

```
{
  "id": "5qd60oqa8t0dgqlon2msci0a37_20240501T213000Z",
  "end": {
    "dateTime": "2024-05-01T18:00:00-04:00",
    "timeZone": "America/New_York"
  },
  "etag": "3427970920200000",
  "kind": "calendar#event",
  "start": {
    "dateTime": "2024-05-01T17:30:00-04:00",
    "timeZone": "America/New_York"
  },
  "status": "confirmed",
  "created": "2024-02-15T12:10:25.000Z",
  "creator": {
    "email": "dummy@example.com"
  },

  "iCalUID": "5dgqlon2msci0a37qd60oqa8t0_R20240513T213000@google.com",
  "summary": "Meeting Summary",
  "updated": "2024-04-30T18:20:15.000Z",
  "htmlLink": "https://dummy.calendar.com/event?eid=5qd60oqa8t0dgqlon2msci0a37_20240501T213000Z",
  "sequence": 0,
  "attendees": [
    {
      "email": "dummy@example.com",
      "organizer": true,
      "responseStatus": "accepted"
    },
    {
      "email": "dummy1@example.com",
      "responseStatus": "accepted"
    },
    {
      "email": "dummy2@example.com",
      "responseStatus": "accepted"
    },
    {
      "email": "dummy3@example.com",
      "responseStatus": "accepted"
    },
    {
      "self": true,
      "email": "dummy4@example.com",
      "responseStatus": "accepted"
    }
  ],
  "eventType": "default",
  "organizer": {
    "email": "dummy@example.com"
  },
  "reminders": {
    "useDefault": true
  },
  "hangoutLink": "https://meet.google.com/dummy-meet-link",
  "conferenceData": {
    "entryPoints": [
      {
        "uri": "https://meet.google.com/dummy-meet-link",
        "label": "meet.google.com/dummy-meet-link",
        "entryPointType": "video"
      },
      {
        "pin": "123456",
        "uri": "https://tel.meet/dummy-meet-link?pin=123456",
        "entryPointType": "more"
      },
      {
        "pin": "789101",
        "uri": "tel:+1-234-567-8901",
        "label": "+1 234-567-8901",
        "regionCode": "US",
        "entryPointType": "phone"
      }
    ],
    "conferenceId": "dummy-conference-id",
    "conferenceSolution": {
      "key": {
        "type": "dummy_type"
      },
      "name": "Dummy Meet",
      "iconUri": "https://dummy.com/dummy-meet-icon.png"
    }
  },
  "recurringEventId": "dummy_recurring_event_id",
  "originalStartTime": {
    "dateTime": "2024-05-01T17:30:00-04:00",
    "timeZone": "America/New_York"
  }
}

```

## Microsoft Outlook

[](#microsoft-outlook)

*For a full list of Microsoft Outlook event properties, see \[here\]*([https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0)) .

JSON

```
{
  "id": "AAMkAGU0NmU2MDdkLTc2YTItNDUzNy1hZGZiLTg5NTBhZDBhZWZkYwBGAAAAAAD2hdptzWPQRaMxTFSH1M95BwCnMSSEM-xIRYvttuW8p15ZAAAAAAENAACnMSSEM-xIRYvttuW8p15ZAAArbXh7AAA=",
  "end": {
    "dateTime": "2024-07-01T05:30:00.0000000",
    "timeZone": "UTC"
  },
  "body": {
    "content": "<HTML_PLACEHOLDER>",
    "contentType": "html"
  },
  "type": "singleInstance",
  "start": {
    "dateTime": "2024-07-01T05:00:00.0000000",
    "timeZone": "UTC"
  },
  "showAs": "busy",
  "iCalUId": "040000008200E00074C5B7101A82E008000000006E2016F08CA1D9010000000000000000100000006ED5238A69D3E949854B2766E21DA615",
  "isDraft": false,
  "subject": "Dummy Meeting Subject",
  "webLink": "https://dummy.office365.com/owa/?itemid=AAMkAGU0NmU2MDdkLTc2YTItNDUzNy1hZGZiLTg5NTBhZDBhZWZkYwBGAAAAAAD2hdptzWPQRaMxTFSH1M95BwCnMSSEM%2FxIRYvttuW8p15ZAAAAAAENAACnMSSEM%2FxIRYvttuW8p15ZAAArbXh7AAA%3D&exvsurl=1&path=/calendar/item",
  "isAllDay": false,
  "location": {
    "uniqueId": "Generic Meeting Room",
    "displayName": "Generic Meeting Room",
    "locationType": "default",
    "uniqueIdType": "private"
  },
  "attendees": [],
  "changeKey": "pzEkhDP8SEWL7bblvKdeWQAAK1bYpw==",
  "locations": [
    {
      "uniqueId": "Generic Meeting Room",
      "displayName": "Generic Meeting Room",
      "locationType": "default",
      "uniqueIdType": "private"
    }
  ],
  "organizer": {
    "emailAddress": {
      "name": "John Doe",
      "address": "john.doe@example.com"
    }
  },
  "categories": [],
  "importance": "normal",
  "recurrence": null,
  "@odata.etag": "W/\"pzEkhDP8SEWL7bblvKdeWQAAK1bYpw==",
  "@odata.type": "#microsoft.graph.event",
  "bodyPreview": "________________________________________________________________________________\r\nGeneric Meeting\r\nJoin with Any Device\r\nClick here to join the meeting\r\nMeeting ID: XXX XXX XXX XXX\r\nPasscode: XXXXXX\r\nDownload Meeting App | Join via Web\r\nMore Information | Meeting Options",
  "isCancelled": false,
  "isOrganizer": true,
  "sensitivity": "normal",
  "isReminderOn": true,
  "occurrenceId": null,
  "hideAttendees": false,
  "onlineMeeting": {
    "joinUrl": "https://dummy.microsoft.com/l/meetup-join/19%3ameeting_M2I2NmIwMWYtODQzMi00MmU0LTg4NWEtY2NlOGRjODA1YTk4%40thread.v2/0?context=%7b%22Tid%22%3a%2210e2f0f0-d173-478a-b15d-b54605813dd0%22%2c%22Oid%22%3a%22b7258109-1891-40f8-8c7d-3516121f2a35%22%7d"
  },
  "transactionId": null,
  "hasAttachments": false,
  "responseStatus": {
    "time": "0001-01-01T00:00:00Z",
    "response": "organizer"
  },
  "seriesMasterId": null,
  "createdDateTime": "2024-07-01T03:31:07.9720841Z",
  "isOnlineMeeting": true,
  "onlineMeetingUrl": null,
  "responseRequested": true,
  "originalEndTimeZone": "Tokyo Standard Time",
  "lastModifiedDateTime": "2024-07-01T03:33:10.3161178Z",
  "allowNewTimeProposals": true,
  "onlineMeetingProvider": "teamsForBusiness",
  "originalStartTimeZone": "Tokyo Standard Time",
  "reminderMinutesBeforeStart": 15
}

```
- [Table of Contents](#)
- -   [Google Calendar](#google-calendar)
- [Microsoft Outlook](#microsoft-outlook)
