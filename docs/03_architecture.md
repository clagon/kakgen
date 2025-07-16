# ディレクトリ構成

本プロジェクトはクリーンアーキテクチャに基づいたディレクトリ構成を採用しています。

## 概要

依存性のルール（内側のレイヤーは外側のレイヤーを知らない）を徹底し、関心を分離することで、保守性・テスト性の高いアプリケーションを目指します。

-   **依存性の方向**: `Handler` → `Usecase` → `Repository(Interface)`

## バックエンドのディレクトリツリー

```plaintext
workspace/src/backend/
├── domain/
│   ├── model/
│   │   └── user.go # Entity (構造体)
│   └── repository/
│       └── user_repository.go # RepositoryのInterface
├── usecase/
│   └── user_usecase.go # UsecaseのInterfaceと実装
├── adapter/
│   ├── handler/
│   │   └── user_handler.go # HTTPリクエストを処理 (Echoのハンドラー)
│   └── repository/
│       └── user_repository_impl.go # Repositoryの具体的な実装 (DB操作)
├── infrastructure/
│   ├── datastore/
│   │   └── db.go # DB接続の初期化
│   └── router/
│      └── router.go # Echoのルーティング設定
├── main.go # サーバー起動、依存関係の注入(DI)
└── go.mod
```

## フロントエンドのディレクトリ構成

フロントエンドについては、Nuxt.js の標準的なディレクトリ構造に従います。各ディレクトリの役割の詳細は、Nuxt.js の公式ドキュメントを参照してください。
