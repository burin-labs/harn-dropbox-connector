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

## Provider

- Provider id: `dropbox`
- API hosts: `api.dropboxapi.com`, `content.dropboxapi.com`
- Recommended scopes for artifact workflows:
  - `files.metadata.read`
  - `files.content.read`
  - `files.content.write`

## Useful methods

- `files.get_metadata`
- `files.list_folder`
- `files.list_folder.continue`
- `files.download`
- `files.export`
- `files.upload`
- `artifact.export_request`
- `artifact.import_request`

## References

- Dropbox HTTP API:
  <https://www.dropbox.com/developers/documentation/http/documentation>
- Dropbox webhooks:
  <https://www.dropbox.com/developers/reference/webhooks>

## Validation

```sh
harn connector test . --provider dropbox
```

The smoke tests use Harn HTTP mocks and do not call Dropbox APIs.
