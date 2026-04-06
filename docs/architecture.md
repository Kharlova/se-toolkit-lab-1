## Product Choice

- **Product:** Telegram
- **Website:** https://telegram.org
- **Description:** Telegram is a cloud-based instant messaging and voice-over-IP service that allows users to exchange text, voice, video messages, and files. It supports large group chats, channels, and bots, and is known for its focus on speed, security, and cross-platform availability.

## Main components

![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

[Telegram Component Diagram Code](./diagrams/src/telegram/component-diagram.puml)

### Component descriptions

1. **MTProto Gateway (Connection Layer)** — Acts as the entry point for all client connections. It handles the MTProto protocol, manages persistent connections from mobile, desktop, and web clients, and routes requests to the appropriate internal services.

2. **Message Handling Service** — Responsible for processing, validating, and persisting messages (both private and group). It assigns message IDs, updates sequence numbers, and publishes events to the event bus for asynchronous propagation to recipients.

3. **Auth & Session Service** — Manages user authentication, session tokens, and phone number verification. It communicates with external SMS gateways for OTP delivery and validates sessions before allowing access to other services.

4. **Media & File Service** — Handles uploading, storing, and serving media files (photos, videos, documents). It writes file chunks to the Distributed File System and maintains metadata in the database.

5. **Notification/Updates Service** — Subscribes to the event bus for new message events and delivers push notifications to users via external push providers (APNs, FCM) when they are offline.

6. **Channel/Broadcast Service** — Manages channels and broadcast groups, handling message distribution to large subscriber bases. It uses the cache layer for fast access to channel metadata and the event bus for fan-out delivery.

## Data flow

![Telegram Sequence Diagram](./diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

[Telegram Sequence Diagram Code](./diagrams/src/telegram/sequence-diagram.puml)

### Flow: Send Message (with File Ref)

When a user sends a message that includes an already-uploaded media file, the following happens:

1. The **Mobile App** sends an RPC request (`sendMessage`) through the **MTProto Gateway**, referencing the uploaded file by its `file_id`.
2. The **MTProto Gateway** forwards the request to the **Auth Service** to validate the user's session. Once authenticated, the request is passed to the **Message Service**.
3. The **Message Service** persists the message in the **Sharded DB** (both inbox and outbox) and increments the sequence counter in the **State Cache**.
4. The **Message Service** returns an acknowledgment with the assigned message ID back through the gateway to the client, which updates the UI (single tick).

Components involved and data exchanged:
- **Mobile App ↔ MTProto Gateway**: RPC request (`sendMessage`) with peer info and file reference.
- **MTProto Gateway ↔ Auth Service**: Session validation request/response.
- **Message Service ↔ Sharded DB**: Write message data (sender, recipient, content, file reference).
- **Message Service ↔ State Cache**: Increment sequence number (`pts`) for sync consistency.

## Deployment

![Telegram Deployment Diagram](./diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

[Telegram Deployment Diagram Code](./diagrams/src/telegram/deployment-diagram.puml)

Telegram's components are deployed across multiple tiers:

- **Client tier**: Telegram Mobile (iOS/Android), Desktop, and Web apps run on users' personal devices (smartphones, computers, browsers).
- **Edge/Connection tier**: MTProto Gateways and Bot API Frontends are deployed at the network edge in Telegram's primary data center, handling incoming TCP/WebSocket connections.
- **Compute tier**: Core microservices (Auth, Message, Channel, Media, Push) run in containers/pods within a compute cluster, communicating via internal RPC (TL-Schema).
- **Data tier**: A sharded database cluster stores chat/message data, a Distributed File System stores media, and an in-memory Redis cache cluster provides fast access to frequently-read state.
- **External tier**: SMS providers (for OTP) and push notification services (APNs/FCM) are third-party cloud services accessed over HTTP/SMPP.

## Assumptions

1. I assume the MTProto Gateway performs load balancing across multiple instances of internal services using consistent hashing or round-robin to distribute traffic evenly.
2. I assume the Sharded Chat DB uses user-ID or chat-ID-based sharding to partition data across multiple database nodes for horizontal scalability.
3. I assume the Distributed File System implements chunk-level deduplication to reduce storage costs for widely shared media files (e.g., viral videos or forwarded photos).

## Open questions

1. How does Telegram handle end-to-end encryption in "Secret Chats" at the protocol level, and how does the data flow differ from regular cloud chats?
2. What specific mechanisms does the Message Service use to guarantee message delivery ordering and consistency across multiple data centers (e.g., when a user switches between DCs)?
3. How does the Channel/Broadcast Service efficiently fan out messages to millions of subscribers without overwhelming the event bus or database?
