# Changelog

## 3.1.3

- Updated workflows to use operating system `ubuntu-22.04` and Node.js version `16.17.0`
- Added the [`packageManager` field to `package.json`](https://nodejs.org/dist/latest-v16.x/docs/api/all.html#all_packages_packagemanager) to enforce the use of NPM version `8.15.0` for environments with [Corepack](https://nodejs.org/dist/latest-v16.x/docs/api/corepack.html) enabled
- Update dependencies to latest

## 3.1.2

- Update dependencies

## 3.1.1

- Update documentation about `cache-hit` to be more clear about its data type and possible values

## 3.1.0

- Add support for choosing either `npm`, `pnpm`, or `yarn` as the package manager target for caching
- Update workflows to use `mangs/simple-release-notes-action@v2` and Node.js version `16.15.1`

## 3.0.0

- Change action name from `dependency-super-cache-action` to `super-cache-action` to reflect its use beyond just caching dependencies (e.g. ESLint cache)
- Renamed input parameter `dependencies_to_cache` to `cache-targets` for clarity purposes when caching non-dependency targets
- Updated dependencies

## 2.0.3

- Update the readme to reference the correct action version; `v1` was mistakenly referenced instead of `v2`

## 2.0.2

- Shorten action description to under 125 characters so it can be published to the GitHub Marketplace

## 2.0.1

- Make project description more accurate

## 2.0.0

- Change action name from `node-modules-super-cache-action` to `dependency-super-cache-action` to reflect its use beyond just caching `node_modules`
- Renamed input parameter `node_modules_path` to `dependencies_to_cache`
- Changed action and `package.json` description accordingly
- Added multiline string example to readme

## 1.0.3

- Readme tweak to the repository description

## 1.0.2

- Readme example and documentation added

## 1.0.1

- Dogfood this action for this repo's own workflows

## 1.0.0

- First version of this action
