# CLAUDE.md

See `AGENTS.md` and the canonical Harn connector authoring guide:

- https://github.com/burin-labs/harn/blob/main/docs/src/connectors/authoring.md

## Provider Notes

- Keep Dropbox API calls scoped to `api.dropboxapi.com` and
  `content.dropboxapi.com`.
- Prefer least-privilege Dropbox file metadata/content scopes for artifact
  workflows.
- Treat Dropbox webhook notifications as wake-up events; list-folder cursors
  remain the authoritative polling path for changed file details.
