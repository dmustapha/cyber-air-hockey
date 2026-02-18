# Cyber Air Hockey — Multiplayer Web3 Esports Game

Real-time air hockey with ELO rankings, on-chain match records, and a full competitive layer.

[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue)](https://www.typescriptlang.org/)
[![Next.js](https://img.shields.io/badge/Next.js-16-black)](https://nextjs.org/)
[![WebSocket](https://img.shields.io/badge/WebSocket-real--time-green)](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

![Cyber Air Hockey Home](docs/images/home.png)

## Live Demo

**[cyber-air-hockey.vercel.app](https://cyber-air-hockey.vercel.app)**

---

## What Is Cyber Air Hockey?

Browser-based air hockey with a full competitive structure built on top. ELO rating system, 6 rank tiers, seasonal leaderboards, 25+ achievements, and match results recorded on-chain via MetaMask. Play against the AI offline or find opponents over WebSocket.

---

## Screenshots

| Game Modes | Global Rankings |
|-----------|----------------|
| ![Game](docs/images/game.png) | ![Leaderboard](docs/images/leaderboard.png) |

---

## Features

- **Real-time multiplayer**: WebSocket physics engine (Matter.js) with low-latency game state sync
- **ELO rating system**: 6 rank tiers from Bronze to Master with skill-based matchmaking
- **On-chain match records**: Match results recorded via MetaMask wallet
- **VS AI mode**: Offline play against computer opponents
- **Season system**: Live competitive seasons with seasonal leaderboards
- **Achievements**: 25+ unlockable titles and badges
- **Player profiles**: Stats, match history, win rates, and rank progression

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

## Playing the Game

---

### Play vs AI (no setup needed)

The fastest way to try the game. No wallet, no account required.

1. Go to [cyber-air-hockey.vercel.app](https://cyber-air-hockey.vercel.app)
2. Click **Play vs AI**
3. Use your mouse or trackpad to control the paddle
4. First to 7 goals wins

The AI runs locally in your browser using Matter.js physics. No server connection needed.

---

### Play multiplayer (real opponents)

1. Go to the game and click **Play vs Player**
2. The matchmaking server pairs you with another player waiting in the queue
3. Once matched, the game starts automatically
4. Game physics are synced in real time over WebSocket
5. Match result is submitted to the leaderboard when the game ends

To test multiplayer without a second player: open two browser tabs, click **Play vs Player** in each. The matchmaking server will pair them together.

---

### On-chain match records

Connect MetaMask to have your match results recorded on-chain.

1. Click **Connect Wallet** and approve the MetaMask connection
2. Play a ranked match
3. When the match ends, sign the result with MetaMask
4. The match record is written to the smart contract with your wallet address, opponent, score, and timestamp

This creates a verifiable on-chain history of your competitive record that nobody can alter.

---

### Check the leaderboard

Go to **Leaderboard** to see global ELO rankings, seasonal standings, and top players by win rate. Your profile page shows your full match history, achievements unlocked, and rank progression over time.

---

### Rank system

| Rank | ELO Range |
|------|-----------|
| Bronze | 0 - 999 |
| Silver | 1000 - 1199 |
| Gold | 1200 - 1399 |
| Platinum | 1400 - 1599 |
| Diamond | 1600 - 1799 |
| Master | 1800+ |

New players start at 1000 ELO. Winning against higher-ranked opponents gains more ELO. Losing to lower-ranked opponents loses more.

---

## How It Works

```
Player connects
      |
      v
Choose mode: VS AI (offline) or VS Player (online)
      |
      +-- VS AI: physics runs client-side (Matter.js)
      |
      +-- VS Player:
            |
            v
         WebSocket server matches opponents
            |
            v
         Real-time game state sync
            |
            v
         Match result signed and recorded on-chain
```

---

## Running Locally

```bash
git clone https://github.com/dmustapha/cyber-air-hockey.git
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
│   │       ├── game/        # Game canvas and physics
│   │       ├── leaderboard/ # Global ELO rankings
│   │       ├── profile/     # Player stats
│   │       └── settings/    # Account settings
│   └── components/cyber/    # UI components
├── server/                  # Node.js WebSocket server
│   └── src/
│       ├── roomManager.ts   # Matchmaking and game rooms
│       └── index.ts         # WS server entry
└── contracts/               # On-chain match verification
```

---

## License

MIT
