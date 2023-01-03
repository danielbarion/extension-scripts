# PixiJS Extension Scripts

Contains all the tools common for building extensions for PixiJS. While this tool is rather generic and can be used for variety of purposes, it has convenient defaults that are specifically designed for PixiJS v7+.

## Getting Started

Simply add these things to your **package.json**. All commands are optional.

```json
{
  "scripts": {
    "clean": "extension-scripts clean",
    "watch": "extension-scripts watch",
    "build": "extension-scripts build",
    "lint": "extension-scripts lint",
    "docs": "extension-scripts docs",
    "types": "extension-scripts types",
    "serve": "extension-scripts serve",
    "deploy": "extension-scripts deploy",
    "release": "extension-scripts release"
  },
  "devDependencies": {
    "@pixi/extension-scripts": "latest"
  }
}
```

### Commands

| Command | Description |
|---|---|
| `clean` | Removes the `dist` and `lib` folders |
| `watch` | Watch the code in development mode, updates on changes |
| `build` | Build `dist` and `lib` targets in release mode as well as the types. |
| `lint` | Using ESLint to lint the `src` folder, this runs with `--fix` enabled. |
| `docs` | Build the `src` folder into `docs` folder using webdoc |
| `types` | Type-check the `src` folder using TypeScript |
| `serve` | Runs `watch` command plus also opens the `examples` folder |
| `deploy` | Does `build` and `docs` and then copies the folders (`dist`, `examples`, `docs`) to `gh-pages` branch |
| `release` | Publish a release, will ask for what type of version bump, do a `deploy` and push to npm and git tags. |


## Configuration

Configuration can be provided using the `extensionConfig` field in **package.json**:

* **`namespace`** _string_ - User-defined global namespace for the bundle.
* **`globals`** _object_ - [Output globals](https://rollupjs.org/guide/en/#outputglobals) as defined by Rollup. This is used for creating the browser bundle. All defaults are provide for the core package of PixiJS (e.g., `@pixi/core`, `@pixi/sprite`, etc).
* **`bundle`** _string_ - The relative path to the output browser file.
* **`clean`** _string[]_ - List of files to clean before each build.
* **`source`** _string_ - The entry-point for building the extension (default: `src/index.ts`)
* **`lint`** _string[]_ - List of additional folders or files to lint.
* **`deploy`** _string[]_ - Glob pattern for files to deploy (default: `{dist,examples,docs}/**`).
* **`serve`** _string_ - Relative path to the serve folder (default: `examples`).
* **`tsconfig`** _string_ - Relative path to the tsconfig file for doing type check (default: `tsconfig.json`)
* **`silent`** _boolean_ - Whether to silence the output (default: `false`)
* **`docsDestination`** _string_ - Relative path to the output documentation folder (default: `docs`)
* **`docsRepository`** _string_ - URL for repository (defaults: package.json's `repository.url`)
* **`docsName`** _string_ - Application name in docs  (defaults: package.json's `name`)
* **`docsCopyright`** _string_ - Copyright in the docs (defaults: package.json's `author`)
* **`docsTitle`** _string_ - HTML base title in docs (defaults: package.json's `name`)
* **`docsDescription`** _string_ - HTML meta description in docs (defaults: package.json's `description`)
* **`docsKeywords`** _string_ - HTML meta keywords in docs (defaults: package.json's `keywords`)

### Example

```json
{
  "extensionConfig": {
    "namespace": "PIXI.myextension",
    "bundle": "dist/pixi-my-extension.js",
    "globals": {
        "lodash": "_"
    }
  }
}
```
