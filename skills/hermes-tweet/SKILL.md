---
name: hermes-tweet
category: social
description: Install and use Hermes Tweet for X/Twitter research, tweet reads, reply reads, user lookup, follower exports, monitoring, and explicitly gated posting workflows.
trigger: Use when a Hermes workflow needs X/Twitter data, social monitoring, tweet context, user or follower lookup, or a reviewed social action path.
---

# Hermes Tweet

## Why This Exists

Hermes workflows often need current X/Twitter context before writing reports,
monitoring launch signals, checking account activity, or preparing social
updates. Hermes Tweet provides that capability as a native Hermes plugin while
keeping action tools explicitly gated.

## Install

```bash
hermes plugins install Xquik-dev/hermes-tweet --enable
```

## Environment Variables

- `XQUIK_API_KEY` enables read, lookup, export, and monitoring workflows.
- `HERMES_TWEET_ENABLE_ACTIONS=true` is required before post, reply, DM, or
  other action tools are available.

Store credentials in the Hermes runtime environment. Do not put keys, account
material, or session details in skill files, examples, or shared notes.

## Reusable Workflow

1. Confirm the plugin is installed and enabled.
2. Start with read-only tools for tweet, reply, user, follower, or monitor
   context.
3. Summarize results with links, account handles, query terms, and timestamps.
4. If the user asks for an action, draft the exact text first.
5. Confirm the target account, destination, text, and action gate before
   dispatch.

## Safety Notes

- A research request does not imply permission to post.
- Never invent engagement metrics or account state.
- Do not persist private credentials or raw account material in outputs.
- Keep action workflows reviewable and reversible where possible.

Repository: <https://github.com/Xquik-dev/hermes-tweet>
