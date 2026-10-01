# skills

[English](./docs/README.md)

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

# 手順書、提案見積、締結見積・請書、解説、用語集、理論集、数式ノート、設計書
npx skills@latest add tomyou666/skills/skills/writing

# Vault のフォルダ・命名・書式
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
- **[grilling4cursor](./skills/session/grilling4cursor/SKILL.md)**（User-invoked）: 設計をラウンドで聞き、前提が揃った質問を AskQuestion にまとめる。共有理解の確認まで着手しない
- **[no-local](./skills/session/no-local/SKILL.md)**（User-invoked）: ローカルのファイルやコマンドを使わず、解除までその状態を保つ
- **[no-write](./skills/session/no-write/SKILL.md)**（User-invoked）: ファイルの作成・編集・削除をせず、解除までその状態を保つ
- **[say-once](./skills/session/say-once/SKILL.md)**（User-invoked）: 普通の大人が一回で聞ける言葉だけを使い、まだ知らないことだけを書く

### dev

実装、Git、レビュー。

- **[git-commit-en](./skills/dev/git-commit-en/SKILL.md)**（User-invoked）: ステージ済み差分から英語の Conventional Commits を作る
- **[git-commit-jn](./skills/dev/git-commit-jn/SKILL.md)**（User-invoked）: ステージ済み差分から日本語の Conventional Commits を作る
- **[code-comments](./skills/dev/code-comments/SKILL.md)**（User-invoked）: 実装コメントとテスト要約を日本語にする
- **[design-to-shadcn-css](./skills/dev/design-to-shadcn-css/SKILL.md)**（User-invoked）: `DESIGN.md` の色トークンを shadcn の CSS 変数へ写す
- **[go-docstring-style](./skills/dev/go-docstring-style/SKILL.md)**（User-invoked）: Go の関数・メソッド・フィールドに docstring を付ける
- **[go-wire](./skills/dev/go-wire/SKILL.md)**（User-invoked）: Google Wire の組み立てを composition root に閉じる
- **[test-overview-style](./skills/dev/test-overview-style/SKILL.md)**（User-invoked）: テストのスイート概要とケース名の書き方を揃える
- **[tsx-i18n-messages](./skills/dev/tsx-i18n-messages/SKILL.md)**（User-invoked）: TSX の表示文言を i18n メッセージへ集約する
- **[update-changelog](./skills/dev/update-changelog/SKILL.md)**（Model-invoked）: `CHANGELOG.md` の Unreleased に日本語1行を追記する
- **[impl-code-check](./skills/dev/impl-code-check/SKILL.md)**（User-invoked）: 直近差分のバグリスク・死にコード・テスト欠落・エラー処理を報告する（直さない）
- **[plan-skill-annotate](./skills/dev/plan-skill-annotate/SKILL.md)**（User-invoked）: 計画 markdown の各ステップに使うスキルを注記する
- **[pr-overview](./skills/dev/pr-overview/SKILL.md)**（User-invoked）: 非技術向けの日本語 PR/MR タイトルと本文を出す

### writing

手順書、提案見積、締結見積・請書、解説、用語集、理論集、数式ノート、設計書。

- **[design-doc-builder](./skills/writing/design-doc-builder/SKILL.md)**（User-invoked）: 要求から設計書を章ごとに分ける。保存先の指定が無いときはファイルを作らない
- **[explanation-writing](./skills/writing/explanation-writing/SKILL.md)**（User-invoked）: 全体像から入るわかりやすい解説を書く・書き直す
- **[finance-theory-collection](./skills/writing/finance-theory-collection/SKILL.md)**（User-invoked）: 金融理論集を共通形式で作る・追記する（Obsidian ノートの書式）
- **[glossary-writing](./skills/writing/glossary-writing/SKILL.md)**（User-invoked）: 用語集を平易な説明と最小限の理論で書く（Obsidian ノートの書式）
- **[it-solo-contract-drafts](./skills/writing/it-solo-contract-drafts/SKILL.md)**（User-invoked）: IT自営業の準委任・請負の締結TODOと、見積書・注文請書のドラフトを作る
- **[math-cheat-sheet](./skills/writing/math-cheat-sheet/SKILL.md)**（User-invoked）: 数学チートシート形式のノートを作る・更新する（Obsidian ノートの書式）
- **[procedure-writing](./skills/writing/procedure-writing/SKILL.md)**（User-invoked）: 上から実行できる手順書を書く
- **[proposal-estimate-draft](./skills/writing/proposal-estimate-draft/SKILL.md)**（User-invoked）: 顧客向けの提案書と概算見積明細を Markdown で作る・改訂する

### obsidian

Vault のフォルダ・命名・書式。

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
