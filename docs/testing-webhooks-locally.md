---
title: "Testing Webhooks LocallyMoon (Dark Mode)Sun (Light Mode)"
description: "Test receiving and verifying Bot status event webhooks locally"
source_file: "docs/testing-webhooks-locally.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.907Z"
api_parameters_count: "0"
---
> **CALLOUT**:

## ☑️

Prerequisite

Before you can receive bot status change events locally, make sure you've set up [Local Webhook Development](/docs/local-webhook-development.md).

# Configuration

[](#configuration)
- * *

## Configure your endpoint

[](#configure-your-endpoint)

1.  Go to the [Recall dashboard](https://api.recall.ai/dashboard/webhooks/) and click **Add Endpoint**

    ![](https://files.readme.io/ce41f68-CleanShot_2024-01-18_at_22.47.24.png)
2.  In **Endpoint URL**, enter your static ngrok URL along with the path to your webhook handler.

    ![](https://files.readme.io/878d44e-CleanShot_2024-02-17_at_10.12.17.png)

## Configure your local server

[](#configure-your-local-server)

**Copy the signing secret for your new webhook endpoint**

![](https://files.readme.io/1f60dde-CleanShot_2024-02-17_at_10.14.56.png)

**Configure your server to use this secret locally.**

> **CALLOUT**:

## 📘

Use an environment variable

*Below the secret is hard-coded into our handler for demonstration purposes, but we recommend using an environment variable.*

*This will allow you to separate this sensitive value from version control and make configuring secrets for different environments much easier.*

JavaScriptpythonGo

```
import { Webhook } from "svix";
import bodyParser from "body-parser";

const secret = "whsec_yhVJ7lfTGMQDJY8YSq9aGcsw4I7/XJIz";

app.post('/webhook/recall', bodyParser.raw({type: 'application/json'}), (req, res) => {
    const payload = req.body;
    const headers = req.headers;

    const wh = new Webhook(secret);
    let msg;
    try {
        msg = wh.verify(payload, headers);
    } catch (err) {
        res.status(400).json({});
    }

    // Do something with the message...

    res.json({});
});

```

```
from fastapi import Request, Response, status

from svix.webhooks import Webhook, WebhookVerificationError

secret = "whsec_yhVJ7lfTGMQDJY8YSq9aGcsw4I7/XJIz"

@router.post("/webhook/recall", status_code=status.HTTP_204_NO_CONTENT)
async def webhook_handler(request: Request, response: Response):
    headers = request.headers
    payload = await request.body()

    try:
        wh = Webhook(secret)
        msg = wh.verify(payload, headers)
    except WebhookVerificationError as e:
        response.status_code = status.HTTP_400_BAD_REQUEST
        return

    # Do someting with the message...

```

```
package main

import (
	"fmt"
	"io"
	"log"
	"net/http"

	svix "github.com/svix/svix-webhooks/go"
)

// Configure your secret from above.
// Alternatively, use a local config file.
const secret = "whsec_yhVJ7lfTGMQDJY8YSq9aGcsw4I7/XJIz"

func main() {
	wh, err := svix.NewWebhook(secret)
	if err != nil {
		log.Fatal(err)
	}

	http.HandleFunc("/webhook/recall", func(w http.ResponseWriter, r *http.Request) {
		headers := r.Header
		payload, err := io.ReadAll(r.Body)
		if err != nil {
			fmt.Println("error:", err)
			w.WriteHeader(http.StatusBadRequest)
			return
		}

		err = wh.Verify(payload, headers)
		if err != nil {
			fmt.Println("error:", err)
			w.WriteHeader(http.StatusBadRequest)
			return
		}

		fmt.Printf("verified payload: %s", string(payload))

		// Do something with the message...

		w.WriteHeader(http.StatusNoContent)
	})

	fmt.Println("Starting server on port 8080")
	http.ListenAndServe(":8080", nil)
}

```

# Receive your first webhook events

[](#receive-your-first-webhook-events)

## Start your server and tunnel

[](#start-your-server-and-tunnel)

Start up your server and open an ngrok tunnel for your static domain, pointing it to the port of your local server.

**Example: Start a node.js server on port 3000 and expose it publicly at my-static-domain.ngrok-free.app**

Shell

```
# Start the server
npm run start --port 3000

# In a new terminal: Start the ngrok tunnel
ngrok http --domain my-static-domain.ngrok-free.app 3000

```

## Create a bot

[](#create-a-bot)

1.  Start an instant Google Meet call: [https://meet.google.com/](https://meet.google.com/)
2.  Call [Create Bot](/reference/bot_create.md), setting `meeting_url` to the URL of the meeting you just created.
3.  As the bot joins the call and starts recording, you should see your server receive the webhook events and verify their signatures successfully.

```
received event: {"data":{"data":{"code":"joining_call","updated_at":"2024-02-17T16:44:00.505440+00:00","sub_code":null}}, "bot": {"id": "92e24581-f82b-401a-8f75-88e64b04c24e", "metadata": {}}},"event":"bot.joining_call"}
received event: {"data":{"data":{"code":"in_waiting_room","updated_at":"2024-02-17T16:44:23.288984+00:00","sub_code":null}}, "bot": {"id": "92e24581-f82b-401a-8f75-88e64b04c24e", "metadata": {}}},"event":"bot.in_waiting_room"}
received event: {"data":{"data":{"code":"in_call_not_recording","updated_at":"2024-02-17T16:44:23.288984+00:00","sub_code":null}}, "bot": {"id": "92e24581-f82b-401a-8f75-88e64b04c24e", "metadata": {}}},"event":"bot.in_call_not_recording"}
received event: {"data":{"data":{"code":"in_call_recording","updated_at":"2024-02-17T16:44:23.288984+00:00","sub_code":null}}, "bot": {"id": "92e24581-f82b-401a-8f75-88e64b04c24e", "metadata": {}}},"event":"bot.in_call_recording"}

```
