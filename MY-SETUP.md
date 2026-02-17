# My Clawdbot Setup

## Quick Start

```bash
cd C:\dev\clawdbot
node dist/entry.js gateway
```

## My Configuration

- **Phone:** +972586135417
- **Mode:** Personal WhatsApp (selfChatMode)
- **Model:** Claude Opus 4.5
- **Gateway:** ws://127.0.0.1:18789

## Commands

### Start the bot

```bash
node dist/entry.js gateway
```

### Re-link WhatsApp (if disconnected)

```bash
node dist/entry.js channels login
```

### Check status

```bash
node dist/entry.js channels status
```

### View logs

```bash
node dist/entry.js logs --follow
```

### Stop the bot

Press `Ctrl+C` in the terminal running the gateway.

## How to Use

1. Open WhatsApp on your phone
2. Go to "Message yourself" (or any chat if configured)
3. Send a message - the bot will respond

## Config Location

`C:\Users\User\.clawdbot\clawdbot.json`

## Workspace

`C:\Users\User\clawd`

## Troubleshooting

**Bot not responding?**

- Check gateway is running: `node dist/entry.js gateway`
- Re-link WhatsApp: `node dist/entry.js channels login`

**Need to rebuild after updates?**

```bash
git pull
pnpm install
pnpm build
```
