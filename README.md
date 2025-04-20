# Stywrap
**Stywrap** is a modular set of [**Webpack**](https://webpack.js.org/) loaders and utilities to convert **stylesheets** from various **preprocessors** (**SASS**, **LESS**, **Stylus**, **CSS**) into JavaScript strings and optionally inject them into the Shadow DOM of Web Components

### 🎁 Features
* ✨ Supports SCSS, SASS, LESS, Stylus, CSS
* 🧱 Structured as a Yarn Workspaces monorepo
* 🌌 Built-in support for Shadow DOM injection
*	🧩 One plugin to rule them all — with optional per-preprocessor loaders
* 🔄 Written in TypeScript


### 🔧 Project Structure
```bash
stywrap/
├── package.json                # Root workspace config
├── yarn.lock
├── .yarnrc.yml                # Enables Yarn Berry features
├── tsconfig.base.json         # Shared base config
├── packages/
│   ├── core/                  # Shared utilities
│   │   ├── src/
│   │   └── package.json
│   ├── sass/                  # Sass loader
│   │   ├── src/
│   │   └── package.json
│   ├── less/                  # Less loader
│   │   ├── src/
│   │   └── package.json
│   ├── stylus/                # Stylus loader
│   │   ├── src/
│   │   └── package.json
│   ├── plugin-webpack/        # Combined Webpack plugin to register all loaders
│   │   ├── src/
│   │   └── package.json
├── demo/
│   ├── lit/                   # Example usage with Lit Web Components
│   └── vanilla/               # Vanilla JS Web Component example
└── README.md
```

### 🧩 Usage Examples

1. **Package usage**: 📦 [@stywrap/sass](/packages/sass/package.json)
  ```ts
  // webpack.config.js
  module.exports = {
    module: {
      rules: [
        {
          test: /\.scss$/,
          use: ['@stywrap/sass'],
        }
      ]
    }
  }
  ```
  
  Given that you have an **SCSS** file like this:
  ```scss
  // button.scss
  .btn {
    padding: 1rem;
  }
  ```

  You can now import the **SCSS** like this:
  ```ts
  import styles from './button.scss';
  console.log(styles); // => ".btn { padding: 1rem; }"

  ```

2. 🌌 **Shadow DOM Injection** (via 📦 [@stywrap/core](/packages/core/package.json))
  ```ts
  import { injectStylesToShadowDOM } from '@stywrap/core';
  import styles from './button.scss';
  
  injectStylesToShadowDOM(shadowRoot, styles);
  ```

3. ☘️ **Webpack Plugin** (for auto-config across preprocessors)
```ts
// webpack.config.js
const StywrapPlugin = require('@stywrap/plugin-webpack');

module.exports = {
  plugins: [
    new StywrapPlugin({
      shadow: true,       // Automatically injects styles into Shadow DOM
      minify: false,      // Optionally minify
    })
  ]
}
```
  
