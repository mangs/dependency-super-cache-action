# `mangs/node-modules-super-cache-action`

GitHub Action that is simple and greatly improves `node_modules` cache performance over `actions/cache`

## Example Use

```yaml
- uses: actions/setup-node@v3
  with:
    node-version: "16.14.2"
- id: super-cache
  uses: mangs/node-modules-super-cache-action@v1
- if: steps.super-cache.outputs.cache-hit != 'true'
  run: npm ci
```

## Action Inputs

| Name                | Required | Default Value    | Descripition                                                       |
| ------------------- | -------- | ---------------- | ------------------------------------------------------------------ |
| `node_modules_path` | N        | `./node_modules` | Path to one or more `node_modules` directories; can include a glob |

## Action Outputs

| Name        | Data Type | Descripition                                                              |
| ----------- | --------- | ------------------------------------------------------------------------- |
| `cache-hit` | Boolean   | A boolean value indicating if a match was found in the repository's cache |
