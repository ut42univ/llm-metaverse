# Project: LLM Metaverse

## Project Overview

This is a monorepo for a lightweight WebXR metaverse experience. It combines a Next.js frontend with a Colyseus multiplayer server and a separate FastAPI-based translation service. The application allows up to 10 users to interact in a shared 3D space with spatial audio, and provides real-time translation and summarization features powered by AI.

### Key Technologies:

- **Client (Next.js):**
  - Framework: Next.js
  - Language: TypeScript
  - 3D Rendering: `@react-three/fiber`, `@react-three/drei`
  - Multiplayer: `colyseus.js`
  - UI: Radix UI, Tailwind CSS
  - XR: `@react-three/xr`
- **Server (Colyseus):**
  - Framework: Colyseus
  - Language: TypeScript
  - Real-time Communication: WebSockets
- **Translation API (FastAPI):**
  - Framework: FastAPI
  - Language: Python
  - AI Model: SeamlessM4T v2

### Architecture:

- **`client/`:** The Next.js frontend application that renders the 3D world and handles user interactions.
- **`server/`:** The Colyseus server that manages the real-time state of the metaverse, including player positions and rotations.
- **`translation-api/`:** A Python-based API that provides text and audio translation services using a pre-trained AI model.
- **`docs/`:** Contains project documentation, including specifications, architecture diagrams, and development plans.

## Building and Running

### 1. Start the Colyseus Server:

```bash
cd server
npm install
npm start
```

### 2. Start the Translation API:

```bash
cd translation-api
uv sync
uv run uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```

### 3. Start the Next.js Client:

```bash
cd client
npm install
npm run dev
```

The client will be available at [http://localhost:3000](http://localhost:3000).

## Development Conventions

- **Styling:** The client uses Tailwind CSS for styling, with some components from Radix UI.
- **State Management:** Component-level state in the client is managed with React hooks. Global state for the multiplayer experience is managed by the Colyseus server.
- **3D:** The 3D scenes are built with `@react-three/fiber` and `@react-three/drei`, following a declarative, component-based approach.
- **Multiplayer:** The connection to the Colyseus server is managed by a custom hook, which automatically connects and disconnects from the room.
- **Translation:** The translation API uses the SeamlessM4T v2 model for both text and audio translation.
