# Changelog

## v1

Pre-release, not yet tagged. Field set is kept in sync with modulab-core's actual manifest parser (backend/internal/modules/installer.go), not an independent spec:

- Required: name, version, author, license, category, min_core, tier. `name` is lowercase-with-hyphens (e.g. `notes`, `unifi-network`), unique within the module store — the earlier `modulab-mod-{name}` namespace requirement was dropped, since no real module (nor Core's installer) ever actually enforced it.
- Implemented and enforced: handler, egress_allowlist (list of hostnames, tier 3 only), jobs (with catch_up), tls_skip_verify, dynamic_egress, egress_hosts_handler, description, display_name, logo, crud (tier 1 config-driven CRUD - table, fields with encrypted, owner_scoped).
- Planned, declared but not yet enforced by Core: resources (memory/timeout caps), storage.quota.
- Removed: scope (per-location/cross-location) - multi-location support was explored early on and dropped before v1 shipped, will not be built. min_core_api/min_core_ui merged into a single min_core, matching what Core actually reads. credentials, depends_on and requested_scopes were removed - each module handles its own configuration, dependencies and permission disclosure itself rather than through a Core-provided manifest mechanism.

Additional fields for modulab-community discovery entries: source_repo, manifest_path and release_url, plus the optional cosign_sig_url and cosign_pubkey (L-5, audit 2026-08-02) - a signed community release's verification key, reviewed as part of the discovery-entry PR rather than trusted from the module's own repo.
