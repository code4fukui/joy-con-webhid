# Joy-Con WebHID

Nintendo Switch のゲームコントローラー「Joy-Con」をWebHID経由で使用できるドライバーです。ボタン、アナログスティック、ジャイロセンサー、加速度センサーなどの機能に対応しています。

## デモ

[デモページ](https://tomayac.github.io/joy-con-webhid/demo/)で実際に動作を確認できます。

Joy-Conを使ってChrome Dino Gameをプレイできるデモ[Chrome Dino WebHID](https://github.com/tomayac/chrome-dino-webhid)もあります。

## 機能

- 左右の Joy-Con の全ボタン、アナログスティック、ジャイロスコープ、加速度センサーに対応
- Joy-Conのバイブレーション機能にも対応

## 必要環境

**Linux**の場合、[Issue #3のコメント](https://github.com/tomayac/joy-con-webhid/issues/3#issuecomment-944427792)を参照してください。

## 使い方

ページ上に Joy-Con とペアリングするためのボタンを設置し、スクリプトを読み込んでイベントハンドラを設定します。

```html
<button class="connect" type="button">Joy-Con接続</button>
```

```js
import * as JoyCon from './node_modules/dist/index.js';

document.querySelector('.connect').addEventListener('click', async () => {
  await JoyCon.connectJoyCon();
});
```

## ライセンス

Apache 2.0ライセンスで提供されています。