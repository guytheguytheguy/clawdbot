# Development Guide

## Setup

```bash
# Install dependencies
pnpm install

# Set up pre-commit hooks
prek install
```

## Development Workflow

### 1. Build

```bash
pnpm build
```

### 2. Run Checks

```bash
# All checks (typecheck, lint, format)
pnpm check

# Individual checks
pnpm lint          # Run oxlint
pnpm format        # Check formatting
pnpm format:fix    # Fix formatting
pnpm lint:fix      # Fix lint issues
```

### 3. Run Tests

```bash
# Unit tests
pnpm test

# Watch mode
pnpm test:watch

# With coverage
pnpm test:coverage

# E2E tests
pnpm test:e2e

# Live tests (requires API keys)
OPENCLAW_LIVE_TEST=1 pnpm test:live
```

### 4. Run Locally

```bash
# Gateway in dev mode
pnpm gateway:dev

# TUI in dev mode
pnpm tui:dev

# CLI commands
pnpm openclaw --dev <command>
```

## Project Structure

```
src/
  cli/           # CLI wiring
  commands/      # Command implementations
  infra/         # Infrastructure code
  media/         # Media pipeline
  channels/      # Channel implementations
  routing/       # Message routing

docs/            # Documentation
extensions/      # Plugin extensions
scripts/         # Build and utility scripts
dist/            # Built output
```

## Code Style

- TypeScript with strict mode
- ESM modules
- Oxlint for linting
- Oxfmt for formatting
- Keep files under ~500 LOC

## Testing

- Framework: Vitest
- Coverage threshold: 70%
- Naming: `*.test.ts` (unit), `*.e2e.test.ts` (e2e)

## Commit Guidelines

Use the committer script:

```bash
scripts/committer "feat: add feature" file1.ts file2.ts
```

Commit message format:

- `feat:` New feature
- `fix:` Bug fix
- `docs:` Documentation
- `refactor:` Code refactoring
- `test:` Test changes
- `chore:` Maintenance

## UI Development

```bash
# Install UI deps
pnpm ui:install

# Dev server
pnpm ui:dev

# Build UI
pnpm ui:build
```

## Mobile Development

### iOS

```bash
pnpm ios:gen      # Generate Xcode project
pnpm ios:open     # Open in Xcode
pnpm ios:build    # Build
pnpm ios:run      # Build and run in simulator
```

### Android

```bash
pnpm android:assemble  # Build APK
pnpm android:install   # Install on device
pnpm android:run       # Build, install, and run
pnpm android:test      # Run unit tests
```

## macOS App

```bash
pnpm mac:package   # Package the app
pnpm mac:open      # Open the built app
pnpm mac:restart   # Restart the running app
```

## Useful Scripts

| Script             | Description       |
| ------------------ | ----------------- |
| `pnpm check`       | Run all checks    |
| `pnpm build`       | Build TypeScript  |
| `pnpm test`        | Run tests         |
| `pnpm gateway:dev` | Dev gateway       |
| `pnpm tui:dev`     | Dev TUI           |
| `pnpm docs:dev`    | Local docs server |
