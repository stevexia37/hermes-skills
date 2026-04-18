---
name: feishu-file-transfer
category: productivity
description: Upload files to Feishu (Lark) and send them as file messages via the Feishu Open API.
trigger: Use when you need to deliver a generated local file to a Feishu chat.
---

# Feishu File Transfer via Open API

## Overview

Upload a local file to Feishu's file service and send it as a file message to a direct-message or group channel.

## Prerequisites

- `FEISHU_APP_ID` and `FEISHU_APP_SECRET` are available in the current environment or profile config
- the target `chat_id` is known and verified
- the local file exists and is readable

## Step 1: Read Credentials

Avoid hard-coding credentials in the skill. Load them from environment or a profile-specific configuration source.

Example:

```bash
printenv FEISHU_APP_ID
printenv FEISHU_APP_SECRET
```

## Step 2: Resolve the Target Chat ID

Do not rely on long-term memory for routing. Read the currently active chat/channel mapping from the current profile or routing metadata.

Example pattern:

```bash
cat ~/.hermes/profiles/{profile_name}/channel_directory.json
```

Use the active Feishu channel ID from the current profile.

## Step 3: Request a Tenant Access Token

```python
import urllib.request, urllib.parse, json

app_id = "YOUR_APP_ID"
app_secret = "YOUR_APP_SECRET"

data = urllib.parse.urlencode({
    "app_id": app_id,
    "app_secret": app_secret,
}).encode()

req = urllib.request.Request(
    "https://open.feishu.cn/open-apis/auth/v3/tenant_access_token/internal",
    data=data,
)
resp = urllib.request.urlopen(req)
token = json.loads(resp.read())["tenant_access_token"]
```

## Step 4: Upload the File

```python
import json

file_path = "/path/to/file.pdf"
file_name = "file.pdf"
boundary = "----WebKitFormBoundary7MA4YWxkTrZu0gW"

body = b"------WebKitFormBoundary7MA4YWxkTrZu0gW\\r\\n"
body += b'Content-Disposition: form-data; name="file_type"\\r\\n\\r\\npdf\\r\\n'
body += b"------WebKitFormBoundary7MA4YWxkTrZu0gW\\r\\n"
body += (f'Content-Disposition: form-data; name="file_name"\\r\\n\\r\\n{file_name}\\r\\n').encode("utf-8")
body += b"------WebKitFormBoundary7MA4YWxkTrZu0gW\\r\\n"
body += (f'Content-Disposition: form-data; name="file"; filename="{file_name}"\\r\\nContent-Type: application/pdf\\r\\n\\r\\n').encode("utf-8")

with open(file_path, "rb") as f:
    body += f.read()

body += b"\\r\\n------WebKitFormBoundary7MA4YWxkTrZu0gW--\\r\\n"

req = urllib.request.Request(
    "https://open.feishu.cn/open-apis/im/v1/files",
    data=body,
    headers={
        "Authorization": "Bearer " + token,
        "Content-Type": "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    },
)
resp = urllib.request.urlopen(req)
file_key = json.loads(resp.read())["data"]["file_key"]
```

## Step 5: Send the File Message

```python
import json

chat_id = "oc_xxxxxxxxxxxxxxxxx"
content = json.dumps({"file_key": file_key})

data = json.dumps({
    "receive_id": chat_id,
    "msg_type": "file",
    "content": content,
}).encode("utf-8")

req = urllib.request.Request(
    "https://open.feishu.cn/open-apis/im/v1/messages?receive_id_type=chat_id",
    data=data,
    headers={
        "Authorization": "Bearer " + token,
        "Content-Type": "application/json; charset=utf-8",
    },
)
resp = urllib.request.urlopen(req)
result = json.loads(resp.read())
```

## Pitfalls

1. Wrong `chat_id` is the most common failure. Always resolve it from current routing metadata rather than stale memory.
2. System Python may not include `requests`; `urllib.request` is a safe built-in fallback.
3. Multipart uploads require exact CRLF handling.
4. `tenant_access_token` expires. Refresh on `401` or `403`.
5. The `content` field must be a JSON-encoded string, not a raw object.

## Security Rules

- Never hard-code production credentials
- Never publish real app IDs, secrets, or chat IDs
- Keep delivery routing profile-aware rather than user-specific
