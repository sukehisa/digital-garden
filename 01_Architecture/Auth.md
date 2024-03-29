---
aliases: []
tags: []
publish: true
date: 2023-07-05T14:08:55+09:00
updated: 2023-10-05T08:27:37+09:00
---
- OpenIC Connect
    - IDトークンを発行する仕様のこと
    - OAuth2.0の認可エンドポイントのリスポンスタイプ　を拡張
        - `code`: 認可コードフロー、`token`: インプリシットフロー
        - に加えて
        - `id_token`が追加
        - `code`, `token`, `id_token`　の任意の組み合わせが返せるように
        
- OAuth2.0
    - 認可エンドポイント
    - トークンエンドポイント
    - OAuth2.0には複数の認可フローがある
        - 上記、認証 or トークン or Both エンドポイントを使って、アクセストークンを取得する　ことがゴール
    - アクセストークン発行のフロー
        - Implicit Flow
            - 認可エンドポイントを使う
        - 認可コードフロー
            - 認可エンドポイントを使う
            - 認可コードを返して、アプリは、認可コードを送って、アクセストークンを取りに行く
    - アクセストークンリフレッシュのフロー
        - リフレッシュ・トークンフロー
            - 過去の認可リクエストの結果、アクセストークン＋リフレッシュトークンの発行も受けていること　が前提
            - リフレッシュトークンを、トークンエンドポイントに渡すと、アクセストークンを再発行できる
- 認可サーバ
    - On-Pre
        - Identity Server
    - SaaS (Hosted Service)
        - Octa
        - Auth0
        - カスタマイズに限界ある（e.g. 同意画面）
            - ユーザ管理：　ユーザ情報がSaaSに
            - ユーザ認証：　認証方式に限りある
    - Semi-Hosted Service
        - Authlete
- エンドユーザ認証
    - エンドユーザの一位識別子を特定する処理である
        - Authleteはエンドユーザ一位識別子を外部からもらって、アクセストークンとのひも付きを管理している
        - ユーザcredentialは持たない
    - やり方は色々ある
        - ID+Password, MFA, 指紋, …
- Deploy Pattern
    - [Deployment and Hosting Patterns in OAuth \| by Justin Richer \| Medium](https://justinsecurity.medium.com/deployment-and-hosting-patterns-in-oauth-a1666dc0d966)