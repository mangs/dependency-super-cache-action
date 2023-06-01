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

## Custom Cache Key Example

```yaml
# ...
# Job 1: production deploy using a matrix strategy
- uses: actions/setup-node@v3
- uses: mangs/super-cache-action@v3
  id: super-cache
  with:
    cache-key-suffix: production-deploy
- if: steps.super-cache.outputs.cache-hit != 'true'
  run: npm ci --production
# ...

# ...
# Job 2: linting and unit testing using a matrix strategy
- uses: actions/setup-node@v3
- uses: mangs/super-cache-action@v3
  id: super-cache
  with:
    cache-key-suffix: linting-and-unit-tests
- if: steps.super-cache.outputs.cache-hit != 'true'
  run: npm ci
# ...
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

| Name               | Required | Default Value    | Descripition                                                                                                                                                                                     |
| ------------------ | -------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `cache-key-suffix` | N        | `<empty-string>` | String appended to the end of the auto-generated cache key that allows for cache key customization (e.g. separate development and production caches with the latter using `npm ci --production`) |
| `cache-targets`    | N        | `./node_modules` | Single- or multi-line string wherein each line targets a resource to cache; can use globs                                                                                                        |
| `package-manager`  | N        | `npm`            | Package manager target for caching operations                                                                                                                                                    |

## Action Outputs

| Name        | Descripition                                                                                                                               |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `cache-hit` | A string containing either `true` or `false` indicating if `cache-targets` were fetched from cache and applied to the current workflow run |
