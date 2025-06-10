---
title: "AuthenticationMoon (Dark Mode)Sun (Light Mode)"
description: "Start making requests to the Recall API."
source_file: "reference.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:15.488Z"
api_parameters_count: "0"
---
# API Keys

[](#api-keys)

API keys are used to authenticate to the Recall.ai platform.

You can create and manage your API keys in the Recall dashboard:
- [(US) us-east-1](https://us-east-1.recall.ai/dashboard/api-keys)
- [(Pay-as-you-go) us-west-2](https://us-west-2.recall.ai/dashboard/api-keys)
- [(EU) eu-central-1](https://eu-central-1.recall.ai/dashboard/api-keys)
- [(JP) ap-northeast-1](https://ap-northeast-1.recall.ai/dashboard/api-keys)

> **CALLOUT**:

## 📘

API keys belong to individual users, but access is environment-scoped. This means that multiple accounts under the same environment share access to the same resources, but have their own API keys.

# HTTP Header: Token Authorization

[](#http-header-token-authorization)

All requests must be authenticated via token in the HTTP `Authorization` header in the following format:

```
Authorization: Token YOUR_API_KEY

```

For e.g if you Recall API Key is `abcdefghijklmnopqrst` then the following should be the authorization header

```
Authorization: Token abcdefghijklmnopqrst

```

Unauthenticated requests will receive a 401 error: `401: Unauthorized`.
- [Table of Contents](#)
- -   [API Keys](#api-keys)
- [HTTP Header: Token Authorization](#http-header-token-authorization)
