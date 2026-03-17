---
summary: "MAX (Mail.ru) channel status and integration path"
read_when:
  - You want to connect OpenClaw to MAX
  - You are evaluating custom channel plugin support
title: "MAX"
---

# MAX (Mail.ru)

Status: not bundled yet.

OpenClaw does not currently ship a built-in MAX channel plugin. You can still add MAX support through the channel-plugin system.

## Current recommendation

- If you need MAX now, implement it as a plugin via `api.registerChannel({ plugin })`.
- Use the channel plugin guide for required channel adapters, onboarding hooks, and config shape.
- Keep channel config under `channels.max`.

References:

- [Plugins](/tools/plugin)
- [Chat Channels](/channels)

## Suggested config shape

Use a dedicated channel section for MAX account credentials and policy:

```json5
{
  channels: {
    max: {
      enabled: true,
      accounts: {
        default: {
          accountId: "default",
          token: "MAX_BOT_TOKEN",
        },
      },
      dmPolicy: "pairing",
    },
  },
}
```

## Minimal implementation checklist

1. Register channel metadata (`id`, `label`, `docsPath`, `selectionLabel`).
2. Implement account resolution (`listAccountIds`, `resolveAccount`).
3. Implement outbound text (`outbound.sendText`) and target normalization.
4. Add inbound monitor/webhook bridge for MAX events.
5. Add pairing and DM/group policy handling.
6. Add status probes and troubleshooting notes.

When MAX support is bundled in OpenClaw, this page will be updated with the native setup flow.
