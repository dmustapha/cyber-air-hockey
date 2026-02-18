# Cyber Air Hockey — Multiplayer Web3 Esports Game

> Real-time air hockey with ELO rankings, blockchain match records, and a full esports meta.

[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue)](https://www.typescriptlang.org/)
[![Next.js](https://img.shields.io/badge/Next.js-16-black)](https://nextjs.org/)
[![WebSocket](https://img.shields.io/badge/WebSocket-real--time-green)](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

![Cyber Air Hockey Home](docs/images/home.png)

## Live Demo

**[→ cyber-air-hockey.vercel.app](https://cyber-air-hockey.vercel.app)**

---

## What Is Cyber Air Hockey?

A browser-based multiplayer air hockey game with a full competitive esports layer — ELO rating system, 6 rank tiers, seasonal leaderboards, 25+ achievements, and on-chain match verification via MetaMask. Play against AI offline or challenge real opponents over WebSocket with results recorded on-chain.

---

## Screenshots

| Game Modes | Global Rankings |
|-----------|----------------|
| ![Game](docs/images/game.png) | ![Leaderboard](docs/images/leaderboard.png) |

---

## Features

- **Real-time Multiplayer** — WebSocket-powered physics engine (Matter.js) for sub-50ms gameplay
- **ELO Rating System** — 6 rank tiers from Bronze to Master with skill-based matchmaking
- **Blockchain Match Records** — On-chain verification via MetaMask wallet
- **VS AI Mode** — Offline practice against computer opponents
- **Season System** — Live competitive seasons with seasonal leaderboards
- **25+ Achievements** — Unlock titles and badges as you play
- **Player Profiles** — Stats, match history, win rates, and rank progression

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Next.js 16, TypeScript, Tailwind CSS |
| Game Physics | Matter.js |
| Multiplayer | WebSocket (Node.js server) |
| Blockchain | MetaMask, Ethereum/EVM smart contracts |
| State | Zustand |
| Deployment | Vercel (frontend), Railway (WebSocket server) |

---

## How It Works

```
Player connects
      │
      ▼
Choose mode: VS AI (offline) or VS Player (online)
      │
      ├── VS AI: Physics runs client-side (Matter.js)
      │
      └── VS Player:
            │
            ▼
         WebSocket server matches opponents
            │
            ▼
         Real-time game state sync (<50ms)
            │
            ▼
         Match result signed + recorded on-chain
```

---

## Running Locally

```bash
git clone https://github.com/dmz4pf/cyber-air-hockey.git
cd cyber-air-hockey
npm install
npm run dev
```

For multiplayer (optional):
```bash
cd server && npm install && npm run dev
```

---

## Project Structure

```
cyber-air-hockey/
├── src/
│   ├── app/
│   │   └── (cyber)/
│   │       ├── game/        # Game canvas + physics
│   │       ├── leaderboard/ # Global ELO rankings
│   │       ├── profile/     # Player stats
│   │       └── settings/    # Account settings
│   └── components/cyber/    # UI components
├── server/                  # Node.js WebSocket server
│   └── src/
│       ├── roomManager.ts   # Matchmaking + game rooms
│       └── index.ts         # WS server entry
└── contracts/               # On-chain match verification
```

---

## License

MIT
