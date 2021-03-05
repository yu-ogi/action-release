# actions
akashic-games organization のリポジトリで共通で利用する Github Actions 用のアクションを管理するためのリポジトリ

## 各アクションについて
### release
#### 概要
指定されたリポジトリに対して以下の処理を行います。
* npm モジュールの publish　処理
* publish 時の バージョンで Github Release Note を作成

#### 入力パラメータ
* `target_repository`: このアクションの対象リポジトリ。ただし、akashic-games organization に属するリポジトリ名を入力する必要がある。
* `target_branch`: このアクションの対象ブランチ。ここで入力したブランチの内容で Publish と GitHub での Tag 打ちが行われる。デフォルト値は master。
* `target_npm_tag`: publish したバージョンにここで入力した名前のタグが付けられる。デフォルト値はlatest。
* `target_dir_path`: 対象リポジトリのルートパス。具体的には、package.json や CHANGELOG.md が配置されているパス。
* `github_token`: 対象リポジトリの Github トークン
* `npm_token`: 対象リポジトリの Npm パッケージの Npm トークン

## ビルド方法
以下のコマンドを実行 

```
npm install
npm run build
```

## テスト方法
以下のコマンドを実行

```
npm test
```
