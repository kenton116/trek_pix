# 開発計画

## 技術選定と環境構築（1週間）

- Flutterのセットアップ
- 必要なプラグインやライブラリの調査と導入

## 要件定義と設計（2週間）

- 要件定義の確認と整理
- UI/UXデザインの初期設計

## 基本機能の開発（4週間）

- ユーザー認証（Firebase Authentication）
- 写真の投稿、フィード表示、保存済み写真の表示
- プロフィール管理、お知らせ機能、プッシュ通知

## 地図関連機能の開発（3週間）

- Google Maps APIの統合
- 写真の撮影地までの経路表示、撮影地の保存機能

## テストとデバッグ（3週間）

- 単体テスト、統合テスト、UI/UXテスト
- バグ修正と最適化

## デプロイとリリース（1週間）

- App StoreとGoogle Playへのデプロイ
- リリース前の最終テストと確認

# 要件定義
  
## プラットフォームサポート

- iOS（最新バージョンと前のバージョンのサポート）
- Android（最新バージョンと前のバージョンのサポート）

## UI/UX

- クロスプラットフォームに適したデザイン
- 画面サイズと解像度の適応

## 機能

- ユーザー認証（メール/パスワード、Google、Apple）
- プロフィール管理（ユーザー名、アイコン）
- お知らせ機能、プッシュ通知
- 写真の投稿、フィード表示、保存済み写真の表示
- 地図関連機能（Google Maps API）

# データモデリング

## ユーザー
### UserProfile

- userProfileID: 主キー、ユニークなユーザーID
- userID: 外部キー、関連するユーザーのuid
- createdAt: アカウント作成日時
- lastLogin: 最終ログイン日時

## 写真
### Photo

- photoID: 主キー、ユニークな写真ID
- userID: 外部キー、関連するユーザーID
- image: 写真のURLまたはバイナリデータ
- caption: 写真の説明やキャプション
- location: 撮影場所（経度、緯度など）
- tags: タグ（配列やリスト形式）
- createdAt: 写真の投稿日時

### Like

- likeID: 主キー、ユニークないいねID
- userID: 外部キー、いいねをしたユーザーID
- photoID: 外部キー、いいねをした写真ID
- createdAt: いいねした日時

## Comment

- commentID: 主キー、ユニークなコメントID
- userID: 外部キー、コメントをしたユーザーID
- photoID: 外部キー、コメントされた写真ID
- content: コメントの内容
- createdAt: コメントの投稿日時


## お知らせ
### Notification

- notificationID: 主キー、ユニークな通知ID
- userID: 外部キー、通知を受け取るユーザーID
- photoID: 外部キー、関連する写真ID
- senderID:外部キー、通知を送信するユーザーのID
- type: 通知の種類（いいね、コメントなど）
- message: 通知メッセージ
- createdAt: 通知の送信日時
- isRead: 既読・未読の状態

## 保存済み写真
### SavedPhoto

- savedPhotoID: 主キー、ユニークな保存済み写真ID
- userID: 外部キー、保存したユーザーのID
- photoID: 外部キー、保存された写真のID
- categoryID: 外部キー、カテゴリのID
- saveDate: 写真を保存した日時

### Category

- categoryID: 主キー、ユニークなカテゴリID
- userID: 外部キー、カテゴリを作成したユーザーのID
- categoryName: カテゴリ名