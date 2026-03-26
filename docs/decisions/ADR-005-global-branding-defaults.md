# ADR-005: Global branding defaults under Administration

- Date: 2026-03-26
- Status: Accepted
- Scope: Global presentation defaults for name and logo

## Context

Per-user branding is already governed via `users.organization_label` and `users.organization_logo_data_url`.

The product also needs a global default branding layer that works when the current user has not defined an individual presentation label or logo. The change must remain single-file compatible, must not require `DB_VER` changes, and must preserve the existing CSV/SQL contracts.

## Decision

- Add a global branding settings payload stored in the existing settings store under the key `presentationBranding`.
- Export and import that payload via the JSON/bound-file data contract as `presentation_branding_settings`.
- Keep the precedence order explicit:
  1. Per-user logo/name override
  2. Global branding defaults
  3. Local `logo.png`
  4. Embedded SVG fallback
- Place the global branding UI in Administration under `Handlinger`.
- Allow a global presentation label plus a PNG-only global logo upload.

## Consequences

- No `DB_VER` change.
- No new stores or indexes.
- No `schemaFields.users` change.
- JSON backup/restore and bound-file sync preserve `presentation_branding_settings`.
- CSV backup/import and SQL export remain unchanged.
- User branding continues to override the global defaults.
- The settings payload is presentation-only and is not treated as a naming or schema migration.
