# chalmeal.github.io

## 概要

自身のスキルシートを作成するテンプレートリポジトリです。

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

### スキルシートを作成

**1. skill-sheet.mdにてテンプレートをもとに自身のスキルシートを作成**

一部の入力はClaudeに任せることができます。必要な入力は以下です。

- 学歴
- 所有資格
- 業務経歴

**2. 公開リポジトリの詳細反映**

Claudeに以下のようなプロンプトを渡すことで公開リポジトリから概要を読み取ってくれます。

```
devcontainer.jsonでマウントしているフォルダは私がGitHubで公開しているリポジトリをクローンしてきたものです。
これらのリポジトリの内容から、skill-sheet.mdの公開リポジトリセクションを記載してください。
```

> [!NOTE]
> マウントできていないとClaudeは読み取ってくれないので、マウントできているか不安な場合は以下のプロンプトを渡して確認する。

```
devcontainer.jsonにて各リポジトリがマウントできている確認したいです。マウントできている場合はREADME.mdの概要を教えてください。
```

**3. 保有スキルの作成**

保有スキルについても業務経歴や公開リポジトリの情報から自動的に作成してくれます。

```
業務経歴および公開リポジトリの内容から保有スキルを作成してください。
```

**4. 経歴概要の作成**

最後に経歴概要を作成してもらいます。

```
skill-sheet.md全体の内容から経歴概要を作成してください。経歴概要は150~200文字程度で作成してください。
```

## GitHub Pagesに反映

GitHub Pagesにてスキルシートを反映することができます。GitHub
Pagesの公開にはindex.htmlが必要です。

**1. GitHub Pagesで公開の準備**

GitHub Pagesで公開するにはいくつか準備が必要です。

- リポジトリ名
  - ユーザーサイトである場合：{ユーザー名}.github.io
  - プロジェクトサイトである場合：自由
- Publicリポジトリであること

**2. GitHub Pagesの設定確認**

Pagesのワークフロー設定作成したPagesが自動的に反映されるようにリポジトリの設定を確認します。

　2-1. GitHubのリポジトリからSettingsに遷移

　2-2. 左のメニューからPagesを押下

　2-3. Sourceで「Deploy from a branch」になっているか確認

**3. index.htmlを生成**

Claudeに以下のようなプロンプトをリクエストします。

```
skill-sheet.mdをもとに、index.htmlを生成し、HTML形式のスキルシートを作成してください。
```

**4. 生成されたindex.htmlをプッシュ**

index.htmlをプッシュすると、GitHub
Pagesのワークフローが自動的に公開してくれます。

### 番外編

`frontend-design@claude-code-plugin`を利用することで高品質なUIを生成してくれます。シンプルなスキルシートだけで問題なければ、本セクションは必須ではありません。

1. /pluginsコマンドでプラグインをインストール
2. frontend-designを選択
3. claudeに対して、どのようなデザインにしたいかを具体的にリクエストし、index.htmlを書き換えてもらう
