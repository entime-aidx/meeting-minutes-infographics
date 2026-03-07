# 議事録インフォグラフィック GitHub Pages セットアップガイド

議事録Skillで作成したHTMLを、GitHub Pagesで公開してURL共有できるようにする手順。

---

## 前提

- GitHubアカウントがあること
- ターミナルで `git` コマンドが使えること

---

## 1. GitHubでリポジトリを作成

1. [GitHub](https://github.com) にログイン
2. **New repository** をクリック
3. 以下を設定：
   - **Repository name**: `meeting-minutes-infographics`（任意の名前でOK）
   - **Public** を選択
   - **Add a README file** は不要（空のリポジトリでOK）
4. **Create repository** をクリック

---

## 2. GitHub Pages を有効化

1. 作成したリポジトリの **Settings** を開く
2. 左メニューから **Pages** を選択
3. **Source** で **Deploy from a branch** を選択
4. **Branch** で `main`（または `master`）を選択、フォルダは **/ (root)**
5. **Save** をクリック

数分後、`https://[あなたのユーザー名].github.io/meeting-minutes-infographics/` でアクセス可能になります。

---

## 3. ローカルの議事録インフォグラフィックフォルダをリポジトリに紐づける

ターミナルで以下を実行（パスは環境に合わせて変更）：

```bash
cd "/Users/terayamataimu/Downloads/Cursor/Lark講座ナレッジ/05_コンテンツライブラリ/議事録インフォグラフィック"

# 既に .git がある場合はスキップ
git init

# リモートを追加（[ユーザー名] を自分のGitHubユーザー名に置き換え）
git remote add origin https://github.com/[ユーザー名]/meeting-minutes-infographics.git

# 初回プッシュ
git add .
git commit -m "初回: 議事録インフォグラフィック"
git branch -M main
git push -u origin main
```

**認証**：プッシュ時に GitHub のユーザー名・パスワード（または Personal Access Token）を求められます。

---

## 4. 動作確認

1. リポジトリの **Actions** タブで、デプロイが完了するまで待つ（1〜2分）
2. ブラウザで `https://[ユーザー名].github.io/meeting-minutes-infographics/議事録_20260304_名刺リニューアル打合せ.html` にアクセス
3. インフォグラフィックが表示されればOK

---

## 5. 今後の流れ

**議事録Skill** で「議事録を作って」と依頼すると：

1. 議事録・Mermaid図・HTMLが作成される
2. ブラウザで自動表示される
3. **GitHubに紐づいていれば** → 自動で `git add` → `commit` → `push` が実行され、数分後にURLで共有可能になる

---

## トラブルシューティング

| 現象 | 対処 |
|------|------|
| `git push` で認証エラー | GitHub の **Settings > Developer settings > Personal access tokens** でトークンを作成し、パスワードの代わりに入力 |
| 404 Not Found | Pages のデプロイ完了まで数分かかることがある。Actions タブでステータスを確認 |
| 既存の .git がある | `議事録インフォグラフィック` が親フォルダのリポジトリに含まれている場合、別フォルダをリポジトリ用に用意するか、親リポジトリで Pages を有効化する |

---

## 更新履歴

| 日付 | 内容 |
|------|------|
| 2025-03-07 | 初版作成 |
