# Backport: Node Storage Body Field

Polyfill for the `node_storage_body_field` sub-module introduced in Drupal 11.3
([#3447617](https://www.drupal.org/project/drupal/issues/3447617)).

In Drupal 11.3, `field.storage.node.body` was moved out of the Node module into
a new `node_storage_body_field` sub-module. Contributed modules that ship node
types with a body field must now declare a dependency on
`node_storage_body_field` to ensure the field storage config exists when their
module is installed.

This module provides a shim for older Drupal versions where that sub-module does
not exist yet. The body field storage itself is still provided by the Node module
on older core versions — this shim simply satisfies the dependency.

## Versions

- **1.x** (Drupal 10.x / 11.0-11.2): Empty shim module that satisfies the
  `node_storage_body_field` dependency. No config is shipped — the Node module
  already provides `field.storage.node.body` on these core versions.
- **2.x** (Drupal 11.3+): Metapackage no-op. Core already provides
  `node_storage_body_field`.

## Usage

Add to your module's `composer.json`:

```json
"require": {
    "drupal/backport_node_storage_body_field": "^1 || ^2"
}
```

Add to your module's `.info.yml`:

```yaml
dependencies:
  - node_storage_body_field:node_storage_body_field
```

Remove `field.storage.node.body` from your module's `config/install` if present.
