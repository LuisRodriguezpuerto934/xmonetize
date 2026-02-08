# 💸 XMONETIZE

**Instant USDC Tipping for X (Twitter) Creators on Solana**

[![Solana](https://img.shields.io/badge/Solana-Devnet-purple)](https://solana.com)
[![Next.js](https://img.shields.io/badge/Next.js-14-black)](https://nextjs.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 🚀 Overview

XMONETIZE enables direct USDC tipping to X (Twitter) creators through the Solana blockchain. Instant, low-cost, borderless payments with no intermediaries.

## ✨ Features

- ✅ **Phantom Wallet** - Secure wallet integration
- ✅ **Tweet Verification** - Validate creator identity
- ✅ **Instant Settlement** - Sub-second confirmations
- ✅ **Microtransactions** - Tip as little as $0.01
- ✅ **Global Reach** - No geographic restrictions

## 📦 Installation

```bash
git clone https://github.com/LuisRodriguezpuerto934/xmonetize.git
cd xmonetize
npm install
```

## 🔧 Configuration

```bash
# Set Solana cluster
export NEXT_PUBLIC_SOLANA_NETWORK=devnet
export NEXT_PUBLIC_SOLANA_RPC=https://api.devnet.solana.com

# Program ID (after deployment)
export NEXT_PUBLIC_PROGRAM_ID=your_program_id
```

## 🚀 Run Locally

```bash
# Start dev server
npm run dev

# Open http://localhost:3000
```

## 📝 Usage

### 1. Connect Wallet
```typescript
import { useWallet } from '@solana/wallet-adapter-react';

const { connect } = useWallet();
await connect(); // Opens Phantom
```

### 2. Send Tip
```typescript
const tip = await program.methods
  .sendTip(tweetUrl, amount)
  .accounts({
    sender: wallet.publicKey,
    creator: creatorAddress,
    escrow: escrowPDA,
  })
  .rpc();
```

### 3. Creator Claims
```typescript
await program.methods
  .claimTip()
  .accounts({
    creator: wallet.publicKey,
    escrow: escrowPDA,
  })
  .rpc();
```

## 🏗️ Architecture

```
User → Phantom Wallet → XMONETIZE UI → Solana Program → USDC Transfer
                          ↓
                    Smart Contract
                    (Escrow System)
                          ↓
                    Creator Claims
```

## 📊 Transaction Flow

| Step | Time | Cost |
|------|------|------|
| Connect | 2s | Free |
| Send Tip | 1s | $0.00025 |
| Confirm | 2s | Free |
| Creator Claims | 1s | $0.00025 |

## 🎯 Use Cases

- **Fan Tipping** - Support favorite creators
- **Content Rewards** - Tip viral posts
- **Global Payments** - No border restrictions
- **Micro-Patronage** - Small recurring tips

## 🔐 Security

- **Escrow System** - Funds held securely
- **PDA Authority** - Program-derived addresses
- **USDC Standard** - SPL token compliance
- **Access Control** - Creator-only claims

## 💰 Economics

| Fee Type | Amount |
|----------|--------|
| Network Fee | ~$0.00025 |
| Platform Fee | 0% |
| Creator Receives | 100% |

## 🛠️ Tech Stack

**Frontend:**
- Next.js 14
- TypeScript
- Tailwind CSS
- @solana/wallet-adapter

**Smart Contract:**
- Anchor 0.32.1
- Rust
- 257 lines

## 📄 Smart Contract

**Location:** `programs/tip_escrow/src/lib.rs`

**Instructions:**
1. `initialize_escrow`
2. `send_tip`
3. `claim_tip`
4. `refund_tip`

**Accounts:**
- Escrow account (PDA)
- Sender token account
- Creator token account
- USDC mint

## 🧪 Testing

```bash
# Smart contract tests
anchor test

# Frontend tests
npm test

# E2E tests
npm run test:e2e
```

## 🚀 Deployment

```bash
# Deploy program
anchor deploy --provider.cluster devnet

# Build frontend
npm run build

# Deploy to Vercel
vercel --prod
```

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md)

## 📄 License

MIT License

## 👤 Author

**Luis Rodriguez Puerto**
- X: [@BrainTease870](https://x.com/BrainTease870)
- GitHub: [@LuisRodriguezpuerto934](https://github.com/LuisRodriguezpuerto934)

## 🏆 Hackathon

Submitted to **Colosseum AI Agent Hackathon 2026**
- Project #82
- Prize Pool: $100,000

---

**Tip the world with USDC** 💸

## Quickstart

```bash
npm install
npm run start  # o revisa scripts en package.json
```

