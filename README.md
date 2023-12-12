# ３期生ミニハッカソン

## 案件者
- TLAのkazu

## 現状の課題
- 去年作成した[サークル紹介サイト](https://keiotla2023.vercel.app/)を今年も作って欲しいという依頼があった
- TLAだけじゃなくて、他のサークルからもそのような依頼があった。
- 作ること自体、そんなに難しくない。
- しかし、文言の修正依頼や写真の差し替え依頼があった時、ただでさえチーム開発等で忙しいのに、そんなのしたくない。


## プロジェクトの概要
### サークル紹介サイト管理アプリ
- サークル紹介サイトの管理アプリを作成して欲しいです
- 作成したアプリは、サークル紹介サイトの管理者(各サークルの運営代)が使うことになります
- 作成したアプリを通じて、サークル紹介サイトの管理者が、サークル紹介サイトのコンテンツを編集できるようにしてください。
- サークルの紹介サイト自体は、去年作成したもので大丈夫です。管理アプリを通じて、文言の変更であったり、写真の追加ができるようになっていればokです。
- パソコンでの使用を想定してるので、スマホでの使用は考えなくて大丈夫です。

### アプリの仕様

#### 各画面の説明
- サークル紹介サイト
    - 誰でも閲覧することができます
- ログイン画面
    - 管理者1,2によらず一緒のログイン画面で大丈夫です
- 管理者画面topページ
    - ログインしたら最初に見れるページ
    - sidebarのtopページボタンを押しても表示されます
    - 管理者１は今いる管理者が一覧で見れるようにしてください
    - 管理者２は全ての管理者が一覧で見れるようにしてください

- 管理者画面サークル編集ページ
    - sidebarのサークル名を押したら表示されるページ
    - 管理者１は自分たちのサークルのコンテンツの編集ができるようにしてください
    - 管理者２も同様のことができるようにしてください
        - ただし、管理者２はsidebarに全てのサークルが表示されています

- 管理者作成ページ
    - 管理者２のみサイドバーに作成ボタンが表示され、それを押すと表示されるページ
    - 新たに管理者１を作成することができるようにしてください
    - サークル名、最初の管理者の名前、メールアドレス、パスワードを入力して、作成ボタンを押すと、管理者１が作成されます。

- 管理者profileページ
    - breezeで作成されるもので大丈夫です
    - 管理者１、２ともに自分のprofileページで、パスワードの変更ができるようにしてください
    - 管理者１はアカウント削除できないようにしてください(表示されない)ようにしてください
    - 管理者２はアカウント削除できるようにしてください


#### 管理者の説明
- 管理者は２種類います
    - 管理者1. サークル紹介サイトの管理者(各サークルの運営代)
    - 管理者2. サークル紹介サイトの管理アプリの管理者(このアプリの管理者である我々)
  - 管理者１のできること
    - 自分たちのサークル紹介サイトのコンテンツの編集
    - 自分たちのサークル紹介サイト管理者画面へのログイン
    - 管理者画面へのログイン権限の付与

  - 管理者２のできること
    - 管理者1のできること全部
    - 最初に管理者１を作成する機能
    - 各管理者の削除機能
    - 各管理者画面へのログイン
    - 管理者２権限の付与





## issue
- issueで作成してあるので、全部やってください

## 作業の進め方
- forkしてclone
- issue番号のブランチを作成して作業
- タスクはprojectで管理してください

## 注意
- 一部の需要を考慮して`arisatan`コマンドでも動くようになってます
- 配色等は各自変更してもらって大丈夫ですが、以下の条件を守ってください
    - tailwind以外使わない
    - tailwind.config.jsにcolorの設定を書く
        - ここはjoberに聞いてください
- 作業前のnodeコンテナで以下のコマンドを実行してください
```
docker compose exec node npm run dev
```

- これは、nodeコンテナでnpm run devを実行するコマンドです。
- これでtailwind等のコンパイルができるようになります。

- 作業後、以下のコマンドを実行してください
```
docker compose exec app composer analyse
```
- エラーが出たら、修正してください
- これは静的解析を行うコマンドです。
  - 静的解析とは、コードの品質をチェックすることです。

```
docker compose exec node npx prettier --write .
```
- これは、prettierを実行するコマンドです。
- これでコードのフォーマットが整います。

## 環境構築方法
```
    ### Laravel インストール方法
    1. `docker compose build --no-cache` (ビルドする)
    2. `docker compose up -d` (コンテナをたてる)
    3. `docker compose exec app sh` (appコンテナに入る)
    4. `composer create-project --prefer-dist laravel/laravel . "10.*"` (src配下にLaravel10をインストール)
    5. ブラウザで `http://localhost` にアクセスし、Laravelのロゴ入りのトップページが表示されることを確認
```

<img width="1446" alt="スクリーンショット 2023-06-09 19 39 34" src="https://github.com/posse-ap/template-ph3-website/assets/33271639/69d42fe3-4e3a-4087-91a9-c55640a2671f">

1. `src > .env` の内容を以下のように書き換える
    ```
    DB_CONNECTION=mysql
    DB_HOST=mysql
    DB_PORT=3306
    DB_DATABASE=website
    DB_USERNAME=posse
    DB_PASSWORD=password
    ```
2. 以下のコマンドを打つ
```
make arisatan
```
