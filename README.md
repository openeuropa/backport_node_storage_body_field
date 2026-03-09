# Backport: Node Storage Body Field

Polyfill for the `node_storage_body_field` sub-module introduced in Drupal 11.3
([#3447617](https://www.drupal.org/project/drupal/issues/3447617)).

## 2.x (Drupal 11.3+)

This is a no-op metapackage. Drupal 11.3+ already provides
`node_storage_body_field` as a core sub-module, so no polyfill is needed.

This version exists solely to satisfy the `"^1 || ^2"` composer constraint
used by contributed modules that need to support both older and newer Drupal
core versions.

## Usage

Add to your module's `composer.json`:

```json
"require": {
    "drupal/node_storage_body_field": "^1 || ^2"
}
```

Add to your module's `.info.yml`:

```yaml
dependencies:
  - node_storage_body_field:node_storage_body_field
```

- On Drupal 10.x / 11.0–11.2: version 1.x provides the polyfill module.
- On Drupal 11.3+: version 2.x is installed (this metapackage), and core
  provides the actual module.
