# Gold Digger Airdrop Tool

A modular airdrop generator and Merkle distributor for the G.O.L.D. and DIGR token ecosystem, built for Solana. Designed for community distribution, staking rewards, and governance-based claim flows.

---

## 📦 Overview

This repo allows projects within the **Gold Digger** ecosystem to:

- Generate Merkle roots for airdrop snapshots
- Verify wallet eligibility off-chain
- Claim tokens using Solana smart contracts (Anchor-based)
- Distribute rewards via **Solana Pay**, **Blinks**, and **QR codes**

Supports 1:1 G.O.L.D. → DIGR allocations, agent-based voting rewards, and integration with Dialect governance infrastructure.

---

## 📁 Repo Structure

```bash
packages/
├── gold-airdrop/
│   ├── scripts/
│   │   └── generate-merkle.ts
│   ├── data/
│   │   └── gold_balances.json
│   ├── output/
│   │   ├── merkle.json
│   │   └── root.txt
│   ├── program/
│   │   └── Anchor claim contract (see below)
│   ├── ui/
│   │   └── claim-qr/ (Solana Pay Blink UI)
│   └── README.md
````

---

## ⚙️ Setup

### 1. Install dependencies

```bash
pnpm install
```

### 2. Prepare balance data

In `data/gold_balances.json`, include a snapshot of balances:

```json
{
  "wallet1...": "100",
  "wallet2...": "200",
  ...
}
```

### 3. Generate Merkle Tree

```bash
pnpm tsx scripts/generate-merkle.ts
```

This outputs:

* `output/merkle.json`: full tree
* `output/root.txt`: Merkle root (for smart contract deployment)

---

## 🔐 Anchor Claim Program (Optional)

Use the Merkle root to allow on-chain claim validation via Anchor.

* Deploy the included program under `gold-airdrop/program/`
* Set Merkle root in the contract state
* Users can claim tokens using their proof

> Want a ready-to-deploy `idl.json`, `lib.rs`, and deploy script? Ask me next!

---

## 🔗 Solana Pay QR UI

The `claim-qr` UI lets users scan a **Blink QR** to:

* Auto-generate their claim proof
* Sign a transaction to claim G.O.L.D.
* Optional: stake or redirect to governance

Uses:

* [Solana Pay](https://solanapay.com/)
* [Dialect Blinks](https://docs.dialect.to/blinks)

---

## 🗳️ Governance Features (DIGR)

* 1:1 allocation from G.O.L.D. → DIGR
* Blink-based voting UI for top holders or stakers
* Jailbird AI agent voting (coming soon)

---

## 💡 Future Ideas

* Multi-phase claim rounds
* zk-proof integration for privacy-preserving drops
* Snapshot fetch from Helius or Dialect indexers
* Unity plugin for in-game claim triggers

---

## 🧠 Related Tools

| Tool            | Description                                        |
| --------------- | -------------------------------------------------- |
| `@gold/airdrop` | CLI tool to verify proofs                          |
| `@gold/sdk`     | JS SDK to fetch Merkle root, build claim txn       |
| `@gold/blink`   | Blink adapters for Solana Pay, Dialect, governance |

---

## 📜 License

MIT © Gold Digger
