# GlimR Security and Storage Policy

## Status
- Policy status: active
- Scope: browser-local storage, bound-file persistence, backup/export handling, and operational limits of the current browser-based deployment model

## Relationship to existing documents
This policy supplements `docs/security/storage-and-privacy-assessment.md` and updates it with verified code-level storage facts from the 2026-03-23 baseline.

## Current storage model

### IndexedDB
- IndexedDB is the primary local persistence layer.
- Core application data is stored in the `glims` database at schema version 15.
- IndexedDB availability depends on browser support, browser profile settings, and storage permissions.
- If durable storage is unavailable, GlimR can fall back to memory-only behavior for limited runtime use, but this is not a safe long-term operating mode.

### localStorage
- `localStorage` is used for lightweight browser-local state including:
  - theme preference
  - autosave preference
  - bound-file display name
  - current user/session identifier
  - legacy planner-related keys
- `localStorage` is not a secure secret store.

### File System Access API and bound file
- Users can bind GlimR to a local JSON file through the File System Access API.
- Autosave can write incremental updates to that bound file.
- Current save behavior is merge-aware and compares against the last synced data snapshot.
- Bound-file behavior depends on browser support and user-granted file permissions.

### Exports and backups
- JSON, CSV, ZIP, SQL, FHIR, and PDF outputs can contain operational or sensitive data.
- Backups and exports must be treated as sensitive local files.
- Current backup/export behavior may include user and AI-provider data depending on the selected export path.

## What the browser environment can and cannot guarantee

### What can be reasonably expected
- Fully offline local operation in a supported Chromium-based browser.
- Local persistence in IndexedDB under normal browser conditions.
- User-mediated local file writes when File System Access API is available and permissions are granted.

### What cannot be guaranteed
- Secure deletion of data from browser-managed storage.
- Uniform behavior across all browsers, profiles, private modes, or enterprise policies.
- Stable IndexedDB or File System Access behavior in private/incognito mode.
- Protection of locally stored secrets equivalent to a dedicated credential vault.

## Sensitive-data considerations
- Browser-local data may contain clinical and operational records.
- User PINs are locally stored application data in the current model.
- AI-provider API keys are locally stored application data in the current model.
- Backups, bound files, and exports can duplicate that data outside the browser store.
- Shared machines, shared browser profiles, and unmanaged local file storage materially increase data-leakage risk.

## Recommended operating mode
- Use a dedicated local machine or a tightly controlled workstation profile.
- Use a supported Chromium-based browser profile dedicated to GlimR.
- Enable regular JSON backups.
- Use bound-file mode only when the environment has stable file permissions and the operator understands that the JSON file becomes a sensitive local datastore.
- Keep optional `logo.png` adjacent to the application only when needed for report branding.

## Private/incognito mode policy
- Private/incognito mode is not a supported default operating mode.
- Browser vendors may limit or disable IndexedDB, localStorage persistence, and File System Access behavior in private sessions.
- Any proposal to require private/incognito mode is Class C and must be handled as a controlled design and governance decision.

## Offline operation policy
- Offline operation is required for core LIMS use.
- Network-connected features such as AI provider calls must remain optional.
- A failed network call must not block core CRUD, reporting, backup, or restore flows.

## Why "clear browser memory after every autosave" is not allowed as an ad hoc change
This idea must not be introduced without a dedicated ADR and design review because it can affect:
- active user sessions
- reload behavior
- error recovery
- autosave expectations
- merge semantics for bound files
- operator trust in whether data is still available after a refresh

It is therefore a migration-sensitive storage behavior change, not a minor cleanup.

## Storage and release obligations
- Storage-affecting changes must follow `docs/governance/data-migration-policy.md`.
- Export/import and bound-file changes must satisfy the relevant rows in `docs/governance/test-matrix.md`.
- No storage-affecting release may rely on undocumented browser behavior.

## Interpretation rule
If a proposed storage or privacy control sounds simple but changes where data lives, when it is retained, or how it is restored, it is not simple. Treat it as a governed change.
