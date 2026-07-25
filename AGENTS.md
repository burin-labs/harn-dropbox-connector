# AGENTS.md

Pure-Harn Dropbox connector for webhook notifications and cursor-based polling.

Shared connector authoring rules live in the Harn guide:

- [Connector authoring guide](https://github.com/burin-labs/harn/blob/main/docs/src/connectors/authoring.md)

Put shared connector guidance in the Harn guide and keep only
provider-specific notes and local hazards here.

`CLAUDE.md` is a symlink to this file. Edit `AGENTS.md` only.

## Provider notes

- Keep API calls scoped to `api.dropboxapi.com` and
  `content.dropboxapi.com`.
- Use the exact metadata and content scopes declared in `harn.toml`.
- Treat webhook notifications as wake-up events; `files/list_folder/continue`
  is the authoritative path for changed-file details.
