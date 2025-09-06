# llm-metaverse (MVP)

軽量 WebXR / Web リアルタイム空間 (研究開発プロトタイプ)。最大 10 名で位置・回転・(VR) 頭部/ハンド同期し、空間音声 + 翻訳/要約 AI を提供。

## コア機能 (MVP)

- 単一ルーム / 最大 10 ユーザー
- 位置 / 回転 / (VR) 頭部・ハンド 20Hz 目標同期 + 補間
- 距離減衰付き空間音声 (LiveKit + WebAudio)
- 翻訳 / 要約 (AI Gateway)
- 再接続 (バックオフ復帰)
- ジェスチャー (Should / 実装進行中)

詳細要件: `docs/spec.md`

## ディレクトリ

| パス      | 説明                                    |
| --------- | --------------------------------------- |
| `client/` | Next.js + Three.js (WebXR) クライアント |
| `server/` | Colyseus 同期サーバ                     |
| `docs/`   | 要件 / アーキ / 計画ドキュメント        |

## クイックスタート

別ターミナルでサーバとクライアントを起動。

1. 依存インストール

```bash
cd server && npm install
cd ../client && npm install
```

2. サーバ起動

```bash
cd server
npm start  # ws://localhost:2567
```

3. クライアント起動

```bash
cd client
npm run dev  # http://localhost:3000
```

4. ブラウザアクセス → ニックネーム入力で参加。

VR (Quest) 対応ブラウザで同 URL → WebXR セッション開始。

## 主な環境変数

| 変数                          | 用途               | 例                   |
| ----------------------------- | ------------------ | -------------------- |
| NEXT_PUBLIC_COLYSEUS_ENDPOINT | クライアント接続先 | ws://localhost:2567  |
| LIVEKIT_URL                   | LiveKit SFU        | wss://localhost:7880 |
| LIVEKIT_API_KEY / SECRET      | トークン署名       | (ローカル)           |
| AI_PROVIDER                   | AI 切替            | mock / openai        |

未設定部分はモック/限定動作。

## 参照ドキュメント

- 要件: `docs/spec.md`
- アーキテクチャ: `docs/architecture.md`
- 開発計画: `docs/development-plan.md`

## ライセンス

TBD (研究用途)。

---
