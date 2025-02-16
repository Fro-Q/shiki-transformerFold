# shiki-transformerFold for VitePress

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

A custom Shiki transformer for creating foldable code blocks with annotation syntax.

This is related to [this issue](https://github.com/shikijs/shiki/issues/861#issuecomment-2661471613).

The code is too ugly to be a part of [shiki](https://github.com/shikijs/shiki). :)

## Installation

1. Copy the code from [`customTransformers.js`](https://github.com/Fro-Q/shiki-transformerFold/blob/main/customTransformers.js) and paste it into a file in your VitePress project, for example, `docs/.vitepress/theme/scripts/customTransformers.js`.
2. Import the transformer in `docs/.vitepress/config.mts` and add it to your configuration:

```js
// ...
import { transformerNotationFold } from './theme/scripts/customTransformers'

export default defineConfig({
  // ...
  markdown: {
    codeTransformers: [transformerNotationFold()]
  }
  // ...
})
```

3. If you're using the default theme, copy and paste the code from [`style.css`](https://github.com/Fro-Q/shiki-transformerFold/blob/main/style.css) into your project's CSS file.
4. If you're using a completely custom theme, feel free to style the button and any other elements as you like.

## Usage

The foldable code block annotation follows this syntax: `[!code fold:<unique-id>:<start-line>-<end-line>]`.

Example:

````
```js
function example() { // [!code fold:my-fold:1-3]
  // Code to fold
  console.log('This section is foldable')
}
```
````

This will render as:

![CleanShot 2025-02-16 at 23 27 19](https://github.com/user-attachments/assets/41d12637-4e27-40ed-a89d-5795b1eb4f32)

It also works with the `line-numbers` option:

````
```js:line-numbers
function example() { // [!code fold:my-fold:1-3]
  // Code to fold
  console.log('This section is foldable')
}
```
````

This will render as:

![CleanShot 2025-02-16 at 23 29 05](https://github.com/user-attachments/assets/6dba93d2-cc2a-48cb-8c62-d6dff08c48a1)

## Caveats

1. Annotation comments **must follow the exact syntax**.
2. Fold ranges cannot overlap.

## License

MIT © [Fro-Q](https://github.com/Fro-Q)
