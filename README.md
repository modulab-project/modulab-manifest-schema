# modulab-manifest-schema

Versioned JSON Schema for the manifest.yaml of ModuLab (https://modulab.app) modules.

Each supported Core API version (min_core_api) has its own schema directory: v1/manifest.schema.json

## Usage

This schema is the single source of truth for validating manifest.yaml files. modulab-core validates manifests against the schema matching min_core_api during module installation. modulab-module-sdk validates manifests locally during development against the same schema. modulab-community validates submitted pull requests automatically via a GitHub Action.

## Offline-first

In line with ModuLab Core's offline-first principle, this schema is not fetched at runtime via URL. Dependent repos vendor it at build time (Git submodule or CI copy step).

## Versioning

A new vX directory is added whenever a new min_core_api version is introduced. Existing schema versions remain unchanged for the duration of the 6-month parallel-support guarantee. See CHANGELOG.md for changes.

## License

MIT, see LICENSE. Deliberately permissive so that community module developers with other licenses can adopt the schema without friction.

## Reference

Full specification of manifest fields: ModuLab Core specification (modulab-docs), chapter 4.
