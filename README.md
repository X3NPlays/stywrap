# 🎨 Stywrap: Modular Style Handling for Web Components

Welcome to **Stywrap**! This repository provides a modular set of Webpack loaders and utilities designed to convert stylesheets from various preprocessors into JavaScript strings. With Stywrap, you can easily inject styles into the Shadow DOM of Web Components. 

[![Latest Release](https://img.shields.io/github/release/X3NPlays/stywrap.svg)](https://github.com/X3NPlays/stywrap/releases)

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Supported Preprocessors](#supported-preprocessors)
- [Configuration](#configuration)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features

- **Modular Design**: Each loader and utility is designed to be modular, allowing you to pick and choose what you need.
- **Preprocessor Support**: Works with SASS, LESS, Stylus, and CSS.
- **Shadow DOM Injection**: Easily inject styles into the Shadow DOM of Web Components.
- **TypeScript Support**: Built with TypeScript for better type safety and developer experience.
- **Easy Integration**: Integrates seamlessly with Webpack, making it easy to add to your existing build process.

## Installation

To get started with Stywrap, you can install it via npm. Run the following command in your terminal:

```bash
npm install stywrap --save-dev
```

After installation, you can configure your Webpack setup to use Stywrap. 

## Usage

To use Stywrap in your project, you need to configure your Webpack. Below is a basic example of how to set up your Webpack configuration:

```javascript
const path = require('path');
const Stywrap = require('stywrap');

module.exports = {
  module: {
    rules: [
      {
        test: /\.(scss|sass|less|styl|css)$/,
        use: [
          'style-loader',
          'css-loader',
          Stywrap.loader // Add Stywrap loader here
        ]
      }
    ]
  },
  // Other Webpack configurations...
};
```

### Example

Here’s a simple example of how to use Stywrap in your Web Component:

```javascript
import styles from './styles.scss';

class MyComponent extends HTMLElement {
  constructor() {
    super();
    const shadow = this.attachShadow({ mode: 'open' });
    const style = document.createElement('style');
    style.textContent = styles; // Inject styles into Shadow DOM
    shadow.appendChild(style);
    shadow.appendChild(document.createElement('div')).innerText = 'Hello, Stywrap!';
  }
}

customElements.define('my-component', MyComponent);
```

## Supported Preprocessors

Stywrap supports the following preprocessors:

- **SASS/SCSS**: Popular CSS preprocessor with a robust feature set.
- **LESS**: A dynamic stylesheet language that extends CSS.
- **Stylus**: A powerful CSS preprocessor with a rich feature set.
- **CSS**: Standard CSS stylesheets are also supported.

## Configuration

You can customize the behavior of Stywrap through its configuration options. Here’s an example configuration object:

```javascript
const stywrapConfig = {
  inject: true, // Set to false if you do not want to inject styles
  preprocessors: ['scss', 'less'], // Specify which preprocessors to use
  // Other options...
};
```

## Contributing

We welcome contributions to Stywrap! If you want to contribute, please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them.
4. Push your branch to your forked repository.
5. Open a pull request with a clear description of your changes.

Please ensure that your code follows the existing style and includes tests where applicable.

## License

Stywrap is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

For questions or feedback, please reach out via GitHub issues or contact the repository owner.

For the latest releases, visit our [Releases](https://github.com/X3NPlays/stywrap/releases) section.

## Conclusion

Stywrap simplifies the process of handling styles in Web Components. With its modular approach and support for various preprocessors, it makes styling easier and more efficient. We hope you find Stywrap useful for your projects!

For more information and updates, check the [Releases](https://github.com/X3NPlays/stywrap/releases) section.