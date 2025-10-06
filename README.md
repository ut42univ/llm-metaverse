# Project LLMeta

## 概要

Project LLMeta は、ユーザーが共有の 3D 空間でリアルタイムに交流し、AI によるコミュニケーション支援を受けられる軽量な WebXR メタバース体験プロジェクトです。

## 主な機能

- **リアルタイムコミュニケーション:** 最大 10 名のユーザーが、空間オーディオを備えた 3D 空間で円滑に音声会話できます。
- **AI による支援:** 各ユーザーにパーソナライズされた AI エージェントが、会話の要約、解説、関連画像の自動生成など、コミュニケーションを豊かにします。
- **クロスプラットフォーム:** デスクトップブラウザおよび XR デバイスからシームレスにアクセス可能です。

## システムアーキテクチャ

システムは、フロントエンド、バックエンドサービス、AI エージェントの 3 層で構成されています。詳細については `docs/system-architecture.md` を参照してください。

```mermaid
graph LR
    subgraph "User"
        UserBrowser["🌐 User's Browser"]
    end

    subgraph "Frontend"
        Client["<b>Client (Next.js)</b>"]
    end

    subgraph "Backend Services"
        Colyseus["<b>Multiplayer Server</b><br/>(Colyseus)"]
        LiveKit["<b>Media Server</b><br/>(LiveKit SFU)"]
        Supabase["<b>Auth & DB</b><br/>(Supabase)"]
        AIService["<b>AI Service</b><br/>(FastAPI, Whisper, LLM, Image Gen)"]
    end

    subgraph "AI Agents (Scalable)"
        AIAgentPool["🤖 <b>AI Agent Pool</b><br/>(1 Agent per User)"]
    end

    UserBrowser --> Client

    Client -- "Auth (JWT)" --> Supabase
    Client -- "Join with JWT" --> Colyseus
    Client -- "Join with JWT" --> LiveKit

    Colyseus -- "Public State (Images, etc.)" <--> Client
    Colyseus -- "Private Messages (Summaries, etc.)" --> Client
    LiveKit -- "Audio/Video Stream" <--> Client

    %% AI Agent Flow
    AIAgentPool -- "Connects as Client" --> LiveKit
    AIAgentPool -- "Connects as Client" --> Colyseus

    LiveKit -- "Nearby Audio Streams" --> AIAgentPool
    AIAgentPool -- "API Request (STT, Summary, Img Prompt)" --> AIService
    AIService -- "API Response (Text, Image URL)" --> AIAgentPool

    AIAgentPool -- "Update Public State (e.g., Shared Image URL)" --> Colyseus
    AIAgentPool -- "Send Private Message (e.g., Summary Text)" --> Colyseus
```

## 技術スタック

主要な技術スタックは以下の通りです。詳細については `docs/technology-stack.ja.md` を参照してください。

- **クライアント (Frontend):** Next.js, TypeScript, React Three Fiber, Colyseus.js, Radix UI, Tailwind CSS
- **サーバー (Backend):** Colyseus, LiveKit, Supabase

## ビルドと実行

### 0. Supabase ローカル環境の起動

```bash
cd supabase
cp .env.example .env    # 初回のみ。GitHub OAuth のクレデンシャルを設定
supabase start
```

`supabase start` 実行後、ターミナルに表示される `anon key` を `client/.env.local` の `NEXT_PUBLIC_SUPABASE_ANON_KEY` に設定してください。
同時に `API URL` が `http://127.0.0.1:54321` なのか `http://localhost:54321` なのかを確認し、その値に合わせて `SUPABASE_AUTH_EXTERNAL_GITHUB_REDIRECT_URI` を更新します。

GitHub OAuth アプリは以下の設定で作成し、取得したクレデンシャルと合わせて `supabase/.env` に保存します。

- **Homepage URL:** `http://127.0.0.1:3000`
- **Authorization callback URL:** `http://127.0.0.1:54321/auth/v1/callback` (または Supabase CLI の `API URL` に合わせたホスト名)

`supabase/.env` に設定する値の例：

```
SUPABASE_AUTH_EXTERNAL_GITHUB_CLIENT_ID=gho_xxxxxxxxx
SUPABASE_AUTH_EXTERNAL_GITHUB_SECRET=ghs_xxxxxxxxx
SUPABASE_AUTH_EXTERNAL_GITHUB_REDIRECT_URI=http://127.0.0.1:54321/auth/v1/callback
```

### 1. Colyseus サーバーの起動

```bash
cd server
npm install
npm start
```

### 2. Next.js クライアントの起動

```bash
cd client
yarn install
yarn dev
```

クライアントは [http://localhost:3000](http://localhost:3000) で利用可能になります。

## ディレクトリ構成

- **`client/`:** 3D ワールドをレンダリングし、ユーザーインタラクションを処理する Next.js フロントエンドアプリケーション。
- **`server/`:** プレイヤーの位置や回転など、メタバースのリアルタイムな状態を管理する Colyseus サーバー。
- **`docs/`:** 仕様書、アーキテクチャ図、開発計画などのプロジェクトドキュメント。
