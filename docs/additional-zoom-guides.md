---
title: "Zoom Signed-in BotsMoon (Dark Mode)Sun (Light Mode)"
description: "Zoom Web bots will emit a fatal error indicating \"Sign In Required\" if they attempt to join a Zoom meeting where the host has enabled \"Only Authenticated Users can Join\" : Enabling this setting means that only users who are logged in to a Zoom account are permitted to join the meeting. Because the b..."
source_file: "docs/additional-zoom-guides.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:10.943Z"
api_parameters_count: "0"
---
[Zoom Web bots](https://recallai.readme.io/reference/zoom#zoom-web) will emit a `fatal`error indicating "Sign In Required" if they attempt to join a Zoom meeting where the host has enabled ["Only Authenticated Users can Join"](https://support.zoom.com/hc/en/article?id=zm_kb&sysparm_article=KB0063837):

![](https://files.readme.io/5df8b2a031760d2b49997b5de87ef585f013fa27f7a4b20a0e0c62ffb63f631a-CleanShot_2025-01-16_at_08.52.54.png)

Enabling this setting means that only users who are logged in to a Zoom account are permitted to join the meeting. Because the bot is not logged in by default, it will not be able to join the meeting.

To enable the bot to join these meetings, you must provide it with a Zoom ZAK token.

> **CALLOUT**:

## 📘

ZAK tokens also allow bots to start meetings on behalf of the user. This can be useful if you want the bot to be able to join or start a meeting on behalf of a user, before they've joined.

Bots that are provided a ZAK token will also appear as the underlying account of the Zoom user that generated the token. This includes the avatar of the user's profile.

## What is a Zoom ZAK Token and how do I get one?

[](#what-is-a-zoom-zak-token-and-how-do-i-get-one)

A ZAK token is a access token that can be [generated through the Zoom API](https://developers.zoom.us/docs/meeting-sdk/auth/#start-meetings-and-webinars-with-a-zoom-users-zak-token). These tokens are short-lived, and must be regenerated frequently.

**Note: *any* ZAK token from *any* Zoom user can be used to authenticate the bot in *any* meeting.**

We recommend creating a dedicated Zoom account for the purpose of generating ZAK tokens, and using that account's ZAK tokens to authenticate all your bots. This means you **don't** need to retrieve the ZAK token from your user's Zoom account.

## How do I provide a ZAK token to the bot?

[](#how-do-i-provide-a-zak-token-to-the-bot)

To provide the ZAK token to the bot, you must specify the `zoom.zak_url` when creating the bot. The `zoom.zak_url` is a URL **on your server** which returns the ZAK token as a plain text HTTP response. Some example pseudocode:

Python

```
def validate_callback_token(token) -> bool:
  """We attach a token in the query parameter of the URL we provide Recall.
  By verifying the presence and validity of this token,  we can authenticate
  incoming requests to our callback URL."""
  pass

def retrieve_zak_token() -> str:
  """This function retrieves a Zoom ZAK token. Note that the response returned
  by calling Zoom's API is a JSON object, and we must extract the token to return a string.
  (https://developers.zoom.us/docs/api/rest/reference/zoom-api/methods/#operation/userZak)
  """
  zoom_api_response = call_zoom_api_userZak()
  return zoom_api_response['token']

# HTTP handler for https://example.com/recall/callbacks/zak
def http_handler(request):
  if not valdate_callback_token(request.query_parameters['token']):
    return HttpResponse(code=401)

  zak_token = retrieve_zak_token()
  return HttpResponse(body=zak_token)



```
