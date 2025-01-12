# GitHub CI/CD実践

### ワークフロー
* PR作成時、ビルドとテストを実行
* リリースタグが作成されたら、コンテナイメージをデプロイ
* issueが作成されたら、ランダムにメンバーアサイン

### イベント
* 配列にすることで複数指定できる
  * `on: [push, pull_request]`

### ランナー
* ジョブの実行環境は2種類
  * Github-Hosted Runners
  * Self-Hosted Runers
* 特に理由ないならGithub-Hosted RunnersでOK
* サポートOSは3種
  * Ubuntu
  * Windows
  * MacOS

### ステップ
* ステップの実装方法は以下の2種
  * シェルコマンド
  * アクション

### 終了ステータス
* OSはコマンド実行時に、終了ステータスと呼ばれる数値を返す
* 成功時はゼロ、失敗時はゼロ以外
```sh
echo "Hello world"

# 直前の終了ステータスを確認する
echo $?
#=> 0
```

### アクション
* マーケットプライス
  * https://github.com/marketplace?query=linter

### 命名
* ジョブ名、ステップ名、ワークフロー実行名がある

### ステップ間の環境変数の共有
* 方法は2つ
  * GITHUB_OUTPUT環境変数
  * GITHUB_ENV環境変数

### GITHUB_TOKEN
* GithubAPIを実行するのに必要な認証
  * https://docs.github.com/ja/rest?apiVersion=2022-11-28
* ワークフロー開始時に自動生成され、終了すると自動的に破棄される

### コマンド

```sh
# githubログイン
gh auth login

gh --help

# レポジトリ一覧
gh repo list
gh repo list | grep practice-cicd

gh pr create --fill-first --web

# 実行中ワークフローの確認
gh run watch

# 終了ワークフローの確認
gh run view
```