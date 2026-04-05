# スキルシート

## 学歴

<!-- 最終学歴を記載します。詳細な学校名などは記載しません。 -->

| 年月     | 学歴             |
| -------- | ---------------- |
| 2022年卒 | 高度情報専門学校 |

## 所有資格

<!-- 所有資格を記載します。 -->
<!-- 最新順に記載します。 -->

| 取得年月   | 資格名                     |
| ---------- | -------------------------- |
| 2025年12月 | 情報処理安全確保支援士     |
| 2025年6月  | AWS Developper Associate   |
| 2023年12月 | データベーススペシャリスト |
| 2023年8月  | AWS Cloud Practisoner      |
| 2022年6月  | 応用情報技術者             |
| 2021年6月  | Oracle Java Silver SE11    |
| 2019年6月  | Oracle Java Bronze SE7/8   |
| 2018年11月 | 基本情報技術者             |

## 業務経歴

<!-- 過去の業務経歴を記載します。機密情報保護のため、具体的な経歴は記載しません。 -->
<!-- 最新順に記載します。 -->

| 期間   | 役割 | 規模   | 担当工程                 | 使用技術                                                                      |
| ------ | ---- | ------ | ------------------------ | ----------------------------------------------------------------------------- |
| 12ヶ月 | SE   | 3名    | `要` `基` `詳` `開`      | SpringBoot(Java) / Vue.js(Vuetify) / MySQL / AWS / Devcontainer / Claude Code |
| 7ヶ月  | SE   | 15名   | `詳` `開` `テ`           | SpringBoot(Java) / React(shadcn) / PostgreSQL / Docker                        |
| 5ヶ月  | PG   | 5名    | `詳` `開` `テ` `保`      | SpringBoot(Java) / Echo(Go) / Laravel(PHP) / MySQL / AWS / Docker             |
| 18ヶ月 | SE   | 5名    | `基` `詳` `開` `テ`      | Echo(Go) / React(MUI) / Laravel(PHP) / MySQL / AWS / Docker / Selenium        |
| 3ヶ月  | SE   | 5名    | `要` `基` `詳` `開` `テ` | SpringBoot(Java) / Vue.js(Vuetify) / PostgreSQL / AWS / Devcontainer          |
| 9ヶ月  | SE   | 5~10名 | `基` `詳` `開` `テ`      | SpringBoot(Java) / Vue.js(Vuetify) / PostgreSQL / AWS / Devcontainer          |

**担当工程**　`要`: 要件定義 `基`: 基本設計 `細`: 詳細設計 `開`: 開発
`テ`: テスト `保`: 保守 `運`: 運用

## 公開リポジトリ

<!-- GitHubに公開しているリポジトリを記載します。使用した技術や、アーキテクチャ構成などの要約を記載します。 -->

### basic-spring-sample

**概要**

小〜中規模アプリ向けの SpringBoot スタートアッププロジェクト。JWT 認証・認可、Spring
Security、Spring
Batch によるバッチ処理、Flyway によるマイグレーション、メール送信、CSV インポート/エクスポートなど実務でよく使う機能を実装したテンプレート。Devcontainer で即起動可能。

**使用技術**

- Java 21
- SpringBoot 3.5.7
- Spring Security
- JWT(jjwt)
- Doma2
- Spring Batch
- Flyway
- MySQL
- Swagger(springdoc-openapi)
- Devcontainer

**アーキテクチャ**:

```
src/main/java/sample/
├── controller/          # プレゼンテーション層
├── service/             # アプリケーション層
├── repository/          # データアクセス層
├── entity/              # エンティティ
├── dto/                 # リクエスト/レスポンス
├── batch/               # バッチ処理（Scheduler + Tasklet）
├── types/               # 列挙型
└── utils/               # 例外・CSV・ロガー
```

### sample-spring

**概要**

Java の学習・検証向けシンプルな SpringBoot サンプル。社員情報の CRUD
API（取得・検索・登録・編集・削除・提出・承認）を実装したレイヤードアーキテクチャのリファレンス実装。

**使用技術**

- Java 21
- SpringBoot 3.4.3
- JPA(Hibernate)
- MySQL
- H2
- Swagger(springdoc-openapi)
- Lombok
- Devcontainer

**アーキテクチャ**:

```
src/main/java/sample/
├── controller/          # プレゼンテーション層
├── service/             # アプリケーション層（interface + impl）
├── repository/          # データアクセス層（interface + impl）
├── model/               # データモデル
├── dto/                 # リクエスト/レスポンス
└── context/             # 定数・例外・ユーティリティ
```

### sample-gin-ddd

**概要**

Go /
Gin フレームワークを用いた DDD アーキテクチャのサンプル。アカウント管理と TODO 管理機能を持ち、管理者とアプリユーザーの 2 種類のロールによる認証・認可を実装。

**使用技術**

- Go 1.21
- Gin
- GORM
- MySQL
- JWT(golang-jwt)
- gorilla/sessions
- Docker

**アーキテクチャ**:

```
pkg/
├── controller/          # ルーティング・ミドルウェア
├── usecase/             # ユースケース層
├── model/               # ドメインモデル
└── infrastracture/
    ├── repository/      # データアクセス層
    ├── db/              # DB接続
    ├── session/         # セッション管理
    └── security/        # セキュリティ
```

### go-gin-auth

**概要**

Go /
Gin による JWT 認証・認可の実装サンプル。ユーザーログインで JWT アクセストークンを発行し、以降の API リクエストをミドルウェアで検証する仕組みを実装。パスワードは SHA-256 でハッシュ化して DB に保存。

**使用技術**

- Go 1.21
- Gin
- GORM
- MySQL
- JWT(golang-jwt)
- gorilla/sessions

**アーキテクチャ**:

```
routers/
└── api/
    ├── auths/           # 認証（controller・middleware・model・routes・validator）
    └── books/           # 書籍（controller・middleware・model・routes・validator）
common/
├── connect/             # DB接続
├── response/            # レスポンス
└── sessions/            # セッション管理
```

### go-gin-file

**概要**

Go / Gin による REST
API 経由のファイルアップロード・ダウンロード機能の実装サンプル。ファイルは AWS
S3 互換の MinIO に格納し、ダウンロード時はファイルパス URL を返す。

**使用技術**

- Go 1.20
- Gin
- GORM
- MySQL
- AWS SDK v2(S3)
- MinIO
- Docker

**アーキテクチャ**:

```
app/
├── api/                 # コントローラ
└── models/              # データモデル
common/
├── aws.go               # AWS(S3)操作
├── db.go                # DB接続
└── response.go          # レスポンス
routes/
└── api.go               # ルーティング
```

### go-echo-mail

**概要**

Go /
Echo によるメール送信 API の実装サンプル。問い合わせ内容を受け取り、SMTP 経由で指定のメールアドレス宛にメールを送信する。開発環境では MailHog を使用してメール送受信を確認可能。

**使用技術**

- Go 1.21
- Echo v4
- GORM
- MySQL
- MailHog(開発環境)
- Docker

**アーキテクチャ**:

```
api/
├── handlers/            # ハンドラ
├── support/             # メール送信
└── validator/           # バリデーション
domain/
├── mails/               # メールモデル・ストア
└── historys/            # 履歴モデル・ストア
common/
├── db.go                # DB接続
└── response.go          # レスポンス
```

## 保有スキル

<!-- 過去の業務経歴や公開リポジトリから保有スキルを記載します。 -->

### プログラミング言語

| スキル | 経験年数 | レベル |
| ------ | -------- | ------ |
|        |          |        |

### フレームワーク・ライブラリ

| スキル | 経験年数 | レベル |
| ------ | -------- | ------ |
|        |          |        |

### インフラ・クラウド

| スキル | 経験年数 | レベル |
| ------ | -------- | ------ |
|        |          |        |

### ツール・その他

| スキル | 経験年数 | レベル |
| ------ | -------- | ------ |
|        |          |        |
