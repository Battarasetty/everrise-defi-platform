# EverRise — Multi-Chain DeFi Security Platform

> A live, production Web3 platform building decentralized security and multi-chain solutions for the DeFi space — deployed across 5 blockchains simultaneously.

🔗 **Live Production App:** [everrise.com](https://www.everrise.com) | [Launch dApp](https://v3app.everrise.com/everswap)

📰 **Featured in:** CoinTelegraph · Yahoo Finance · Business Insider · Benzinga · Bitcoin.com

---

## 🔍 Project Overview

EverRise is a blockchain technology company building a full ecosystem of decentralized applications (dApps) providing security and multi-chain solutions for DeFi protocols and individual token holders. The platform operates simultaneously across **5 blockchains** — Ethereum, BNB Chain, Polygon, Avalanche, and Fantom — with a unified token supply and shared smart contract infrastructure.

I worked here as a **Frontend Developer** at EverRise Technologies Pvt Ltd (Aug 2022 – Dec 2023), contributing to two core products: **EverSwap** and the **NFT Staking Vault**. My role covered frontend UI engineering, smart contract integration, backend API development, and multi-wallet connectivity.

---

## ⛓️ Blockchain Networks Worked On

| Network | Role in Ecosystem |
|---|---|
| Ethereum | Primary chain, NFT staking |
| BNB Chain | High-volume swaps, low fees |
| Polygon | Fast transactions |
| Avalanche | Cross-chain bridge target |
| Fantom | Fast finality |

All features I built supported all 5 chains — users switch networks seamlessly within the app.

---

## 🛠️ What I Built

### 1. EverSwap — Multi-Chain Token Swap Interface

EverSwap lets users swap native coins cross-chain and swap tokens across multiple blockchains. Projects list their tokens to collect fees in native coins, reducing sell pressure on their chart.

**Frontend Engineering:**
- Built the complete swap UI — token selection, amount input, real-time price impact display, slippage tolerance settings, and transaction confirmation flow
- Integrated real-time price feeds and liquidity data directly from smart contracts
- Built network switching — detects the user's connected chain and prompts a network change when required
- Built full transaction state management: pending → confirming → confirmed → failed, with clear UI feedback at every stage
- Implemented optimistic UI updates — balances reflect immediately on submission, rolled back if the on-chain transaction fails
- Handled blockchain latency edge cases — users see accurate live status even when confirmation takes 30–60 seconds

**Smart Contract Integration:**
- Integrated EverSwap smart contracts into the frontend using ethers.js
- Called contract read functions (getAmountsOut, allowance checks) for real-time price quotes before swap execution
- Called contract write functions (approve, swap) with proper gas estimation and structured error handling
- Implemented full ERC-20 token approval flows — checked existing allowance before prompting approval, skipped the step when already sufficient

---

### 2. NFT Staking Vault — Cross-Chain Stake Management

The Staking Vault lets users stake RISE tokens and earn yield, secured within on-chain NFT Stakes (ERC-721) that are tradable, bridgeable, and transferable across all 5 chains. A user's staking position is itself a tradable asset.

**Frontend Engineering:**
- Built the staking dashboard — active stakes, earned rewards, APY, lock periods, and per-stake unlock countdowns
- Built the full stake creation flow: amount input → lock period selection → token approval → stake transaction → NFT minted confirmation
- Built vault management UI — view, transfer, bridge, and unstake NFT positions from one place
- Aggregated a user's stake positions across all 5 blockchain networks into a single unified dashboard view
- Built reward claim flows with optimistic updates and transaction receipt polling
- Implemented multi-step confirmation UIs for stake transfer and cross-chain bridge flows

**Smart Contract Integration:**
- Integrated staking contract functions: stake(), unstake(), claimRewards(), transfer()
- Read on-chain ERC-721 NFT metadata to display per-stake details (amount locked, time remaining, rewards accrued)
- Handled cross-chain bridge transactions — initiated bridge on the source chain, polled for completion on the destination chain

---

### 3. Wallet Connectivity — MetaMask & WalletConnect

- Integrated **MetaMask** as the primary wallet provider across all dApps
- Implemented **WalletConnect** for mobile wallet support
- Built a unified wallet connection modal supporting multiple providers
- Managed full wallet state lifecycle: disconnected → connecting → connected, with account change and chain change listeners
- Auto-detected connected network, flagged unsupported chains, and prompted seamless network switch
- Handled edge cases: user rejects connection, switches account mid-session, disconnects externally without page reload

---

### 4. Backend API Contributions

- Wrote REST API endpoints (Node.js / Express) serving token metadata, transaction history, and staking statistics to the frontend
- Built APIs aggregating user stake positions across multiple chains into a single response
- Integrated third-party blockchain data APIs (price feeds, block explorers) on the backend layer
- Defined API contracts with the backend team for real-time data consumed by swap and staking UIs

---

## ⚡ Key Engineering Challenges Solved

### Challenge 1 — Multi-Chain State Without Blocking the UI
A user's balances, stakes, and transaction history exist across 5 separate blockchains. Querying them sequentially would take 5–10 seconds and freeze the dashboard.

**Solution:** Built a parallel async fetching layer using Promise.allSettled — all 5 chains queried simultaneously with independent per-chain loading states. A failed chain shows a retry option without affecting the rest of the UI.

---

### Challenge 2 — Transaction UX Across Slow Blockchains
Blockchain transactions take 15 seconds to several minutes. A UI that just freezes while waiting causes users to retry, resulting in duplicate transactions and lost funds.

**Solution:** Built a full transaction lifecycle UI — pending (spinner + block explorer hash link) → confirming (block confirmation counter) → confirmed (success state) → failed (error message + retry). Users always know the exact status of their transaction.

---

### Challenge 3 — ERC-20 Double-Transaction Approval Confusion
ERC-20 tokens require two sequential MetaMask popups: first approve the contract to spend tokens, then execute the actual transaction. Most users don't understand this and abandon the flow after the first popup.

**Solution:** Built a clear step indicator (Step 1: Approve · Step 2: Confirm) explaining each transaction before the MetaMask popup appears. Pre-checked existing allowance — if already approved for sufficient amount, skipped Step 1 entirely and went straight to execution.

---

### Challenge 4 — Optimistic UI Under Chain Latency
Waiting for on-chain confirmation before updating the UI makes the app feel like a 2010 website despite being a modern React app.

**Solution:** Applied optimistic updates throughout — balances and stake positions update instantly on transaction submission. If the transaction reverts on-chain, the UI rolls back to the previous state with a clear error. This gave the app the feel of a fast web2 product despite blockchain constraints.

---

## 🔧 Tech Stack

| Layer | Technologies |
|---|---|
| Frontend | React.js, TypeScript, JavaScript (ES6+) |
| Web3 / Blockchain | ethers.js, MetaMask SDK, WalletConnect |
| Smart Contracts | ERC-20, ERC-721 (NFT), custom DeFi contracts |
| State Management | Redux Toolkit, Context API |
| Backend APIs | Node.js, Express.js, REST |
| Networks | Ethereum, BNB Chain, Polygon, Avalanche, Fantom |
| Styling | CSS3, Tailwind CSS |

---

## 📰 Press Coverage (During My Tenure)

- **CoinTelegraph** — Leading global crypto industry publication
- **Yahoo Finance** — Mainstream financial media coverage
- **Business Insider** — International business and tech press
- **Benzinga** — Financial news and analysis platform
- **Bitcoin.com** — Major crypto ecosystem media

---

## 🔗 Live Links

- **Main Website:** [everrise.com](https://www.everrise.com)
- **EverSwap (Live):** [v3app.everrise.com/everswap](https://v3app.everrise.com/everswap)
- **NFT Staking Vault (Live):** [v3app.everrise.com/staking](https://v3app.everrise.com/staking)

---

*This is a proprietary production application. This README documents my engineering contributions during my tenure at EverRise Technologies Pvt Ltd (Aug 2022 – Dec 2023). No proprietary source code or internal data is included.*
