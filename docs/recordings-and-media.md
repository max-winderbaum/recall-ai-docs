---
title: "Recordings and MediaMoon (Dark Mode)Sun (Light Mode)"
description: "Recordings Recordings are the fundamental entity for capturing and storing conversation data. A recording serves as a container that encapsulates various types of conversation data and metadata, providing both real-time data streams through Real-Time Endpoints and comprehensive snapshots of meetings..."
source_file: "docs/recordings-and-media.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.684Z"
api_parameters_count: "0"
---
# Recordings

[](#recordings)

Recordings are the fundamental entity for capturing and storing conversation data.

A recording serves as a container that encapsulates various types of conversation data and metadata, providing both real-time data streams through [Real-Time Endpoints](/docs/real-time-endpoints.md) and comprehensive snapshots of meetings or interactions through Media objects.

Recordings can be generated through a variety of data sources, such a [Meeting Bots](/docs/bot-overview.md) and the [Desktop SDK](/docs/desktop-sdk-beta.md).

# Media

[](#media)

Media refers to the different types of data produced by a recording. Each captures a distinct aspect of the conversation, enabling targeted use cases such as transcription analysis, participant behavior tracking, or meeting playback.

Media object expose the data captured by them through the `data` field including [download urls](/docs/download-urls.md) for various cases. These are available once a media object is complete (i.e it has transitioned to the `done` status).

Some examples can be found below.

## **Transcript**

[](#transcript)

Provides the text representation of the conversation, including who said what and when. Transcripts can be used for searching, analyzing, or summarizing the conversation content.

*See: [Generating Transcripts](/docs/real-time-vs-async-transcription.md)*

## **Video (Mixed)**

[](#video-mixed)

Mixed video refers to a single video file containing all participants’ video feeds combined into one stream. Ideal for replaying the entire meeting as it happened.

*See: [Bot Recording](/docs/receive-a-recording.md)*

## **Audio (Mixed)**

[](#audio-mixed)

Mixed audio refers to a single audio file containing all participants' audio feeds combined into one stream. Ideal for replaying the conversation's audio and generating transcripts.

## **Participant Events**

[](#participant-events)

A detailed log of participant activities during the meeting, such as join/leave times, active speaker events, and other engagement actions. Useful for analyzing participant behavior and engagement patterns.

*See: [Participants Events](/docs/meeting-participants-events.md)*

## **Meeting Metadata**

[](#meeting-metadata)

Structured data that includes key information about the meeting, such as the meeting title or unique identifiers (though importantly, the metadata exposed by a given meeting platform varies). Useful for providing high-level information about a given meeting.

*See: [Meeting Metadata](/docs/meeting-metadata.md)*
