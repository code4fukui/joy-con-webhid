# Joy-Con WebHID

すべてのボタン、アナログスティック、およびデバイスのジャイロスコープと加速度センサーをサポートする、[Nintendo Joy-Cons](https://en.wikipedia.org/wiki/Joy-Con)用の[WebHID](https://web.dev/hid)ドライバです。

## 機能

- Joy-Conのすべてのボタン、アナログスティック、ジャイロスコープ、加速度センサーのサポート
- 振動制御
- Nintendo Switch HVC Controller（ファミリーコンピュータ コントローラー）のサポート
- Nintendo Ring-Conのサポート

## 必要条件

**Linux**の場合、事前に必要な手順について、[Issue #3のこちらのコメント](https://github.com/tomayac/joy-con-webhid/issues/3#issuecomment-944427792)を参照してください。

## 使い方

```bash
npm install --save joy-con-webhid
```

ページ内にペアリング用のボタンを配置してください。

```html
<button class="connect" type="button">Connect Joy-Con</button>
```

スクリプトをインポートし、ペアリングボタンに処理を紐付けます。

```js
import * as JoyCon from './node_modules/dist/index.js';

document.querySelector('.connect').addEventListener('click', async () => {
  await JoyCon.connectJoyCon();
});
```

## ライセンス

Apache 2.0
