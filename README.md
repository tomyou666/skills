# skills

[![skills.sh](https://skills.sh/b/tomyou666/skills)](https://skills.sh/tomyou666/skills)

コミット、レビュー、文書、Obsidian、Qiita の作業を、Agent Skills として揃える。

## インストール

対話でスキルとエージェントを選ぶ。

```bash
npx skills@latest add tomyou666/skills
```

全プロジェクトで使う場合は、各コマンドの末尾に `-g` を付ける。

特定のスキルだけ入れる場合（`<SKILL>` をスキル名に置き換える）:

```bash
npx skills@latest add tomyou666/skills --skill <SKILL>
```

### グループ

必要なグループだけ入れる。

```bash
# 会話の振る舞い
npx skills@latest add tomyou666/skills/skills/session

# 実装、Git、レビュー 
npx skills@latest add tomyou666/skills/skills/dev

# 手順書と提案見積
npx skills@latest add tomyou666/skills/skills/writing

# Vault のノート
npx skills@latest add tomyou666/skills/skills/obsidian

# Qiita 記事
npx skills@latest add tomyou666/skills/skills/qiita
```

入れたか確認する:

```bash
npx skills list
```

## 呼び出し方

チャットでスキル名を付ける。Cursor なら `/スキル名` や `@スキル名`。

**User-invoked** は明示したときだけ動く。**Model-invoked** は、関連する作業を頼んだときにエージェントが選ぶこともある。確実に従わせるなら名前を付ける。

## スキル

### session

会話の振る舞い。

- **[ask-question-tool](./skills/session/ask-question-tool/SKILL.md)**（User-invoked）: 質問を Cursor の AskQuestion ツールに載せる
- **[brief-english-final](./skills/session/brief-english-final/SKILL.md)**（User-invoked）: 途中の進捗を英語1行にし、最終回答は設定言語のままにする
- **[no-local](./skills/session/no-local/SKILL.md)**（User-invoked）: ローカルのファイルやコマンドを使わず、解除までその状態を保つ
- **[no-write](./skills/session/no-write/SKILL.md)**（User-invoked）: ファイルの作成・編集・削除をせず、解除までその状態を保つ

### dev

実装、Git、レビュー。

- **[git-commit-en](./skills/dev/git-commit-en/SKILL.md)**（Model-invoked）: ステージ済み差分から英語の Conventional Commits を作る
- **[git-commit-jn](./skills/dev/git-commit-jn/SKILL.md)**（Model-invoked）: ステージ済み差分から日本語の Conventional Commits を作る
- **[code-comments](./skills/dev/code-comments/SKILL.md)**（Model-invoked）: 実装コメントとテスト要約を日本語にする
- **[design-to-shadcn-css](./skills/dev/design-to-shadcn-css/SKILL.md)**（Model-invoked）: `DESIGN.md` の色トークンを shadcn の CSS 変数へ写す
- **[go-docstring-style](./skills/dev/go-docstring-style/SKILL.md)**（Model-invoked）: Go の関数・メソッド・フィールドに docstring を付ける
- **[go-wire](./skills/dev/go-wire/SKILL.md)**（Model-invoked）: Google Wire の組み立てを composition root に閉じる
- **[test-overview-style](./skills/dev/test-overview-style/SKILL.md)**（Model-invoked）: テストのスイート概要とケース名の書き方を揃える
- **[tsx-i18n-messages](./skills/dev/tsx-i18n-messages/SKILL.md)**（Model-invoked）: TSX の表示文言を i18n メッセージへ集約する
- **[update-changelog](./skills/dev/update-changelog/SKILL.md)**（Model-invoked）: `CHANGELOG.md` の Unreleased に日本語1行を追記する
- **[impl-code-check](./skills/dev/impl-code-check/SKILL.md)**（User-invoked）: 直近差分のバグリスク・死にコード・テスト欠落・エラー処理を報告する（直さない）
- **[plan-skill-annotate](./skills/dev/plan-skill-annotate/SKILL.md)**（User-invoked）: 計画 markdown の各ステップに使うスキルを注記する
- **[pr-overview](./skills/dev/pr-overview/SKILL.md)**（User-invoked）: 非技術向けの日本語 PR/MR タイトルと本文を出す

### writing

手順書と提案見積。

- **[procedure-writing](./skills/writing/procedure-writing/SKILL.md)**（User-invoked）: 上から実行できる手順書を書く
- **[proposal-estimate-draft](./skills/writing/proposal-estimate-draft/SKILL.md)**（User-invoked）: 顧客向けの提案書と概算見積明細を Markdown で作る・改訂する

### obsidian

Vault のノート。

- **[obsidian-design-doc-builder](./skills/obsidian/obsidian-design-doc-builder/SKILL.md)**（User-invoked）: 要求から Obsidian 向け設計書を章ごとに分ける
- **[obsidian-finance-theory-collection](./skills/obsidian/obsidian-finance-theory-collection/SKILL.md)**（User-invoked）: 金融理論集ノートを共通形式で作る・追記する
- **[obsidian-glossary-writing](./skills/obsidian/obsidian-glossary-writing/SKILL.md)**（User-invoked）: 用語集を平易な説明と最小限の理論で書く
- **[obsidian-math-cheat-sheet](./skills/obsidian/obsidian-math-cheat-sheet/SKILL.md)**（User-invoked）: 数学チートシート形式のノートを作る・更新する
- **[obsidian-vault](./skills/obsidian/obsidian-vault/SKILL.md)**（Model-invoked）: Vault のフォルダ構成、命名、作成フロー、Markdown と数式の書式に従う

### qiita

Qiita 記事。

- **[qiita-article-planner](./skills/qiita/qiita-article-planner/SKILL.md)**（User-invoked）: テーマとペルソナを聞いて見出し構成を作る
- **[qiita-sample-pattern-extractor](./skills/qiita/qiita-sample-pattern-extractor/SKILL.md)**（User-invoked）: サンプル記事からいいねが付きやすい型を抽出する
- **[qiita-writing-principles](./skills/qiita/qiita-writing-principles/SKILL.md)**（User-invoked）: いいねが付きやすい記事の構成と読者設計をチェックする

## このリポジトリで開発する

このリポジトリ自身で Cursor からスキルを使うとき、リポジトリルートで実行する。

```bash
npx skills@latest add . -a cursor -y
```
