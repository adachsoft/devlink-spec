# Device discovery

Devlink agents advertise themselves on the local network using DNS-Based Service Discovery (DNS-SD, RFC 6763).

| DNS-SD field | Value |
| --- | --- |
| Service type | `_as-devlink._tcp` |
| Instance name | The device's user-visible name |
| Default port | `8787` |

The service label `_as-devlink` is within the 15-character service-name limit from RFC 6335. The DNS-SD registration type uses the `_tcp` transport.

## TXT record

The service TXT record contains these keys:

| Key | Value |
| --- | --- |
| `id` | Stable device/agent identifier |
| `name` | User-visible device name |
| `platform` | Platform identifier, such as `android` |
| `api` | Core API semantic version |
| `path` | Core API base path; defaults to `/v1` |

Clients MUST resolve the service before connecting and MUST resolve it again when the advertised IP address or port changes. The service may be reachable at a different address after network changes.

On Android, the agent uses `NsdManager` to register and discover the DNS-SD service.
