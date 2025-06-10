---
title: "Google Meet FAQMoon (Dark Mode)Sun (Light Mode)"
description: "Frequently asked questions about Google Meet bots."
source_file: "docs/google-meet-faq.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:11.487Z"
api_parameters_count: "0"
---
## Can the bot skip the waiting room?

[](#can-the-bot-skip-the-waiting-room)

If the bot is [signed in to a Google account](/reference/google-meet-login-getting-started), and that account's email address has been added to the meeting invite, then it will be able to skip the waiting room and directly enter the meeting.

## The bot shows as in\_waiting\_room, but I don't see the pop-up?

[](#the-bot-shows-as-in_waiting_room-but-i-dont-see-the-pop-up)

If a bot was sent to a Google Meet meeting, but your user didn't see it ask to be let in from the waiting room, it's likely because they were not the host of the meeting.

If the meeting was organized by someone else, by default, they won't be able to let anyone in (and won't see any indication of the bot asking to be let in), as only the "Hosts" will see popups to let participants in from the waiting room.

If none of the Hosts are in the call yet, nobody will see a pop-up to let the bot in. Once the host joins, then the host will see the pop-up appear.

Participants whose email address is on the event invite are able to join with no host present, so other invited participants may join before the host and wonder why the bot is not joining.

This behavior can be configured as shown [here](https://support.google.com/a/answer/13722774?hl=en), but since you likely don't want to ask someone to change their Google workspace settings, we recommend informing the host/organizer of the meeting that you've invited a bot. This way, there is no confusion and there's no need for them to change their settings.

## How do I change the bot's icon in the participants list?

[](#how-do-i-change-the-bots-icon-in-the-participants-list)

By default, the bot's icon in the Google Meet's participant list will be the first letter of it's name, in a circle of random color such as the following:

![](https://files.readme.io/b6dba0a-CleanShot_2024-06-04_at_15.48.432x.png)

The only way to change this to something else is to have the bot join as a [Signed-In Google Meet Bot](/docs/google-meet-login-getting-started). If the bot is signed in, it's icon will be the profile picture of the account it's signed in to.



## Why did my bot fail to join a meeting with `google_meet_bot_blocked` status code?

[](#why-did-my-bot-fail-to-join-a-meeting-with-google_meet_bot_blocked-status-code)

Google has some detection metrics in place to automatically block unwanted users from joining calls for various reasons

One of the main reasons are when the bot name contains certain words (curses, profane language, or other trigger words). Other related times, the filter can be triggered by seemingly innocent names and phrases. To test this issue, join a Google Meet call from an incognito browser window with the name you're testing. If you're rejected, you'll need to modify the name until it's accepted by Google

Other times, a separate detection metric can cause the bot to be flagged as a false positive. In this case, we recommend implementing Signed-in Google Meet bots and that will reduce the number of encounters

# Authenticated Bots

[](#authenticated-bots)
- * *

## What's the concurrency limit per Google Login?

[](#whats-the-concurrency-limit-per-google-login)

Based on our testing, the concurrency limit for a single Google Login is *roughly* 50, but this number isn't made public by Google and can have a high degree of variance.

Because of this, Recall adds an extra buffer which will kick in at 30 concurrent logins and assigns a different account to the bot. You should use this number as a heuristic for determining the number of logins you need, but we recommend also erring on the side of caution by adding an extra buffer yourself.



## What happens when all of my Google Logins are at their login limit?

[](#what-happens-when-all-of-my-google-logins-are-at-their-login-limit)

When the limit is reached for all accounts, you'll receive a fatal event with the sub code `google­_meet­_login­_not­_available` and you should create a new user to increase your concurrency limit.



## Can I use the same Google Workspace for multiple Recall accounts/environments?

[](#can-i-use-the-same-google-workspace-for-multiple-recall-accountsenvironments)

Yes - you shouldn't have any issues with sharing the same Google Workspace across multiple accounts.



## Can multiple bots using the same login join the same meeting?

[](#can-multiple-bots-using-the-same-login-join-the-same-meeting)

No - one login can only be used by one bot to join the same meeting. While one login can be shared among bots joining different meetings, same-meeting support for the same login isn't currently supported.



## Can I enable authenticated Google Meet bots for some meetings, but use the default behavior for others?

[](#can-i-enable-authenticated-google-meet-bots-for-some-meetings-but-use-the-default-behavior-for-others)

Yes! To configure authentication behavior for Google Meet, you can use the `google_meet.login_required` parameter in [Create Bot](/reference/bot_create).

If this parameter is absent in the request body, bots will authenticate **only if** the Google Meet is sign-in only. Otherwise, the bot will default to joining as an anonymous user.

If you set `google_meet.login_required` to `true`, bots will **always** join Google Meet calls as authenticated users, regardless of the meeting's joining requirements.



## Why does the meeting title in the bot's metadata different from the actual title?

[](#why-does-the-meeting-title-in-the-bots-metadata-different-from-the-actual-title)

This occurs when the bot joins a Google Meet meeting where the end time is has already past. Google Meet doesn't show the real title after the meeting has ended so it is not possible to get the meeting title
