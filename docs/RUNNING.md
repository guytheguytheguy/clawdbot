# Running OpenClaw

This guide covers all the ways to run OpenClaw locally for development and production.

## Quick Reference

| Script               | Description                |
| -------------------- | -------------------------- |
| `pnpm openclaw`      | Main CLI entry point       |
| `pnpm start`         | Alias for `pnpm openclaw`  |
| `pnpm dev`           | Run via node scripts       |
| `pnpm tui`           | Terminal UI                |
| `pnpm tui:dev`       | Terminal UI (dev profile)  |
| `pnpm gateway:dev`   | Gateway without channels   |
| `pnpm gateway:watch` | Gateway with file watching |

## Gateway Modes

### Standard Gateway

```bash
# Default gateway
pnpm openclaw gateway

# Custom port
pnpm openclaw gateway --port 18789

# Force start (kills existing process)
pnpm openclaw gateway --force

# Loopback only
pnpm openclaw gateway --bind loopback
```

### Development Gateway

Skip channel initialization for faster startup:

```bash
pnpm gateway:dev
```

Reset and start fresh:

```bash
pnpm gateway:dev:reset
```

Watch mode (auto-restart on file changes):

```bash
pnpm gateway:watch
```

## Terminal UI (TUI)

```bash
# Production TUI
pnpm tui

# Development TUI (isolated state)
pnpm tui:dev
```

## Agent Mode

Run agent turns directly:

```bash
# Basic agent call
pnpm openclaw agent --message "Hello"

# With delivery to recipient
pnpm openclaw agent --to +15555550123 --message "Summary" --deliver

# RPC mode (JSON output)
pnpm openclaw:rpc
pnpm moltbot:rpc
```

## Environment Variables

| Variable                 | Description                 |
| ------------------------ | --------------------------- |
| `OPENCLAW_SKIP_CHANNELS` | Skip channel initialization |
| `CLAWDBOT_SKIP_CHANNELS` | Alias for above             |
| `OPENCLAW_PROFILE`       | Named profile to use        |
| `CLAWDBOT_PROFILE`       | Alias for above             |
| `OPENCLAW_LIVE_TEST`     | Enable live tests           |

## Profiles

Profiles isolate state under `~/.openclaw-<name>`:

```bash
# Use dev profile
pnpm openclaw --dev gateway

# Use named profile
pnpm openclaw --profile staging gateway

# Set profile via environment
OPENCLAW_PROFILE=dev pnpm openclaw gateway
```

## State Directories

| Profile | State Directory       |
| ------- | --------------------- |
| Default | `~/.openclaw/`        |
| Dev     | `~/.openclaw-dev/`    |
| Custom  | `~/.openclaw-<name>/` |

## Ports

| Mode       | Default Port |
| ---------- | ------------ |
| Production | 18789        |
| Dev        | 19001        |

## Troubleshooting

### Port Already in Use

```bash
# Force start (kills existing)
pnpm openclaw gateway --force

# Or manually find and kill
ss -ltnp | grep 18789
kill <pid>
```

### Health Check

```bash
pnpm openclaw doctor
```

### View Logs

```bash
pnpm openclaw logs
```

### Check Status

```bash
# Quick status
pnpm openclaw status

# Full status with probes
pnpm openclaw status --all
pnpm openclaw channels status --probe
```

### Reset Local State

```bash
pnpm openclaw reset
```

## Build Before Running

If you see stale dist errors:

```bash
pnpm build
```

## macOS Specific

On macOS, the gateway typically runs as a menubar app. Use the restart script:

```bash
./scripts/restart-mac.sh
```

View logs:

```bash
./scripts/clawlog.sh
```
