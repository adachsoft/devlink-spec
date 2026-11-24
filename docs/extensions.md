# Extensions

Extensions add capabilities that are not common to every devlink platform. Use a shared semantic identifier when the capability has the same meaning across platforms (for example, `power.keep-awake`). Use a platform-specific identifier for platform-specific behavior (for example, `android.adb`).

## Extension contract

1. Choose a lowercase, dot-separated identifier matching `^[a-z][a-z0-9-]*(\.[a-z][a-z0-9-]*)+$`.
2. Add the OpenAPI document at `spec/extensions/<id>.yaml`.
3. Use `/ext/<id>/v<major>` as the base path, such as `/ext/android.adb/v1`.
4. Require the `ext:<id>` Bearer-token scope.
5. Contribute the extension's status as a free-form object under its extension ID in `/v1/status`.
6. Register the document in `redocly.yaml` under `apis`, using a unique API key and the document path as `root`. For example:

   ```yaml
   apis:
     core:
       root: spec/core.yaml
     android-adb:
       root: spec/extensions/android.adb.yaml
   ```

Extensions are independently versioned and are advertised by `GET /v1/extensions`. Clients should use only extensions that are advertised and enabled.
