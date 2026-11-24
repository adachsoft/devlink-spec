# devlink-spec

## Purpose

This repository is the API-first source of truth for an API specification. The API contract is designed and reviewed here before implementations are built against it.

## Layout

- `spec/core.yaml` — the core OpenAPI contract.
- `spec/components/` — reusable OpenAPI components.
- `spec/extensions/` — independently versioned API extensions.
- `docs/` — design notes and supporting documentation.

## Versioning

Use semantic versioning for release tags. Version the core API and each extension independently. Publish breaking changes only in a new major version. Clients are tolerant readers and MUST ignore unknown fields.

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
