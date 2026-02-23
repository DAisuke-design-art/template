# Secure Repository Template

機密情報（APIキー、パスワードなど）をGitHubにアップロードせずに安全に管理するための初期設定テンプレートです。

## 📁 構成ファイル

- **`.gitignore`**: 機密情報を含むファイル（`.env`など）やシステムファイル、依存関係フォルダがGitにコミットされないように指定します。
- **`.env.example`**: 必要な環境変数のキーのみを定義したテンプレートファイルです。実際の値は含めません。

## 🚀 使い方

### 1. リポジトリの初期化

このテンプレートをプロジェクトのルートディレクトリに配置します。

### 2. 環境変数の設定

1. `.env.example` をコピーして `.env` ファイルを作成します。
   ```bash
   cp .env.example .env
   ```
2. `.env` ファイルを開き、実際のAPIキーやパスワードを入力します。
   ```ini
   # .env
   GITHUB_TOKEN=ghp_abc123...
   OPENAI_API_KEY=sk-xyz789...
   ```
   **注意**: `.env` ファイルは `.gitignore` に含まれているため、GitHubにはアップロードされません。

### 3. Gitへのコミット

通常通り開発を進め、コミットします。

```bash
git add .
git commit -m "Initial commit with secure template"
git push origin main
```

## ⚠️ セキュリティのベストプラクティス

1. **`.env` は絶対にコミットしない**: 誤って `git add -f .env` などで強制的に追加しないように注意してください。
2. **`.env.example` を更新する**: アプリケーションで新しい環境変数が必要になった場合は、常に `.env.example` にもキーを追加し、チームメンバーや将来の自分が分かるようにしてください。
3. **誤ってアップロードした場合**: もし誤って機密情報をプッシュしてしまった場合は、直ちにそのキー（APIキーなど）を無効化（Revoke）し、再発行してください。Gitの履歴から削除するだけでは不十分な場合があります。

## 📚 推奨ツール

- **[Python-dotenv](https://pypi.org/project/python-dotenv/)** (Python): `.env` ファイルを読み込むためのライブラリ。
- **[Dotenv](https://www.npmjs.com/package/dotenv)** (Node.js): `.env` ファイルを読み込むためのライブラリ。
- **[git-secrets](https://github.com/awslabs/git-secrets)**: コミット時に機密情報が含まれていないかチェックするツール。
