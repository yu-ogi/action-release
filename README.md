# actions
akashic-games organization のリポジトリで共通で利用する Github Actions 用のアクションを管理するためのリポジトリ。
各アクションをディレクトリ単位で切り分けています。

## 各アクションについて
### release
#### 概要
指定されたリポジトリに対して以下の処理を行います。
* npm モジュールの publish　処理
  * publish時のオプションは、指定されたリポジトリのpackage.jsonの`publishConfig`の内容に準拠します。
* publish 時の バージョンで Github Release Note を作成

#### 入力パラメータ
* `github_token`: 対象リポジトリの Github トークン。必須パラメータ
* `npm_token`: 対象リポジトリの Npm パッケージの Npm トークン。必須パラメータ

### 利用例
```yml
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

### 注意点
このアクションを使用する場合、対象のパッケージでは以下の対応が必要になります。
* スコープ化された公開パッケージの場合、package.jsonの`publishConfig.access`に`"public"`を指定する必要があります。

## ビルド方法
以下のコマンドを実行

```
npm install
npm run build
```

上記コマンドによって、各アクションのディレクトリ下に`dist/index.js`というビルド成果物が生成されます。
アクションを更新するためにはビルド生成物をgit管理する必要があります。

## テスト方法
以下のコマンドを実行

```
npm test
```
