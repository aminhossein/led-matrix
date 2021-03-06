# RGB LED Matrix

[![Build Status](https://travis-ci.org/sallar/led-matrix.svg?branch=master)](https://travis-ci.org/sallar/led-matrix)

This library provides a set of tools for:

+ Simulating a physical RGB LED Matrix using HTML5
+ A data store for creating shapes, colors, text in order to render on the Matrix

## Install

``` bash
$ npm install led-matrix --save-dev
# or
$ yarn add led-matrix
```

## Usage

``` js
import { LEDMatrix, createStore } from 'led-matrix';

const store = createStore(32, 16);
const matrix = new LEDMatrix(canvasElement, {
  x: 32,
  y: 16,
  // other options...
});
matrix.setData(store.matrix);
matrix.render();
```

### Options

``` typescript
{
  x: number;
  y: number;
  pixelWidth: number;
  pixelHeight: number;
  margin: number;
  glow: boolean;
  animated: boolean;
}
```

### Store Methods

+ `store.write(x, y, text, font, size, color)`
+ `store.fill(x, y, r, g, b, a)`
+ `store.drawPixel(x, y, r, color)`
+ `store.drawLine(x1, y1, x2, y2, color)`
+ `store.drawFastVLine(x, y, h, color)`
+ `store.drawFastHLine(x, y, w, color)`
+ `store.drawRect(x, y, w, h, color)`
+ `store.drawRoundRect(x, y, w, h, radius, color)`
+ `store.drawTriangle(x1, y1, x2, y2, x3, y3, color)`
+ `store.drawCircle(x1, y1, radius, color)`
+ `store.fillScreen(color | null)`
+ `store.fillRect(x, y, w, h, color)`
+ `store.fillRoundRect(x, y, w, h, radius, color)`
+ `store.fillTriangle(x1, y1, x2, y2, x3, y3, color)`
+ `store.fillCirlce(x, y, radius, color)`
+ `store.drawBitmap(x, y, bitmap, w, h, color)`

### Color Tools

The `Store` accepts colors in `IRGBA` type:

``` typescript
interface IRGBA {
  r: number;
  g: number;
  b: number;
  a: number;
}
```

To make working with this object easier, this module exports some color conversion tools:

``` typescript
import { Color } from 'led-matrix';

Color.hex('#FF0000');
Color.hex(0xFF0000);
Color.rgba(255, 255, 255, 0.5);
```

## License

Licensed under the [MIT License](LICENSE)
