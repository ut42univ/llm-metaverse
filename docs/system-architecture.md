# System Architecture Diagram

This document provides a visual representation of the current and considered system architecture for the LLM Metaverse project. The diagram is created using Mermaid and reflects the ongoing design discussions.

**Note:** This architecture is flexible and subject to change as the project evolves. Dotted lines and components represent future considerations or alternative options.

```mermaid
graph TD
    UserBrowser["🌐 User's Browser (Desktop/XR)"]
    Client["<b>Client Application</b><br/>Next.js / React"]
    ColyseusServer["<b>Colyseus Server</b><br/>(State Sync)"]
    SelfHostedAI["<b>Self-hosted AI</b><br/>(FastAPI)<br/><i>Option 1</i>"]
    Supabase["<b>Supabase</b><br/>(Auth, DB)"]
    LiveKit["<b>LiveKit SFU</b><br/>(Audio, AI Host)"]
    AIAgent["<b>AI Agent</b><br/>(Voice, Text)<br/><i>Option 2</i>"]
    CloudAI["<b>Cloud AI APIs</b><br/>(Google, etc.)<br/><i>Option 3</i>"]

    %% --- Connections ---
    UserBrowser --> Client
    Client --> ColyseusServer

    Client --> SelfHostedAI
    Client -.-> LiveKit
    LiveKit --> AIAgent
    Client -.-> CloudAI

    Client -.-> Supabase
    Client -.-> LiveKit
```
