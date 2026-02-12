# OpenClaw Quickstart

## Prerequisites

- Node.js 22+
- pnpm 10+

## Installation

```bash
pnpm install
```

## Running OpenClaw

### Basic Commands

```bash
# Run the CLI (shows help)
pnpm openclaw

# Run with a specific command
pnpm openclaw <command>

# Alternative ways to run
pnpm start
pnpm dev
```

### Common Commands

| Command                   | Description                      |
| ------------------------- | -------------------------------- |
| `pnpm openclaw gateway`   | Run the WebSocket Gateway        |
| `pnpm openclaw status`    | Show channel health and sessions |
| `pnpm openclaw tui`       | Launch Terminal UI               |
| `pnpm openclaw onboard`   | Interactive setup wizard         |
| `pnpm openclaw configure` | Set up credentials and defaults  |
| `pnpm openclaw doctor`    | Health checks and quick fixes    |

### Development Mode

Dev mode isolates state under `~/.openclaw-dev` with a separate gateway port (19001):

```bash
# Run gateway in dev mode
pnpm openclaw --dev gateway

# Run TUI in dev mode
pnpm tui:dev
```

### Gateway Commands

```bash
# Start gateway on default port
pnpm openclaw gateway

# Start gateway on custom port
pnpm openclaw gateway --port 18789

# Force start (kill existing process on port)
pnpm openclaw gateway --force

# Gateway with loopback binding
pnpm openclaw gateway --bind loopback --port 18789
```

### Messaging

```bash
# Send a message
pnpm openclaw message send --target +15555550123 --message "Hello"

# Send via Telegram
pnpm openclaw message send --channel telegram --target @mychat --message "Hi"

# Run agent and deliver response
pnpm openclaw agent --to +15555550123 --message "Run summary" --deliver
```

### Channel Management

```bash
# Login to WhatsApp Web
pnpm openclaw channels login --verbose

# Check channel status
pnpm openclaw channels status --probe
```

## Build & Development

```bash
# Build the project
pnpm build

# Run linting and formatting checks
pnpm check

# Run tests
pnpm test

# Run tests with coverage
pnpm test:coverage
```

## Profiles

Use named profiles to isolate state and config:

```bash
# Use a named profile
pnpm openclaw --profile myprofile gateway

# Dev profile (shorthand)
pnpm openclaw --dev gateway
```

## Documentation

Full documentation: https://docs.openclaw.ai/cli
