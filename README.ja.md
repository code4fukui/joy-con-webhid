# Joy-Con WebHID

Nintendo Switch のコントローラー「Joy-Con」をWebHID経由で使用できるドライバーです。ボタン、アナログスティック、ジャイロスコープ、加速度センサーなどの機能に対応しています。

## デモ

[デモページ](https://tomayac.github.io/joy-con-webhid/demo/)で実際に動作を確認できます。

<img width="800" alt="Joy-Con WebHID デモ画面。左右の Joy-Con がわずかに傾いており、片方のアナログスティックが右に倒れ、もう一方の Joy-Con の A ボタンが押されている様子が表示されている。" src="https://user-images.githubusercontent.com/145676/101152193-01fc4f80-3623-11eb-8afd-50485f2807c6.png">

Joy-ConでChrome Dino Gameをプレイできるデモ[Chrome Dino WebHID](https://github.com/tomayac/chrome-dino-webhid)もあります。

[![Joy-Con WebHID Chrome Dino デモ動画](https://img.youtube.com/vi/HuhQXXgDnCQ/0.jpg)](https://www.youtube.com/watch?v=HuhQXXgDnCQ)

## 機能

- 左右の Joy-Con の全ボタン、アナログスティック、ジャイロスコープ、加速度センサーに対応
- Joy-Con のバイブレーション機能にも対応

## 使い方

ページ上に Joy-Con とペアリングするためのボタンを設置します。

```html
<button class="connect" type="button">Joy-Con接続</button>
```

スクリプトをインポートし、ペアリングボタンにイベントハンドラを設定します。
定期的にJoy-Conの接続を確認し、接続/再接続/スリープ解除に対応します。

```js
import * as JoyCon from './node_modules/dist/index.js';

// Joy-Conの初回ペアリング。個別にペアリングする必要があります。
// ペアリング後は、次回ページ読み込み時に自動的に再接続されます。
document.querySelector('.connect').addEventListener('click', async () => {
  await JoyCon.connectJoyCon();
});

// Joy-Conはアイドル時にスリープし、触れると再び起動するため、
// 定期的にイベントリスナーを設定する必要があります。
setInterval(async () => {
  for (const joyCon of JoyCon.connectedJoyCons.values()) {
    if (joyCon.eventListenerAttached) {
      continue;
    }
    await joyCon.open();
    await joyCon.enableStandardFullMode();
    await joyCon.enableIMUMode();
    await joyCon.enableVibration();
    console.log(await joyCon.getDeviceInfo());
    await joyCon.rumble(600, 600, 0.5);
    joyCon.addEventListener('hidinput', ({ detail }) => {
      console.log(`入力報告 (${joyCon.device.productName}):`, detail);
    });
    joyCon.eventListenerAttached = true;
  }
}, 2000);
```

## ライセンス

Apache 2.0ライセンスで提供されています。