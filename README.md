# @takajourei/react-zoom-pan-pinch

This is a fork of
[react-zoom-pan-pinch](https://github.com/prc5/react-zoom-pan-pinch) created in
order to fix transform translate3d to transform matrix.

> Super fast and light react npm package for zooming, panning and pinching html
> elements in easy way

## Features

- :rocket: Fast and easy to use
- :factory: Light, without external dependencies
- :gem: Mobile gestures, touch gestures and desktop mouse events support
- :gift: Powerful context usage, which gives you a lot of freedom
- :wrench: Highly customizable
- :crown: Animations and Utils to create own tools

## Help me keep working on this project ❤️

- [Become a Sponsor on GitHub](https://github.com/sponsors/prc5)

---

## Installation

```bash
npm install --save @takajourei/react-zoom-pan-pinch
```

or

```bash
yarn add @takajourei/react-zoom-pan-pinch
```

## Examples

```jsx
import React, { Component } from "react";

import { TransformWrapper, TransformComponent } from "@takajourei/react-zoom-pan-pinch";

export const Example = () => (
  <TransformWrapper>
    <TransformComponent>
      <img src="image.jpg" alt="test" />
    </TransformComponent>
  </TransformWrapper>
);
```

or

```jsx
import React, { Component } from "react";

import { TransformWrapper, TransformComponent } from "react-zoom-pan-pinch";

export const Example = () => (
  <TransformWrapper
    initialScale={1}
    initialPositionX={200}
    initialPositionY={100}
  >
    {({ zoomIn, zoomOut, resetTransform, ...rest }) => (
      <>
        <div className="tools">
          <button onClick={() => zoomIn()}>+</button>
          <button onClick={() => zoomOut()}>-</button>
          <button onClick={() => resetTransform()}>x</button>
        </div>
        <TransformComponent>
          <img src="image.jpg" alt="test" />
          <div>Example text</div>
        </TransformComponent>
      </>
    )}
  </TransformWrapper>
);
```

or

```tsx
import React, { useRef } from "react";
import {
  TransformWrapper,
  TransformComponent,
  ReactZoomPanPinchRef,
} from "react-zoom-pan-pinch";

const Controls = ({ zoomIn, zoomOut, resetTransform }) => (
  <>
    <button onClick={() => zoomIn()}>+</button>
    <button onClick={() => zoomOut()}>-</button>
    <button onClick={() => resetTransform()}>x</button>
  </>
);

const Component = () => {
  const transformComponentRef = useRef<ReactZoomPanPinchRef | null>(null);

  const zoomToImage = () => {
    if (transformComponentRef.current) {
      const { zoomToElement } = transformComponentRef.current;
      zoomToElement("imgExample");
    }
  };

  return (
    <TransformWrapper
      initialScale={1}
      initialPositionX={200}
      initialPositionY={100}
      ref={transformComponentRef}
    >
      {(utils) => (
        <React.Fragment>
          <Controls {...utils} />
          <TransformComponent>
            <img src="image.jpg" alt="test" id="imgExample" />
            <div onClick={zoomToImage}>Example text</div>
          </TransformComponent>
        </React.Fragment>
      )}
    </TransformWrapper>
  );
};
```

## License

MIT © [TakajouRei](https://github.com/TakajouRei)
