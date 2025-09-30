# Requirements Definition: LLMeta

## 1. Overview

This document defines the requirements for the WebXR metaverse experience project, "LLMeta". LLMeta is a lightweight web application that allows users to interact in a shared 3D space in real-time and receive communication support from AI.

## 2. Project Objectives

- **Real-time Communication:** Provide an environment where up to 10 users can have smooth voice conversations in a 3D space with spatial audio.
- **AI-powered Support:** Provide each user with a personalized AI agent to enrich communication with features like conversation summarization, explanations, and automatic generation of related images.
- **Cross-platform:** Realize an experience that is seamlessly accessible from desktop browsers and XR devices.

## 3. Functional Requirements

### 3.1. User Management Features

- **Authentication:** Users can create an account and log in. Supabase will be used for the authentication infrastructure.
- **Profile:** Users can set their display name and avatar to be used within the metaverse.

### 3.2. Metaverse Core Features

- **Rooms:** Users can create a session (room) or join an existing one.
- **3D Space:** Users can move freely as avatars within a 3D rendered space.
- **Real-time Synchronization:** The position and movement of user avatars are synchronized in real-time for all users in the room via the Colyseus server.
- **Spatial Audio:** Implement spatial audio where the way voices are heard changes according to the distance between users. LiveKit SFU will be used for media streaming.

### 3.3. AI Supporter Features

- **Personal AI Agent:** Each user is assigned a one-to-one AI agent.
- **Real-time Speech Recognition:** User speech is converted to text in real-time using the Whisper model.
- **Private Support:** The AI agent provides conversation summaries and term explanations as text, visible only to the individual user.
- **Public Support (Image Generation):** The AI agent automatically generates images based on the conversation context and shares them in a way that is visible to all users in the room.

## 4. Non-functional Requirements

### 4.1. Performance

- **Low Latency:** Minimize the delay of voice and state synchronization between users to not hinder natural communication.
- **Rendering:** Optimize 3D assets and rendering processes to maintain a stable frame rate even on XR devices.

### 4.2. Scalability

- The system must have a scalable architecture to accommodate an increase in the number of users and rooms. The AI agents will have a scalable design, operating independently for each user.

### 4.3. Security

- Communication between users must be encrypted.
- Joining a room requires authentication with a JWT (JSON Web Token) issued by Supabase.

### 4.4. Development & Operations

- **Technology Stack:**
    - **Frontend:** Next.js, TypeScript, React Three Fiber, Tailwind CSS
    - **Backend:**
        - **Multiplayer:** Colyseus
        - **Media:** LiveKit
        - **Auth/DB:** Supabase
        - **AI Service:** FastAPI, Whisper, LLM, Image Generation Model
- **Maintainability:** The backend is divided into microservices based on responsibility, allowing each service to be developed and deployed independently.

## 5. System Configuration

The system consists of three layers: frontend, backend services, and AI agents. Details are as described in the Mermaid diagram in `system-architecture.md`. User authentication, state synchronization, media streaming, and AI processing are handled by independent services, achieving a loosely coupled collaboration.
