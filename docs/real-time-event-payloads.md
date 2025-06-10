---
title: "Real-Time Event PayloadsMoon (Dark Mode)Sun (Light Mode)"
description: "participant_events transcript.data transcript.partial_data audio_mixed_raw.data audio_separate_raw.data video_separate_png.data"
source_file: "docs/real-time-event-payloads.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.569Z"
api_parameters_count: "0"
---
# `participant_events`

[](#participant_events)

JSON

```
{
  "event": "participant_events.chat_message", // participant_events.join, participant_events.leave, participant_events.speech_on, participant_events.speech_off (& more)
  "data": {
    "data": {
      "participant": {
      	"id": number,
      	"name": string | null,
        "is_host": boolean,
        "platform": string | null,
        "extra_data": object
    	},
      "timestamp": {
        "absolute": string,
        "relative": float
      },
      "data":
      	{
          "text": string,
          "to": string
        } // populated for `participant_events.chat_message` event
      	| null
    },
    // The real-time endpoint configured to receive data
    "realtime_endpoint": {
      "id": string,
      "metadata": object,
    },
    // The associated ParticipantEvents Resource encapsulating this data
    "participant_events": {
      "id": string,
      "metadata": object
    },
    "recording": {
      "id": string,
      "metadata": object
    },
    // The related bot, if the recording is produced by a bot
    "bot": {
      "id": string,
      "metadata": object
    }
  }
}

```



# `transcript.data`

[](#transcriptdata)

JSON

```
{
  "event": "transcript.data",
  "data": {
    "data": {
      "words": [{
        "text": string,
        "start_timestamp": { "relative": float },
        "end_timestamp": {"relative": float } | null
      }],
      "participant": {
      	"id": number,
      	"name": string | null,
        "is_host": boolean,
        "platform": string | null,
        "extra_data": object
      }
    },
    "realtime_endpoint": {
      "id": string,
      "metadata": object,
    },
    "transcript": {
      "id": string,
      "metadata": object
    },
    "recording": {
      "id": string,
      "metadata": object
    },
    "bot": {
      "id": string,
      "metadata": object
    }
  }
}

```



# `transcript.partial_data`

[](#transcriptpartial_data)

JSON

```
{
  "event": "transcript.partial_data",
  "data": {
    "data": {
      "words": [{
        "text": string,
        "start_timestamp": { "relative": float },
        "end_timestamp": {"relative": float } | null
      }],
      "participant": {
      	"id": number,
      	"name": string | null,
        "is_host": boolean,
        "platform": string | null,
        "extra_data": object
      }
    },
    "realtime_endpoint": {
      "id": string,
      "metadata": object,
    },
    "transcript": {
      "id": string,
      "metadata": object
    },
    "recording": {
      "id": string,
      "metadata": object
    },
    "bot": {
      "id": string,
      "metadata": object
    }
  }
}

```



# `audio_mixed_raw.data`

[](#audio_mixed_rawdata)

JSON

```
{
  "event": "audio_mixed_raw.data",
  "data": {
    "data": {
      "buffer": string, // base64-encoded raw audio 16 kHz mono, S16LE(16-bit PCM LE)
      "timestamp": {
      	"relative": float,
        "absolute": string
    	}
    },
    "realtime_endpoint": {
      "id": string,
      "metadata": object,
    },
    "audio_mixed": {
      "id": string,
      "metadata": object
    },
    "recording": {
      "id": string,
      "metadata": object
    },
    "bot": {
      "id": string,
      "metadata": object
    },
  }
}

```



# `audio_separate_raw.data`

[](#audio_separate_rawdata)

JSON

```
{
  "event": "audio_separate_raw.data",
  "data": {
    "data": {
      "buffer": string, // base64-encoded raw audio 16 kHz mono, S16LE(16-bit PCM LE)
      "timestamp": {
      	"relative": float,
        "absolute": string
    	},
      "participant": {
      	"id": number,
      	"name": string | null,
        "is_host": boolean,
        "platform": string | null,
        "extra_data": object
      }
    },
    "realtime_endpoint": {
      "id": string,
      "metadata": object,
    },
    "audio_separate": {
      "id": string,
      "metadata": object
    },
    "recording": {
      "id": string,
      "metadata": object
    },
    "bot": {
      "id": string,
      "metadata": object
    },
  }
}

```



# `video_separate_png.data`

[](#video_separate_pngdata)

JSON

```
{
  "event": "video_separate_png.data",
  "data": {
    "data": {
      "buffer": string, // base64 encoded png at 2fps with resolution 360x640
      "timestamp": {
      	"relative": float,
        "absolute": string
    	},
      "type": "webcam" | "screenshare",
      "participant": {
      	"id": number,
      	"name": string | null,
        "is_host": boolean,
        "platform": string | null,
        "extra_data": object
      }
    },
    "realtime_endpoint": {
      "id": string,
      "metadata": object,
    },
    "video_separate": {
      "id": string,
      "metadata": object
    },
    "recording": {
      "id": string,
      "metadata": object
    },
    "bot": {
      "id": string,
      "metadata": object
    },
  }
}

```
