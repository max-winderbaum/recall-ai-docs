---
title: "Stream Audio/Video from Webpage to a MeetingMoon (Dark Mode)Sun (Light Mode)"
description: "Use Recall.ai's Output Media API to stream audio and video from a webpage directly to a meeting"
source_file: "docs/stream-media.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:12.115Z"
api_parameters_count: "0"
---
Recall supports streaming a webpage's audio and video to meetings via the bot's camera and microphone. This set of APIs is the perfect combination to build interactive AI agents that listen to the meeting and react in realtime. Some of our customers use this functionality to build AI-powered sales agents, coaches, recruiters, meeting planners and more.

For example implementations/use cases, see our demo repos:
- [AI Voice Agent Demo](https://github.com/recallai/voice-agent-demo)
- [Real-time Translator Demo](https://github.com/recallai/real-time-translator-demo)

## A specific example

[](#a-specific-example)

The following video demonstration shows an example of a bot reacting in real time to the conversation in the meeting.

<a target="\_self" href="https://www.loom.com/embed/bafb9727c2e049b2b55e07be0ff7bd80?sid=afbbb552-3a25-45e5-916a-d201774519d1" title="loom.com">iframe</a>

# Platform Support

[](#platform-support)

| Platform | Bot Configuration (output_media) |
| --- | --- |
| Zoom* | ✅ |
| Google Meet | ✅ |
| Microsoft Teams | ✅ |
| Cisco Webex | ✅ |
| Slack Huddles | ❌ |

*\*Zoom native bot not supported*

> **CALLOUT**:

## 🚧

Streaming Media incompatible with [`automatic_video_output`](/docs/output-video-in-meetings) and [`automatic_audio_output`](/docs/output-audio-in-meetings)

Bot Media Output cannot currently be used with [`automatic_video_output`](/docs/output-video-in-meetings) or [`automatic_audio_output`](/docs/output-audio-in-meetings).

The [Output Video](/reference/bot_output_video_create) and [Output Audio](/reference/bot_output_audio_create) endpoints must also **not** be used if your bot is streaming a webpage's contents to the meeting.

# Quickstart

[](#quickstart)
- * *

## Streaming a webpage's audio/video to a meeting

[](#streaming-a-webpages-audiovideo-to-a-meeting)

### Method 1: Using `output_media` in [Create Bot](/reference/bot_create)

[](#method-1-using-output_media-in--create-bot)

You can use the `output_media` configuration in the [Create Bot](/reference/bot_create) endpoint to stream the audio and video contents of a webpage to your meeting.

`output_media` takes the following parameters:
- `kind`: The type of media to stream (currently only `webpage` is supported)
- `config`: The webpage configuration (currently only supports `url`)

Let's look at an example call to [Create Bot](/reference/bot_create):

JSON

```
// POST /api/v1/bot/
{
  "meeting_url": "https://us02web.zoom.us/j/1234567890",
  "bot_name": "Recall.ai Notetaker",
  "output_media": {
    "camera": {
      "kind": "webpage",
      "config": {
        "url": "https://www.recall.ai"
      }
    }
  }
}

```

The example above tells Recall to create a bot that will continuously stream the contents of [recall.ai](https://www..recall.ai) to the provided meeting URL.

### Method 2: Using the [Output Media](/reference/bot_output_media_create) endpoint

[](#method-2-using-the-output-media-endpoint)

You can choose to start outputting media by calling the [Output Media](/reference/bot_output_media_create) endpoint at any point when the bot is in a call.

The parameters for the request are the same as the `output_media` configuration.

**Example cURL:**

cURL

```
curl --request POST \
     --url https://api.recall.ai/api/v1/bot/{bot_id}/output_media/ \
     --header 'Authorization: ${RECALL_API_KEY}' \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data-raw '
{
	"camera": {
    "kind": "webpage",
    "config": {
      "url": "https://recall.ai"
    }
  }
}
'

```

#### Stopping media output

[](#stopping-media-output)

You can stop the bot media output at any point while the bot is streaming media to a call by calling the [Stop Output Media](/reference/bot_output_video_destroy) endpoint.

**Example cURL:**

cURL

```
curl --request DELETE \
     --url https://api.recall.ai/api/v1/bot/{bot_id}/output_media/ \
     --header 'Authorization: ${RECALL_API_KEY}' \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
     --data-raw '{ "camera": true }'

```

## Accessing realtime meeting data

[](#accessing-realtime-meeting-data)

The bot exposes a Websocket endpoint to retrieve realtime meeting data while the webpage is streaming audio and video to the call. Right now, only realtime transcripts are supported. You can connect to the realtime API from your webpage with the following example:

JavaScript

```

const ws = new WebSocket('wss://meeting-data.bot.recall.ai/api/v1/transcript');

ws.onmessage = (event) => {
  const message = JSON.stringify(event.data);

  // .. your logic to handle realtime transcripts
};

ws.onopen = () => {
  console.log('Connected to WebSocket server');
};

ws.onclose = () => {
  console.log('Disconnected from WebSocket server');
};

```

The websocket messages coming from the `/api/v1/transcript` endpoint have the same shape as the `data` object in [Real-time transcription](/docs/real-time-transcription#events) .



## Piping the meeting audio to the webpage

[](#piping-the-meeting-audio-to-the-webpage)

Output media bots configure an input device inside the running webpage that receives the mixed meeting audio of all participants.

You can access a [`MediaStream`](https://developer.mozilla.org/en-US/docs/Web/API/MediaStream) object and its audio track from the webpage running inside the bot. The following example shows how to get samples of the meeting audio in [`AudioData`](https://developer.mozilla.org/en-US/docs/Web/API/AudioData) objects:

javascript

```

const mediaStream =   await navigator.mediaDevices.getUserMedia({ audio: true });
const meetingAudioTrack = mediaStream.getAudioTracks()[0];

const trackProcessor = new MediaStreamTrackProcessor({ track: meetingAudioTrack });
const trackReader = trackProcessor.readable.getReader();

while (true) {
  const { value, done } = await trackReader.read();
  const audioData = value;
  ... // Do something with the audio data
}

```



# Debugging

[](#debugging)
- * *

## Debugging your webpage with remote Devtools

[](#debugging-your-webpage-with-remote-devtools)

During the development process, you may need to debug your output media bot's webpage. Recall provides an easy way to connect to the webpage's [Chrome Devtools](https://developer.chrome.com/docs/devtools) while the bot is running. Check the video demo below and read the following instructions to learn how to access your bot's Devtools.


<a target="\_self" href="https://www.loom.com/embed/88268f164d164e809faba0befcb3b5c4?sid=d98036aa-c98e-426e-bd0a-2e56cec80c5c" title="loom.com">iframe</a>

1.  Send an output media bot to your meeting, and wait for its output media stream
2.  [Log in](https://www.recall.ai/login) to your Recall.ai dashboard
3.  Select Bot Explorer in the sidebar
4.  In the Bot Explorer app, search for your bot by ID

![](https://files.readme.io/45ba45d4f1d96e38c59e91b37ae4325c5066d21f8193a8a9ec98888ffa6dced7-image.png)

5.  Open the "Debug Data" tab for your bot then under CPU Metrics, click the "Open Remote Devtools" button. A devtools inspector connected to your live bot will open in a new tab

    ![](https://files.readme.io/12013f339d96e728aa6177faed2ab9d9d789f2012cdf43ee384d9904ccd562e3-CleanShot_2025-04-11_at_13.23.082x.png)


> **CALLOUT**:

## 📘

Bot must be alive

Since Output Media Devtools are exposed by the bot itself and CPU metrics are in real-time, they are only available when the bot is actively in a call.

You can also view the CPU usage for an individual bot in the "Bot Details" section. You can use this graph to uncover any performance bottlenecks with your webpage which might be causing the webpage to lag or perform poorly.

![](https://files.readme.io/2003b2475688e3109aeb12172426f2a153f5d276931e3bd0528209714f796c6a-CleanShot_2024-12-09_at_11.36.22.png)

## Addressing audio and video issues: 4 core bots

[](#addressing-audio-and-video-issues-4-core-bots)

While we expose CPU metrics to help you identify and address any performance issues on your end, sometimes this is out of your control and you just need more CPU power.

The streaming media functionality runs in isolation from the bot producing the final meeting recording. Below is a breakdown of the compute resources available to the instance running your webpage:

| Variant | CPU | Memory |
| --- | --- | --- |
| web | 250 millicores | 750MB |
| web_4_core | 2250 millicores | 5250MB |
| native | ❌ Unsupported | ❌ Unsupported |

To enable this, you can specify 4-core bots in your [Create Bot](/reference/bot_create) request by using the `variant` parameter:

JSON

```
{
  ...
  "variant": {
    "zoom": "web_4_core",
    "google_meet": "web_4_core",
    "microsoft_teams": "web_4_core"
  }
}

```

These bots run on larger machines, which can help address any CPU bottlenecks hindering the audio & video quality of your Output Media feature.

> **CALLOUT**:

## ❗️

Important

Due to the inherent cost of running larger machines, 4-core bots are priced as following:
- **Pay-as-you-go plan:** $1.10/hour
- **Monthly plans:** $0.10/hour on top of your standard bot usage rate.

# FAQ

[](#faq)
- * *

## Do you support WebGL?

[](#do-you-support-webgl)

Our bots do not have GPU's so WebGL is not currently supported.

## What are the browser dimensions of the webpage?

[](#what-are-the-browser-dimensions-of-the-webpage)

1280x720px
