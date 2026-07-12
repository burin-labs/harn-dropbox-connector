# harn-dropbox-connector

Pure-Harn Dropbox connector for file artifact workflows.

The initial surface is deliberately connector-shaped, not document-renderer
shaped:

- Normalize Dropbox webhook challenges and signed account-change notifications
  into Harn connector events.
- Poll Dropbox `files/list_folder` cursors from Harn-managed state.
- Dispatch common Dropbox file metadata, listing, download, export, and upload
  APIs through allowlisted egress descriptors.
- Build deterministic request descriptors for artifact export/import flows.

Document rendering and manifest vocabulary stay in `harn-documents`; this
package owns the external Dropbox boundary.

## Install

```sh
harn add github.com/burin-labs/harn-dropbox-connector@v0.1.0
```

For local development, use a path dependency on this checkout. Use the Harn
CLI version pinned in `.harn-version` for validation.

## Configure

- Provider id: `dropbox`
- API hosts: `api.dropboxapi.com`, `content.dropboxapi.com`
- Required secrets: `dropbox/access-token`, `dropbox/app-secret`
- Required OAuth scopes: `files.metadata.read`, `files.content.read`,
  `files.content.write`

Start browser-based setup with `harn connect dropbox`. Check its status with
`harn connect status --connector dropbox --json`.

## Useful methods

- `files.get_metadata`
- `files.list_folder`
- `files.list_folder.continue`
- `files.download`
- `files.export`
- `files.upload`
- `artifact.export_request`
- `artifact.import_request`

## Provider references

- Dropbox HTTP API:
  <https://www.dropbox.com/developers/documentation/http/documentation>
- Dropbox webhooks:
  <https://www.dropbox.com/developers/reference/webhooks>

## Validate

```sh
harn connector test . --provider dropbox
```

The smoke tests use Harn HTTP mocks and do not call Dropbox APIs.
