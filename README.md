# Mayaドキュメント
Mayaはイベントのオンラインチケット・イベント当日の入退場管理・イベント期間内の来場者の移動履歴追跡・リアルタイム混雑情報機能を提供します。

## Mayaのリポジトリ構成

Mayaは[Maya FrontEnd](https://github.com/Maya-org/Maya-front)と[Maya BackEnd](https://github.com/Maya-org/Maya-Reservation-Backend)から成り立っています。

また、このドキュメントリポジトリ内にはこのアプリを使用する際のドキュメントが含まれています。

## 使用方法・動作環境

Mayaは基本的に[Firebase](https://firebase.google.com/)上で動作します。

MayaのフロントエンドはFlutterで構成されており、Web版以外にもAndroid・iOS版も簡単に利用できます。(但し、完璧に動作するとは限りません)

### フロントエンド
フロントエンドはいくつか設定手順があります。

- [APIエンドポイント](https://github.com/Maya-org/Maya-front/blob/main/maya_flutter/lib/api/API.dart#L20)を後述するバックエンドのURLに変更してください。
- [FlutterFire](https://firebase.flutter.dev/docs/cli/)で`flutterfire configure`を実行して`firebase_options.dart`を生成してください。
- Firebaseの[Hosting](https://firebase.google.com/docs/hosting?hl=ja)を使用してデプロイしてください。(注意:デプロイ先のアドレスによっては[index.html](https://github.com/Maya-org/Maya-front/blob/main/maya_flutter/web/index.html#L17)に変更が必要です。)
- Firebaseのプロジェクト設定からHostingのアドレスをリンクしてください。

### バックエンド
バックエンドはいくつか設定手順があります。

- [Functions](https://firebase.google.com/docs/functions)を使用してデプロイしてください。