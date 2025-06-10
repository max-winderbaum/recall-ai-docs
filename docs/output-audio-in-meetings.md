---
title: "Output AudioMoon (Dark Mode)Sun (Light Mode)"
description: "There are two primary methods of outputting audio from bots: Automatic audio output Calling the Output Audio endpoint Streaming audio into a call is can now be done with Output Media Platform Support Platform Available Zoom ✅ Google Meet ✅ Microsoft Teams ✅ Cisco Webex ✅ Slack Huddles ❌ Zoom Native ..."
source_file: "docs/output-audio-in-meetings.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.357Z"
api_parameters_count: "0"
---
There are two primary methods of outputting audio from bots:
- **Automatic audio output**
- **Calling the [Output Audio](/reference/bot_output_audio_create.md) endpoint**

Streaming audio into a call is can now be done with [Output Media](/docs/stream-media.md)

## Platform Support

[](#platform-support)

| Platform | Available |
| --- | --- |
| *Zoom | ✅ |
| Google Meet | ✅ |
| Microsoft Teams | ✅ |
| Cisco Webex | ✅ |
| Slack Huddles | ❌ |

*\*Zoom Native not yet supported.*

## Audio Format

[](#audio-format)

Audio should be provided as an mp3 encoded as a base 64 string.

MP3 files can easily be converted to a b64 string using CLI tools such as [ffmpeg](https://ffmpeg.org/) or an online tool such as [b64Guru](https://base64.guru/converter/encode/audio/mp3).

# Outputting Audio

[](#outputting-audio)
- * *

## Using `automatic_audio_output`

[](#using-automatic_audio_output)

[Create Bot](/reference/bot_create.md) accepts an `automatic_audio_output` configuration for automatically outputting audio when the bot starts recording, with the option to repeat the audio when participants join.

`data` allows you to specify the mp3 the bot should play.
- `kind` - The type of data encoded in the b64 string (Currently only `mp3` is supported)
- `b64_data` - Data encoded in Base64 format, using the standard alphabet (as specified [here](https://datatracker.ietf.org/doc/html/rfc4648#section-4))

`replay_on_participant_join` can be optionally used to repeat the audio whenever someone joins.
- `debounce_mode`: Debounce mode ("trailing" or "leading")
- `leading`: The debounce timer will start counting down when the first participant joins.
- `trailing`: The debounce timer will start counting down when the last participant joins.
- `debounce_interval`: The amount of time to wait for additional participants to join before replaying the audio.
- `disable_after`: The number of seconds after which the audio will no longer replay when new participants join. This parameter is useful to prevent the bot from interrupting a meeting, if a late participant joins.

**`automatic_audio_output` example**

JSON

```
// POST https://us-east-1.recall.ai/api/v1/bot/
{
  "automatic_audio_output": {
    "in_call_recording": {
      "data": {
        "kind": "mp3",
        "b64_data": "..."
      },
      "replay_on_participant_join": {
        "debounce_mode": "trailing",
        "debounce_interval": 10,
        "disable_after": 60
      }
    }
  },
  ...
}

```

Using the above configuration as an example, let's say we have the following scenario:
- Participant 1 is there a bit early and joins right before the bot starts recording.
- 5 seconds after recording starts, Participant 2 joins.
- 5 seconds later, Participant 3 joins.
- Participant 4 is running late, and joins the call three minutes after recording starts.

In this scenario, Participants 1 and 4's experiences are fairly straightforward.
- Participant 1 hears the audio played when the bot starts recording.
- Participant 4 never hears the audio played since they joined 180 seconds after the bot started recording, which is greater than the `disabled_after` value of 60.

Participants 2 and 3 will experience something slightly different based on the `debounce_mode`:
- In `trailing` mode, the audio would play 10 seconds after Participant 3 joins (15 seconds after Participant 2 joins).
- If we set the `debounce_mode` to `leading`, however, the audio will play 10 seconds after Participant 2 joins (5 seconds after Participant 3 joins).

## Using the Output Audio endpoint

[](#using-the-output-audio-endpoint)

If your use case requires more manual control over outputting bot audio, you can use the [Output Audio](/reference/bot_output_audio_create.md) endpoint.

This endpoint takes the same parameters as the bot configuration objects above:

```
// POST https://us-east-1.recall.ai/api/v1/bot/{id}/output_audio/
{
  "kind": "mp3",
  "b64_data": "..." // b64 encoded string
}

```

> **CALLOUT**:

## 📘

To use the [Output Audio](/reference/bot_output_audio_create.md) endpoint, currently bots must be configured with an `automatic_audio_output` in the [Create Bot](/reference/bot_create.md)request.

If you do not wish to leverage any automatic audio output, and just want to use the endpoint, we recommend adding a short silent mp3 file as the `b64_data` in this configuration.
