# このドキュメントを読む前に
このドキュメントは、データベースの構造を説明します。

ただし、このドキュメントで扱われているデータの多くはMayaによって自動的に管理されており、不用意に触るべきではありません。

## おそらく触るであろうデータ一覧
- [admin]()
- [events]()
- [ticketTypes]()

# DBの構成について

Mayaでは各種イベント情報や混雑情報などをすべてFirebaseの[RealTimeDB](https://firebase.google.com/docs/database)
あるいは、[FireStore](https://firebase.google.com/docs/firestore)に保存しています。

このドキュメントでは、そこに保存されるデータの構成を説明します。

# 使用されるDBの種類について

イベントの予約情報などはすべて[FireStore](https://firebase.google.com/docs/firestore)に保存されます。

リアルタイム更新の混雑状況はすべて[RealTimeDB](https://firebase.google.com/docs/database)に保存されます。

# FireStore内のデータの構造について

使用されるデータ構造のルートコレクションは以下の通りです。

**詳しいデータ構造については[Backend](https://github.com/Maya-org/Maya-Reservation-Backend/blob/main/openapi/reference/Reservation-API.json)のOpenAPIドキュメントを参照してください。**

- [admin]()
- [events]()
- [reservations]()
- [rooms]()
- [ticketTypes]()
- [tickets]()
- [track]()

## admin
`admin`は主に権限情報を保存します。

`uid`のドキュメントの下に権限情報を保存します。

構造は以下の画像の通りです。
![admin](img/admin.png)

## events
`events`はイベント情報を保存します。

イベント情報はイベントIDをキーとして保存します。

構造は以下の画像の通りです。
![events_1](img/events_1.png)
![events_2](img/events_2.png)

## reservations
`reservations`は予約情報を保存します。

予約情報は`uid`をキーとして、その下の`reservations`コレクションの中に予約IDをキーとして保存します。

構造は以下の画像の通りです。
![reservations_1](img/reservations_1.png)
![reservations_2](img/reservations_2.png)

## rooms
`rooms`は部屋情報を保存します。

部屋情報は部屋IDをキーとして保存します。

構造は以下の画像の通りです。
![rooms_1](img/rooms_1.png)
![rooms_2](img/rooms_2.png)

## ticketTypes
`ticketTypes`はチケットタイプ情報を保存します。

チケットタイプ情報はチケットタイプIDをキーとして保存します。

構造は以下の画像の通りです。
![ticketTypes_1](img/ticketTypes_1.png)

## tickets
`tickets`はチケット情報を保存します。

チケット情報はチケットIDをキーとして保存します。

構造は以下の画像の通りです。
![tickets_1](img/tickets_1.png)

## track
`track`はお客さんの移動履歴を保存します。

移動履歴データはチケットIDをキーとして保存し、その下の`tracks`コレクションに移動履歴を保存します。

構造は以下の画像の通りです。
![track_1](img/track_1.png)
![track_2](img/track_2.png)

# RealTimeDB内のデータの構造について
RealTimeDB内には現在のお客さんの滞在状況を保存します。

部屋のIDをキーとして、その値に現在の滞在人数を保存します。

構造は以下の画像の通りです。
![track_3](img/track_3.png)