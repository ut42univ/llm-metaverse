# 技術スタック

このドキュメントは、システムのアーキテクチャとクライアントサイドのドキュメントに基づき、LLM Metaverse プロジェクトで使用される技術スタックの概要を説明します。

## フロントエンド (クライアント)

クライアントは Next.js アプリケーションで、3D ワールドのレンダリングとユーザーインタラクションを担当します。

- **フレームワーク:** [Next.js](https://nextjs.org/)
- **言語:** [TypeScript](https://www.typescriptlang.org/)
- **3D レンダリング:**
    - [@react-three/fiber](https://docs.pmnd.rs/react-three-fiber/getting-started/introduction)
    - [@react-three/drei](https://github.com/pmndrs/drei)
- **マルチプレイヤー:** [Colyseus.js](https://docs.colyseus.io/colyseus/getting-started/javascript-client/)
- **UI:**
    - [Radix UI](https://www.radix-ui.com/)
    - [Tailwind CSS](https://tailwindcss.com/)
- **XR:** [@react-three/xr](https://docs.pmnd.rs/react-xr/introduction)

## バックエンドサービス

バックエンドは、アプリケーションのさまざまな側面を処理するために、いくつかのマイクロサービスで構成されています。

- **マルチプレイヤーサーバー:** [Colyseus](https://www.colyseus.io/) - クライアント間のリアルタイムの状態と通信を管理します。
- **メディアサーバー:** [LiveKit](https://livekit.io/) - リアルタイムの音声およびビデオストリーミング (SFU) を処理します。
- **認証 & データベース:** [Supabase](https://supabase.com/) - 認証およびデータベースサービスを提供します。
- **AI サービス:**
    - **フレームワーク:** [FastAPI](https://fastapi.tiangolo.com/)
    - **音声テキスト変換:** [Whisper](https://openai.com/research/whisper)
    - **言語モデル:** 様々な AI 搭載機能のための大規模言語モデル (LLM)。
    - **画像生成:** テキストプロンプトからビジュアルを作成するための画像生成モデル。
