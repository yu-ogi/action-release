# actions
akashic-games organization のリポジトリで共通で利用する Github Actions 用のアクションを管理するためのリポジトリ

## 各アクションについて
### release
#### 概要
指定されたリポジトリに対して以下の処理を行います。
* npm モジュールの publish　処理
* publish 時の バージョンで Github Release Note を作成

#### 入力パラメータ
* `github_token`: 対象リポジトリの Github トークン。必須パラメータ
* `npm_token`: 対象リポジトリの Npm パッケージの Npm トークン。必須パラメータ

### Usage (利用例)
```
# relaseアクション利用前にactions/checkout等で対象のgithubリポジトリをcheckoutしておく必要があります
- name: Checkout repository
  uses: actions/checkout@v2
- name: Publish and Release
  uses: akashic-games/actions/release@master
  with:
    # 基本的にはデフォルトで設定されている秘匿変数GITHUB_TOKENを使用します
    github_token: ${{ secrets.GITHUB_TOKEN }}
    # npmトークンは予め対象のgithubリポジトリに秘匿変数として登録しておくことを推奨します
    npm_token: ${{ secrets.NPM_TOKEN }}
```

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
