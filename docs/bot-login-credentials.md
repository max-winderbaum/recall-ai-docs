---
title: "Bot Login CredentialsMoon (Dark Mode)Sun (Light Mode)"
description: "❗️ This method for setting up authenticated Google Meet bots has been deprecated. Please refer to the guide in below link to setup authenticated Google Meet bots:: Setup Authenticated Google Meet Bot By default the Google Meet bot joins every meeting as a guest participant. This can lead to certain ..."
source_file: "docs/bot-login-credentials.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:14.747Z"
api_parameters_count: "0"
---
> **CALLOUT**:

## ❗️

This method for setting up authenticated Google Meet bots has been deprecated. Please refer to the guide in below link to setup authenticated Google Meet bots:

[Setup Authenticated Google Meet Bot](google-meet-login-getting-started)

By default the Google Meet bot joins every meeting as a guest participant. This can lead to certain limitations (e.g not having a configurable avatar).

In order to avoid, Recall supports authorized Google Meet bot participant i.e bots will be able to sign in using configurable credentials before joining a meeting.

## Creating Bot Account

[](#creating-bot-account)

1.  Use a fresh google account for the bot.
2.  Ensure to set both **recovery email** & **recovery phone number** on the bot account. Failure to do so can result in the bot running into "BOT\_SIGN\_IN\_FAILED" errors.
3.  Ensure the bot account language is set to **English(US)**.

## How login credentials work

[](#how-login-credentials-work)

1.  If `Login Mandatory` is turned on, the bot will login with the credentials before joining every call.
2.  If `Login Mandatory` is turned off, the bot will only attempt to login for calls that require the participants to be signed in.
3.  The `bot_name` field does not work for logged in bots as Google Meet does not support customising name for logged in participants.

## Login Methods

[](#login-methods)

![](https://files.readme.io/a07ae06-image.png)

There are several methods that the bot can use to log-in. Each method requires it's own set of credentials, and these can be configured in the dashboard under the [Google Meet Credentials tab](https://api.recall.ai/dashboard/platforms/gmeet).

### SSO V2 (Green Box) (Recommended)

[](#sso-v2-green-box-recommended)

This is currently the recommended method to have Google Meet bots sign in to the call. This method is the fastest and most reliable sign-in method.

You can set up SSO V2 using the following steps:

1.  Create a dedicated Google Workspace that contains a bot user.
    1.  You must have a paid workspace, it can be on the cheapest (starter) tier and only needs one user account
    2.  You can use any domain, either a new domain that you register for this purpose, or a subdomain of your primary domain. For instance `sso.yourcompany.com`.
    3.  **You cannot reuse your existing Google Workspace if you already have one.** The reason is because this method relies on the organisation-wide SSO policy which could break your existing Google accounts.
2.  Configure an user in your workspace which the bot will authenticate as.
    1.  Fill **username** field in the dashboard with the email address of the bot account. For e.g if the bot's account is `bot@sso.yourcompany.com` then **username = [bot@sso.yourcompany.com](mailto:bot@sso.yourcompany.com)**. **Incorrect username value will cause the bot to be stuck in joining\_call state**.
    2.  **The bot will join the meetings using the name of this google account, you can specify the name to be what makes sense for your use case.**
    3.  This will override the `bot_name` parameter in [Create Bot](/reference/bot_create.md) endpoint, this is a limitation of authenticated Google Meet bots.
3.  Ensure you login to the user account at least once, in order to accept the new account disclaimer.
    1.


![](https://files.readme.io/4f82faa-image_3.png)

2.  **If you skip this step the bot will get stuck in the `joining_call` state**
3.  Create an RSA private key and self-signed certificate: `openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -sha256 -days 3650 -nodes`. Store these files somewhere safe!
4.  In Google Workspace admin, set up an SSO profile for the organisation:
    1.


![](https://files.readme.io/b561cfa-Screenshot_2023-07-13_at_2.21.29_pm.png)

2.


![](https://files.readme.io/2952082-Screenshot_2023-07-13_at_2.28.35_pm.png)

3.  Check "*Set up SSO with third-party provider*"
    1.  *Sign-in page URL:* `https://us-east-1.recall.ai/api/v1/bot/gmeet-sign-in`
    2.  *Sign-out page URL:* `https://us-east-1.recall.ai/api/v1/bot/gmeet-sign-out`
    3.  *Verification certificate*: Upload the `cert.pem` file created in step 3
    4.  Check "*Use a domain-specific issuer*"
    5.  Scroll to the bottom and click "*Save*"
4.  Back in your Recall Dashboard: [https://us-east-1.recall.ai/dashboard/platforms/gmeet](https://us-east-1.recall.ai/dashboard/platforms/gmeet) fill out the following
    1.  *SSO V2 - Google Workspace Domain:* the domain of your google workspace, eg `sso.yourcompany.com`
    2.  *SSO V2 - Private Key (PEM):* the `key.pem` file created in step 3
    3.  *SSO V2 - Certificate (PEM):* the `cert.pem` file created in step 3
    4.  *Login Mandatory*: check this box

### Username/Password (Red Box)

[](#usernamepassword-red-box)

This is the most basic and straightforward sign-in method, where the bot uses the username and password of the Google account to sign in. However this method is the slowest, and can sometimes fail if Google rejects the request or displays a CAPTCHA.

You can setup Username/Password sign-in through the following steps:

1.  Create a new Google Account for the bot, and note the username, password, recovery email and recovery phone number.
2.  Input these values in the Recall Dashboard

### SSO V1 (Blue Box)

[](#sso-v1-blue-box)

Deprecated - please use SSO V2 above.

#### Migration from SSO V1

[](#migration-from-sso-v1)

If you currently have bots signing in using SSO V1, you will want to temporarily disable SSO by unchecking Login Mandatory in your Recall Dashboard before the cutover.

This is so your existing bots do not fail to authenticate using the SSO V1 method after you change the signing certificate in your Google Workspace.
