# ESP32_BLE_DEMO
ESP32(Arduino)でBluetooth Low Energyを使ってAndroidスマホと通信するデモです。

## 開発環境、ライブラリ
ESP32側は通常のArduino環境にESP32を追加して、更に以下のライブラリを入れて使います。

### １．[ESP32_BLE_Arduinoライブラリ](https://github.com/nkolban/ESP32_BLE_Arduino)

ESP32に標準で入っているSimoleBLEは中身がありません。Bluetoothのスキャナで見るの、ESP32が見えますが、実体は無し。このライブラリを入れて初めて実体ができます。なお、本ライブラリのexamplesもしっかりしています。

使い方については、英語ですが、[こちらのYouTube](https://www.youtube.com/watch?v=oCMOYS71NIU)で作者が解説していて、しっかり聞けば理解が進みます。（英語は辛いけど．．．）YouTubeの字幕で英語->日本語と設定して、しっかり見ましょう。

### ２．[MIT APP INVENTOR 2](http://appinventor.mit.edu/explore/)

Androidのアプリケーション開発に使います。Web上で自分のプロジェクトを作成して、QRコードを読み込んで自分のAnroidスマホと同期してデバッグ等できます。当初、使い方が判らずに戸惑いましたが、1時間ほど掛けて、英語のチュートリアル4つほど見れば、基本的な使い方は判ります。こちらもYouTubeの字幕機能を使って日本語字幕を見ましょう。ちなみに、ネット上ではApp Inventor 2を略してAI2と呼ばれている？

★★注意！★★

１．自分の開発をするには、Googleアカウントが要ります。作りましょう。

２．開発環境にアクセスするたびにキーボード設定が英語になります。自分だけかなぁ？

### ３．[MIT App Inventor Extensions BluetoothLE](http://appinventor.mit.edu/extensions/)

上記リンクの「Download .aix File」から、BluetoothLE.aixをダウンロードしてこちらに置いている、ESP32_BLE_DEMO.aiaと共に使用してください。これが無いと、標準のAI2では通常のBluetooth（古い方）しかサポートしていません。（本当は古い方のBluetoothがESP32のライブラリにあれば、早かったのですが．．．）なお、ダウンロードリンクの前に[BluetoothLE Documentation and Resources](http://iot.appinventor.mit.edu/#/bluetoothle/bluetoothleintro)ってリンクがありますが、書き換えるにはこちらの知識も必要です。

#### 参照しているHP等

[limiflog](http://www.limifrog.io/2017/05/ble-transfers-using-mit-app-inventor-for-android/)

[Androidのプログラム](https://github.com/LimiFrog/LimiFrog-SW/tree/master/firmwares_and_utilities/MIT_AppInventor2)はこちらを参照、と言うか、ほとんどそのまま使っています。当初はAI2とESP32、BLEで検索していてたどり着いたのですが、Arduinoのプログラムが見つからず、[Androidのプログラム](https://github.com/LimiFrog/LimiFrog-SW/tree/master/firmwares_and_utilities/MIT_AppInventor2)を[ESP32_BLE_Arduinoライブラリ](https://github.com/nkolban/ESP32_BLE_Arduino)と接続できるように書き換えています。また、スマホ側の受信文字が数字ではなく、文字として、次々につなぎ合わせる様になっていたので、一回ごとの数字表示に変更しています。

Arduinoがサーバ、Android(スマホ)がクライアントとして動作しています。

UUIDは正規の取得方法ではなく、[ESP32_BLE_Arduinoライブラリ](https://github.com/nkolban/ESP32_BLE_Arduino)にあった値をそのまま使用しています。

### 使い方

１．Githubから.inoと.aiaをダウンロードしておく。

２．ArduinoのESP32用設定とライブラリを入れておく。

３．AI2の.aixをダウンロードしておく。

４．ArduinoでESP32_BE_DEMO.inoをESP32に書き込む。

５．Arduinoのシリアルモニタを開いておく。（ESP32をリセットすると、接続待ちになっているのが判る）

６．あらかじめ、スマホのPlayストアで、「MIT AI2 Companion」をインストールしておく。

７．AI2でESP32_BLE_DEMO.aiaを開き、左端の「Palette」の一番下の「Extention」をクリックして、「Import extention」で３．でダウンロードした、BluetoothLE.aixを読み込みます。

８．スマホでMIT AI2 Companionを起動しておく。

９．AI2で、「Connect」メニューの下の、「AI Companion」をクリックして、QRコードを表示する。

１０．スマホのscan QR codeでQRコードを読み込む。少し画面が切り替わるまでに時間が掛かる。

１１．表示された画面の「Start Scan」を押す。下に,で区切って周辺のBluetooth機器が表示される。UART ServiceがESP32なので、何番目か見つけ、「at index:」の後ろのボックスに数字を入れて、「Connect」を押す。

１２．「Connect」の下にESP32のアドレスが表示され、シリアルモニタの数字がカウントアップし始める。

１３．「Enable data reception」をクリックすると、シリアルモニタに表示されている数字が下に表示される。

１４．「Your message here」のボックスに文字を入れて、「Send Message」を押すと、文字がシリアルモニタに表示される。

、しておき、これを起動して、
