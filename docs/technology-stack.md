# Technology Stack

This document outlines the technology stack used in the LLM Metaverse project, based on the system architecture and client-side documentation.

## Frontend (Client)

The client is a Next.js application responsible for rendering the 3D world and handling user interactions.

- **Framework:** [Next.js](https://nextjs.org/)
- **Language:** [TypeScript](https://www.typescriptlang.org/)
- **3D Rendering:**
    - [@react-three/fiber](https://docs.pmnd.rs/react-three-fiber/getting-started/introduction)
    - [@react-three/drei](https://github.com/pmndrs/drei)
- **Multiplayer:** [Colyseus.js](https://docs.colyseus.io/colyseus/getting-started/javascript-client/)
- **UI:**
    - [Radix UI](https://www.radix-ui.com/)
    - [Tailwind CSS](https://tailwindcss.com/)
- **XR:** [@react-three/xr](https://docs.pmnd.rs/react-xr/introduction)

## Backend Services

The backend is composed of several microservices to handle different aspects of the application.

- **Multiplayer Server:** [Colyseus](https://www.colyseus.io/) - Manages real-time state and communication between clients.
- **Media Server:** [LiveKit](https://livekit.io/) - Handles real-time audio and video streaming (SFU).
- **Authentication & Database:** [Supabase](https://supabase.com/) - Provides authentication and database services.
- **AI Service:**
    - **Framework:** [FastAPI](https://fastapi.tiangolo.com/)
    - **Speech-to-Text:** [Whisper](https://openai.com/research/whisper)
    - **Language Model:** A Large Language Model (LLM) for various AI-powered features.
    - **Image Generation:** An image generation model to create visuals from text prompts.
