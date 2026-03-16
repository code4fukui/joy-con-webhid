# Joy-Con WebHID

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

A [WebHID](https://web.dev/hid) driver for [Nintendo Joy-Cons](https://en.wikipedia.org/wiki/Joy-Con) with support for all buttons, analog sticks, and the device's gyroscope and accelerometer sensors.

## Features

- Support for all Joy-Con buttons, analog sticks, gyroscope, and accelerometer
- Vibration control
- Support for the Nintendo Switch HVC Controller (ファミリーコンピュータ コントローラー)
- Support for the Nintendo Ring-Con

## Requirements

For **Linux**, see this [comment on Issue #3](https://github.com/tomayac/joy-con-webhid/issues/3#issuecomment-944427792) for required pre-steps.

## Usage

```bash
npm install --save joy-con-webhid
```

Make sure you have a pairing button on your page.

```html
<button class="connect" type="button">Connect Joy-Con</button>
```

Import the script and hook up the pairing button.

```js
import * as JoyCon from './node_modules/dist/index.js';

document.querySelector('.connect').addEventListener('click', async () => {
  await JoyCon.connectJoyCon();
});
```

## License

Apache 2.0.