# `mangs/super-cache-action`

Simple GitHub Action that improves cache performance over `actions/cache`'s recommendations for Node.js projects

## Simple Example

```yaml
- uses: actions/setup-node@v3
- uses: mangs/super-cache-action@v3
  id: super-cache
- if: steps.super-cache.outputs.cache-hit != 'true'
  run: npm ci
```

## Multiline Dependencies Example

```yaml
- uses: actions/setup-node@v3
- uses: mangs/super-cache-action@v3
  id: super-cache
  with:
    cache-targets: |
      ./.eslintcache
      ./node_modules
- if: steps.super-cache.outputs.cache-hit != 'true'
  run: npm ci
```

## Action Inputs

| Name              | Required | Default Value    | Descripition                                                                              |
| ----------------- | -------- | ---------------- | ----------------------------------------------------------------------------------------- |
| `cache-targets`   | N        | `./node_modules` | Single- or multi-line string wherein each line targets a resource to cache; can use globs |
| `package-manager` | N        | `npm`            | Package manager target for caching operations                                             |

## Action Outputs

| Name        | Descripition                                                                                                  |
| ----------- | ------------------------------------------------------------------------------------------------------------- |
| `cache-hit` | A boolean value indicating if `cache-targets` were fetched from cache and applied to the current workflow run |
