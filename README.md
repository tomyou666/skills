# skills

[![skills.sh](https://skills.sh/b/tomyou666/skills)](https://skills.sh/tomyou666/skills)

コミット、PR、レビュー、言語スタイルを、Agent Skills として揃える。

## インストール

```bash
npx skills@latest add tomyou666/skills
```

対話でスキルとエージェントを選ぶ。

全プロジェクトで使う場合:

```bash
npx skills@latest add tomyou666/skills -g
```

特定のスキルだけ入れる場合（`<SKILL>` をスキル名に置き換える）:

```bash
npx skills@latest add tomyou666/skills --skill <SKILL>
```

入れたか確認する:

```bash
npx skills list
```

## 呼び出し方

チャットでスキル名を付ける。Cursor なら `/スキル名` や `@スキル名`。

**User-invoked** は明示したときだけ動く。**Model-invoked** は、関連する作業を頼んだときにエージェントが選ぶこともある。確実に従わせるなら名前を付ける。

## スキル

### User-invoked

- **[ask-question-tool](./skills/ask-question-tool/SKILL.md)**: 質問を Cursor の AskQuestion ツールに載せる
- **[brief-english-final](./skills/brief-english-final/SKILL.md)**: 途中の進捗を英語1行にし、最終回答は設定言語のままにする
- **[impl-code-check](./skills/impl-code-check/SKILL.md)**: 直近差分のバグリスク・死にコード・テスト欠落・エラー処理を報告する（直さない）
- **[plan-skill-annotate](./skills/plan-skill-annotate/SKILL.md)**: 計画 markdown の各ステップに使うスキルを注記する
- **[pr-overview](./skills/pr-overview/SKILL.md)**: 非技術向けの日本語 PR/MR タイトルと本文を出す

### Model-invoked

- **[code-comments](./skills/code-comments/SKILL.md)**: 実装コメントとテスト要約を日本語にする
- **[design-to-shadcn-css](./skills/design-to-shadcn-css/SKILL.md)**: `DESIGN.md` の色トークンを shadcn の CSS 変数へ写す
- **[git-commit-en](./skills/git-commit-en/SKILL.md)**: ステージ済み差分から英語の Conventional Commits を作る
- **[git-commit-jn](./skills/git-commit-jn/SKILL.md)**: ステージ済み差分から日本語の Conventional Commits を作る
- **[go-docstring-style](./skills/go-docstring-style/SKILL.md)**: Go の関数・メソッド・フィールドに docstring を付ける
- **[go-wire](./skills/go-wire/SKILL.md)**: Google Wire の組み立てを composition root に閉じる
- **[procedure-writing](./skills/procedure-writing/SKILL.md)**: 上から実行できる手順書を書く
- **[test-overview-style](./skills/test-overview-style/SKILL.md)**: テストのスイート概要とケース名の書き方を揃える
- **[tsx-i18n-messages](./skills/tsx-i18n-messages/SKILL.md)**: TSX の表示文言を i18n メッセージへ集約する
- **[update-changelog](./skills/update-changelog/SKILL.md)**: `CHANGELOG.md` の Unreleased に日本語1行を追記する

## このリポジトリで開発する

このリポジトリ自身で Cursor からスキルを使うとき、リポジトリルートで実行する。

```bash
npx skills@latest add . -a cursor -y
```
