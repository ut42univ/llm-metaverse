# System Architecture Diagram

This document provides a visual representation of the current and considered system architecture for the LLM Metaverse project. The diagram is created using Mermaid and reflects the ongoing design discussions.

**Note:** This architecture is flexible and subject to change as the project evolves. Dotted lines and components represent future considerations or alternative options.

```mermaid
graph LR
    UserBrowser["🌐 User's Browser<br/>(Desktop/XR)"] --> Client["<b>Client</b><br/>(Next.js, React, R3F)"]

    Client -- "WebSocket" --> Colyseus["<b>Multiplayer Server</b><br/>(Colyseus)<br/>State Sync"]
    Client -- "WebSocket" --> LiveKit["<b>Media Server</b><br/>(LiveKit SFU)<br/>Spatial Audio"]
    Client -- "HTTP/REST" --> Supabase["<b>Auth & DB</b><br/>(Supabase)"]

    AIAgent["🤖 <b>AI Agent Bot</b><br/>(LiveKit Agents)"] -- "WebSocket" --> LiveKit
    AIAgent -- "WebSocket" --> Colyseus

    LiveKit -- "Audio Stream" --> TranslationAPI["<b>Translation/STT API</b><br/>(FastAPI, Whisper)"]
```
