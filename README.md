# devlink

Devlink is a small agent for a developer's test device. It exposes an HTTP API on the local network so development tools can keep the device debuggable—for example, by keeping wireless ADB enabled, keeping the screen on while charging, or watching Wi-Fi state. The first target is an Android phone, with the agent implemented in Kotlin.

This repository is the API-first specification only; it does not contain the agent implementation. The core API describes capabilities shared by all platforms, while platform-specific behavior belongs in extensions.

## Repository layout

- `spec/core.yaml` — the platform-neutral OpenAPI core contract.
- `spec/components/` — reusable schemas and responses shared by the core and extensions.
- `spec/extensions/` — OpenAPI documents for independently versioned extensions.
- `docs/` — [device discovery](docs/discovery.md), [security](docs/security.md), [versioning](docs/versioning.md), and [extension authoring](docs/extensions.md) guidance.

## Extensions

- [`android.adb`](spec/extensions/android.adb.yaml) — Android wireless debugging.
- [`power.keep-awake`](spec/extensions/power.keep-awake.yaml) — Keep the screen on while charging.
- [`network.wifi`](spec/extensions/network.wifi.yaml) — Wi-Fi connection and signal monitoring.
- [`device.battery`](spec/extensions/device.battery.yaml) — Battery level, charging, and health state.
- [`display.screenshot`](spec/extensions/display.screenshot.yaml) — Capture the current screen.

## Linting

Run the OpenAPI linter from the repository root:

```sh
npx @redocly/cli lint
```

## Standards

- OpenAPI 3.1
- RFC 9457 problem details (`application/problem+json`)
- RFC 6750 Bearer authentication
- RFC 2119 requirement keywords (`MUST`, `MUST NOT`, `SHOULD`, `SHOULD NOT`, and `MAY`)
- RFC 6335 service-name limits and RFC 6763 DNS-SD
