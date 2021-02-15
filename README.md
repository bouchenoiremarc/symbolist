# create-canvas-context

🎨 Create a canvas and get a rendering context from it.

[![npm](https://img.shields.io/npm/v/create-canvas-context?color=%2385f)](https://www.npmjs.com/package/create-canvas-context) [![gzipped](https://img.shields.io/bundlephobia/minzip/create-canvas-context?label=gzipped&color=%23d5e)](https://www.npmjs.com/package/create-canvas-context) [![license](https://img.shields.io/github/license/bouchenoiremarc/create-canvas-context?color=%23e48)](https://github.com/bouchenoiremarc/create-canvas-context/blob/main/LICENSE)

## Installation

#### With yarn

```sh
yarn add create-canvas-context
```

#### With npm

```sh
npm install create-canvas-context
```

## Usage

Import `createCanvasContext`.

```tsx
import { createCanvasContext } from "create-canvas-context"
```

Invoke it while specifying a context type (`"2d"`, `"bitmaprenderer"`, `"webgl"` or `"webgl2"`).

```tsx
createCanvasContext("2d")
```

Access in return a canvas and the specified rendering context as a pair.

```tsx
const [canvas, context] = createCanvasContext("2d")
```

Optionally override defaults using [options](#options).

```tsx
const [canvas, context] = createCanvasContext("2d", {
  canvas: document.createElement("canvas"),
  offscreen: true,
  alpha: false
})
```

## Options

A secondary `options` argument surfaces all context-specific attributes available using [`HTMLCanvasElement.getContext()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/getContext) and adds a few optional settings to tweak the behavior of `createCanvasContext`.

#### `canvas`

```tsx
canvas?: HTMLCanvasElement | OffscreenCanvas
```

Setting `canvas` to an existing canvas (either an `HTMLCanvasElement` or an `OffscreenCanvas`) will provide it instead of creating one.

#### `offscreen`

```tsx
offscreen?: boolean = false
```

Setting `offscreen` to `true` will create an `OffscreenCanvas` instead of an `HTMLCanvasElement`.

If you provided an existing `HTMLCanvasElement` using the `canvas` option, it will get its control transferred to an `OffscreenCanvas` using [`HTMLCanvasElement.transferControlToOffscreen()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/transferControlToOffscreen).

#### `width` and `height`

```tsx
width?: number
height?: number
```

Setting `width` and `height` will set specific canvas dimensions and override existing values.
