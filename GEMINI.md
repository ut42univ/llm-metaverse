# Project: LLM Metaverse

## Project Overview

This project, "LLM Metaverse," is a lightweight WebXR metaverse experience that allows users to interact in a shared 3D space with AI-powered communication assistance. The project is a monorepo composed of three main parts: a Next.js client, a Colyseus server, and a Python-based translation API.

### Key Technologies:

-   **Client (Frontend):** Next.js, TypeScript, React Three Fiber, Colyseus.js, Radix UI, Tailwind CSS
-   **Server (Backend):** Colyseus, LiveKit, Supabase
-   **Translation & AI API:** FastAPI, SeamlessM4T v2

### Architecture:

The system is composed of a frontend, backend services, and AI agents.

-   **`client/`**: A Next.js application that renders the 3D world and handles user interactions.
-   **`server/`**: A Colyseus server that manages the real-time state of the metaverse, such as player positions and rotations.
-   **`translation-api/`**: A Python-based API that provides text and speech translation services using a pretrained AI model.
-   **`docs/`**: Project documentation, including specifications, architecture diagrams, and development plans.

## Building and Running

### 1. Colyseus Server

```bash
cd server
npm install
npm start
```

### 2. Translation API

```bash
cd translation-api
uv sync
uv run uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```

### 3. Next.js Client

```bash
cd client
npm install
npm run dev
```

The client will be available at [http://localhost:3000](http://localhost:3000).

## Development Conventions

-   **Styling:** The project uses Tailwind CSS for styling, with some components from Radix UI.
-   **State Management:** Component-level state is managed with React hooks. Global state for the multiplayer experience is managed by Colyseus.
-   **3D:** The 3D scenes are built with `@react-three/fiber` and `@react-three/drei`, following a declarative, component-based approach.
-   **Multiplayer:** The connection to the Colyseus server is managed by the `useColyseusLifecycle` hook, which automatically connects and disconnects from the room.
-   **Translation API:** The translation API uses FastAPI and the SeamlessM4T v2 model for translation and speech synthesis.
