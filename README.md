# `mangs/dependency-super-cache-action`

Simple GitHub Action that improves dependency cache performance over `actions/cache`'s recommendations for Node.js projects

## Simple Example

```yaml
- uses: actions/setup-node@v3
  with:
    node-version: "16.15.0"
- id: super-cache
  uses: mangs/dependency-super-cache-action@v2
- if: steps.super-cache.outputs.cache-hit != 'true'
  run: npm ci
```

## Multiline Dependencies Example

```yaml
- uses: actions/setup-node@v3
  with:
    node-version: "16.15.0"
- id: super-cache
  uses: mangs/dependency-super-cache-action@v2
  with:
    cache_targets: |
      ./.eslintcache
      ./node_modules
- if: steps.super-cache.outputs.cache-hit != 'true'
  run: npm ci
```

## Action Inputs

| Name            | Required | Default Value    | Descripition                                                                              |
| --------------- | -------- | ---------------- | ----------------------------------------------------------------------------------------- |
| `cache_targets` | N        | `./node_modules` | Single- or multi-line string wherein each line targets a resource to cache; can use globs |

## Action Outputs

| Name        | Data Type | Descripition                                                              |
| ----------- | --------- | ------------------------------------------------------------------------- |
| `cache-hit` | Boolean   | A boolean value indicating if a match was found in the repository's cache |
