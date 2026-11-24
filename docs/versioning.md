# Versioning

## Independent semantic versions

The core API and each extension use independent semantic versions (`MAJOR.MINOR.PATCH`). The core API version is reported by `/v1/info`; each extension reports its own version in `/v1/extensions`.

Core endpoints use a versioned path such as `/v1`. Extension endpoints use `/ext/<id>/v<major>`, for example `/ext/android.adb/v1`. A breaking change MUST use a new major-version path, such as `/v2` for the core or `/ext/<id>/v2` for an extension. Non-breaking changes retain the existing major-version path.

## Tolerant readers

Clients MUST tolerate unknown fields in response objects and ignore fields they do not understand. API responses do not prohibit additional fields.

## Capability negotiation

Before using extension endpoints, a client reads `GET /v1/extensions` and uses only extensions that are both advertised and enabled. The descriptor provides the extension's base path and required scope. This capability-negotiation approach is similar in spirit to discovery in LSP and MCP; it does not imply protocol compatibility.
