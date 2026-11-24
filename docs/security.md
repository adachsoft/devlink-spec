# Security

## Network boundary

The agent is for private networks only. It MUST reject requests whose source address is not private or local. Accepted source addresses are limited to IPv4 private ranges defined by RFC 1918, IPv6 unique-local addresses defined by RFC 4193, IPv4 or IPv6 link-local addresses, and IPv4 or IPv6 loopback addresses.

## Bearer authentication and scopes

Every API request MUST use a Bearer token in the `Authorization` header as specified by RFC 6750. Tokens carry scopes:

- `core` is required for `/v1/*` core endpoints.
- `ext:<id>` is required for the corresponding extension, where `<id>` is its extension identifier.

The agent MUST return `401 Unauthorized` when a token is missing or invalid, and MUST return `403 Forbidden` when a valid token lacks the required scope. Unauthorized responses include a `WWW-Authenticate` header.

## Extension safety

Sensitive extensions MUST be disabled by default and MUST be explicitly enabled on the device. Default extensions MUST NOT expose endpoints for installing applications or reading user data.

The requirement keywords `MUST`, `MUST NOT`, `SHOULD`, `SHOULD NOT`, and `MAY` are used with the meanings defined by RFC 2119.
