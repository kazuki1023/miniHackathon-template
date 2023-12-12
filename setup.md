## [重要]issue作成方法
今回、issueはgithubActionsを用いると自動で作成されるようになってます。
- 自動で作成されたものに加えて、自分で作成したいissueがある場合は、github上で作成してもらって構いません。

大まかな流れは以下の通りです。
1. githubのtokenを取得する
2. それをルートディレクトリの.envとgithubのrepositoryのsecretに登録する
3. それをセットした状態にして、actionsタブからworkflowを実行する

## 以下詳細な流れです
### 1. githubのtokenを取得する
1-1. githubのsettingsからDeveloper settingsを選択
1-2. Personal access tokensを選択
1-3. Generate new token(classic)を選択
- 選択がわかりやすいので、こちらを選択してますが、どちらでも構いません。
1-4. Noteに任意の名前を入力
1-5. repoとworkflowにチェックを入れる
1-6. Generate tokenを押す

### 2. それをルートディレクトリの.envとgithubのrepositoryのsecretに登録する
2-1. ルートディレクトリの.envに以下を追加

```
GITHUB_TOKEN=1-6で生成したtoken
```

2-2. githubのrepositoryのsettingsからsecrets and variablesを選択

2-3. actionsを選択

2-4. New repository secretを選択

2-5. Nameに`TOKEN`と入力

2-6. Secretに1-6で生成したtokenを入力

2-7. Add secretを押す

### 3. それをセットした状態にして、actionsタブからworkflowを実行する
3-1. actionsタブを選択

3-2. `Create Issues from Markdown Templates`を選択

3-3. Run workflowを選択

3-4. Run workflowを押す(ブランチ変更しなくて大丈夫です！)

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
