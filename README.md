# SpeakSDK for C++ サンプルアプリケーション
本ソースコードは株式会社NTTドコモが提供するドコモAIエージェントAPI [SpeakSDK](https://github.com/docomoDeveloperSupport/speak-cpp-sdk)のサンプルコードです。


## 動作条件
1. Raspberry Pi 3 Model B (OS: Raspbian 4.14)
1. Speak SDK(1.6.1以上)
1. Python3 (GetDeviceToken.pyを利用するために必要)

## GetDeviceToken.pyの使用
対話サービスを利用するにはデバイスIDの登録とデバイストークンの取得が必要です。  
スクリプト中における `client_secret` はダミー値であるため、ご自身で取得した値に書き換えて実行してください。

GetDeviceToken.pyを実行すると以下の様にデバイスID登録用のURLを表示して登録の完了を待機します。

```
$ python3 GetDeviceToken.py
Success to get DeviceID :xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
デバイスIDの取得に成功しました。
Please register DeviceID as your device on User Dashboard.
下記リンク（↓）を使ってブラウザ等でデバイスIDを自分のアカウントに登録して下さい。
https://doufr.aiplat.jp/device/regist?directAccess=true&deviceId=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

Press any key AFTER registration >>> 
```

ブラウザでURLにアクセスしてデバイスID登録を完了させて下さい。  
登録にはGoogleアカウントまたはdアカウントによる認証が必要です。  
登録が完了したらEnterを入力して下さい。

```
Success to get DeviceToken : xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
デバイストークンの取得に成功しました。
Success to get RefreshToken : xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
リフレッシュトークンの取得に成功しました。
```

GetDeviceToken.pyはデバイストークンとリフレッシュトークンを取得して標準出力に表示します。

> リフレッシュトークンはデバイストークンの更新に使用します。  
GetDeviceToken.pyは取得したリフレッシュトークンを隠しファイルに保存しています。
デバイストークンの使用期限が切れた時はGetDeviceToken.pyを再び実行して下さい。
保存したリフレッシュトークンでデバイストークンを更新します。


## speak_sample.cppのコンパイル

Speak SDKがインストールされたRaspberry Pi上で以下のコマンドでコンパイルします。

```
$ g++ --std=c++11 -lspeak -o speak_sample speak_sample.cpp
```

"speak_sample"という実行バイナリが生成されます。


## speak_sample.cppの使用

コマンドライン引数に接続先URLとデバイストークンを与えて起動します。

```
$ ./speak_sample wss://dospf.aiplat.jp/ciel [device token]
```

起動すると音声対話ができます。

## License
本サンプルコードは以下の修正BSDライセンスが適用されます。

[LICENSE.txt](/LICENSE.txt)

また本サンプルアプリケーションの動作に必要となる[SpeakSDK](https://github.com/docomoDeveloperSupport/speak-cpp-sdk)の利用にあたっては下記ソフトウェア開発キットの利用に関する規約が適用されます。規約をご確認のうえ利用をお願いいたします。

[ソフトウェア開発キットの利用に関する規約](https://github.com/docomoDeveloperSupport/speak-cpp-sdk/blob/master/LICENSE.md)

## Acknowledgments
This product includes software developed by the OpenSSL Project for use in the OpenSSL Toolkit. (http://www.openssl.org/)  
This product includes cryptographic software written by Eric Young (eay@cryptsoft.com)

## Author
[NTT DOCOMO, INC.](https://docs.sebastien.ai/)






