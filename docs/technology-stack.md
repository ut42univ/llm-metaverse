# Technology Stack

This document outlines the current and considered technology stack for the LLM Metaverse project, reflecting the architecture discussions as of 2025-09-30.

## 1. Core Stack (Currently Implemented)

These are the technologies actively used in the current version of the project.

### Frontend (Client)

- **Framework**: Next.js / React
- **Language**: TypeScript
- **3D Rendering**: `@react-three/fiber`, `@react-three/drei`
- **XR**: `@react-three/xr`
- **Multiplayer Client**: `colyseus.js`
- **UI/Styling**: Tailwind CSS, Radix UI

### Backend

#### Multiplayer Server

- **Framework**: Colyseus
- **Environment**: Node.js
- **Language**: TypeScript
- **Primary Role**: Manages real-time synchronization of player states (position, rotation, etc.).

#### AI Service

- **Framework**: FastAPI
- **Language**: Python
- **Primary Role**: Provides AI-powered services like text translation.
- **Model**: SeamlessM4T v2
- **Future Direction**: This self-hosted service is a candidate for replacement by one of the options listed under "Advanced AI Integration" to reduce maintenance overhead.

## 2. Future Considerations

These are technologies and services being considered for future integration to enhance the platform's capabilities.

### BaaS (Backend as a Service)

- **Service**: Supabase
- **Potential Roles**:
    - **Auth**: User authentication and authorization.
    - **Database**: Persistent storage for user profiles, world data, etc.
    - **Storage**: Storing user-uploaded assets like VRM avatars.

### Real-time Voice & Spatial Audio

- **Service**: LiveKit
- **Potential Role**:
    - Provides real-time, low-latency voice communication using WebRTC.
    - Enables spatial audio, where the volume and panning of a user's voice depend on their position in the 3D world.

### Advanced AI Integration

- **Concept**: Cloud AI APIs & LiveKit Agents
- **Potential Roles**:
    - **Direct Cloud AI APIs**: Instead of self-hosting, use managed services (e.g., Google AI, OpenAI API) for text-based AI features. This would be called from the client or a lightweight backend gateway, replacing the FastAPI service.
    - **AI Agent for LiveKit**: A server-side bot that connects to a LiveKit room. It could handle both voice and text-based AI tasks:
        - **Voice**: Live transcription (Speech-to-Text), real-time voice translation.
        - **Text**: Process text commands or translations, potentially unifying all AI interactions through a single interface.
        - **Interaction**: Power interactive AI characters.
