# Project: LLM Metaverse

## Project Overview

This project, "LLM Metaverse," is a lightweight WebXR metaverse experience that allows users to interact in a shared 3D space with AI-powered communication assistance. The project is a monorepo composed of two main parts: a Next.js client and a Colyseus server.

### Key Technologies:

-   **Client (Frontend):** Next.js, TypeScript, React Three Fiber, Colyseus.js, Radix UI, Tailwind CSS
-   **Server (Backend):** Colyseus, LiveKit, Supabase

### Architecture:

The system is composed of a frontend and backend services.

-   **`client/`**: A Next.js application that renders the 3D world and handles user interactions.
-   **`server/`**: A Colyseus server that manages the real-time state of the metaverse, such as player positions and rotations.
-   **`docs/`**: Project documentation, including specifications, architecture diagrams, and development plans.

## Building and Running

### 1. Colyseus Server

```bash
cd server
npm install
npm start
```

### 2. Next.js Client

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
