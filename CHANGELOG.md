# Changelog

## [Unreleased]

## [1.5.0]

### 修正

- `ask-question-tool` に、AskQuestion が使えないときは会話形式で質問する指示を追加
- `no-local` で Write を許可した
- `pr-overview` の概要セクションを箇条書き形式で出力するよう修正

## [1.4.0]

### その他

- 英語版 README を `docs/README.md` に追加し、日本語版と相互リンクした

## [1.3.0]

### 追加

- わかりやすい解説を書く `explanation-writing` を追加
- 設計の質問を AskQuestion にまとめる `grilling4cursor` を追加
- 一回で通じる文を書く `say-once` を追加

### 修正

- `say-once` を `session` へ移した
- `update-changelog` 以外の dev スキルを、明示したときだけ動くように変更
- 用語集、金融理論集、数学チートシート、設計書のスキルを `writing` へ移し、`obsidian-` を外した
- 設計書スキルから Vault の保存先と書式を外し、保存先の指定が無いときはファイルを作らないようにした
- `obsidian-vault` から数学ノートの章立てを削除

## [1.2.0]

### 追加

- Obsidian、Qiita、提案見積、セッション制御のスキルを公開対象に追加
- `obsidian-rules` を Model-invoked の `obsidian-vault` に変更して追加

### 修正

- `procedure-writing` を明示したときだけ動くように変更

### その他

- スキルを session / dev / writing / obsidian / qiita に分け、グループ単位のインストール手順を README に追加
- `.cursor-obsidian` を削除

## [1.1.0]

### 修正

- `impl-code-check` の指摘に、該当ファイルと行を明示するよう変更

## [1.0.0]

### 追加

- Agent Skills 形式の `skills/` 配置と `npx skills add` 向け手順を追加
