# chalmeal.github.io

## 概要

自身のスキルシートを作成するテンプレートリポジトリです。`frontend-design@claude-code-plugin`を利用してスキルシートを作成します。

## スキルシートの作成方法

### 記載項目

| 項目           | 説明                                                                                                   |
| -------------- | ------------------------------------------------------------------------------------------------------ |
| 学歴           | 最終学歴を記載します。詳細な学校名などは記載しません。                                                 |
| 所有資格       | 所有資格を記載します。                                                                                 |
| 業務経歴       | 過去の業務経歴を記載します。機密情報保護のため、具体的な経歴は記載しません。                           |
| 公開リポジトリ | GitHubに公開しているリポジトリを記載します。使用した技術や、アーキテクチャ構成などの要約を記載します。 |
| 保有スキル     | 過去の業務経歴や公開リポジトリから保有スキルを記載します。                                             |

### リポジトリのマウント

GitHubに公開しているリポジトリを要約してスキルシートに反映させます。リポジトリの要約はClaudeに要約してもらうため、別リポジトリのマウントを行います。

```
workspace
├── repository-1/　　　　← 各種リポジトリ
├── repository-2/
├── repository-3/
├── repository-n/
└── skill-sheet/
    ├── .devcontainer/
    │   └── devcontainer.json  ← 各種リポジトリをマウント
    ├── skill-sheet.md         ← 項目を記載
    ├── index.html             ← スキルシートを生成
    └── CLAUDE.md              ← 各種リポジトリを参照
```

devcontainer.jsonにてリポジトリのマウント

```json
"mounts": [
  // 各種リポジトリをマウント
  "source=${localWorkspaceFolder}/../repository-1,target=/workspace/repository-1,type=bind",
  "source=${localWorkspaceFolder}/../repository-2,target=/workspace/repository-2,type=bind",
  "source=${localWorkspaceFolder}/../repository-3,target=/workspace/repository-3,type=bind",
  ...
  "source=${localWorkspaceFolder}/../repository-n,target=/workspace/repository-n,type=bind",
],
```
