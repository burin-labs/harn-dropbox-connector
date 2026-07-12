# AGENTS.md

Shared connector authoring rules live in the Harn guide:

- [Connector authoring guide](https://github.com/burin-labs/harn/blob/main/docs/src/connectors/authoring.md)

Put shared connector guidance in the Harn guide and keep only Dropbox-specific
notes here.

## Provider notes

- Keep API calls scoped to `api.dropboxapi.com` and
  `content.dropboxapi.com`.
- Use the exact metadata and content scopes declared in `harn.toml`.
- Treat webhook notifications as wake-up events; `files/list_folder/continue`
  is the authoritative path for changed-file details.
