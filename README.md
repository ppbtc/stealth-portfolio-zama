# Stealth Portfolio – Encrypted DeFi Position Manager on Zama

Stealth Portfolio is an **encrypted on-chain portfolio & PnL tracker** built on top of the **Zama Confidential Blockchain Protocol (FHEVM)**.

It lets traders record positions and PnL **on-chain but fully encrypted**, and compute basic risk metrics over encrypted data. Only the owner (and optionally approved viewers) can see the decrypted numbers, while the contract logic runs over ciphertext using FHEVM.

> Built for the [Zama Developer Program](https://www.zama.ai/programs/developer-program).

---

## ✨ Key Features

- **Encrypted on-chain portfolio**
  - Store positions and PnL per wallet using FHE encrypted types (e.g. `euint64`).
  - No raw balances or PnL ever appear on-chain in plaintext.

- **On-chain computation over encrypted data**
  - Use FHEVM operations to update PnL and exposure directly on encrypted values.
  - Demonstrates homomorphic addition / aggregation for confidential finance.

- **Selective disclosure**
  - The owner can decrypt their own stats locally from the encrypted state.
  - (Roadmap) Share only aggregated metrics (ROI bucket, Sharpe-like score) with third parties.

- **Modern dApp stack**
  - Contracts: Hardhat + FHEVM
  - Frontend: React / Next.js + Tailwind + RainbowKit/wagmi
  - Network: FHEVM local node & Sepolia testnet support

---

## 🏗 Architecture

At a high level:

- **Smart contract (`StealthPortfolio.sol`)**
  - Manages encrypted portfolio state per user:
    - Encrypted total PnL
    - Encrypted total notional volume
    - (Optional) Encrypted per-position fields
  - Uses FHEVM types and operators to update state on-chain without ever decrypting.

- **Frontend (Next.js)**
  - Connects via EVM wallet (MetaMask etc.)
  - Uses the FHEVM SDK to:
    - Encrypt position/PnL updates client-side.
    - Send encrypted payloads to the contract.
    - Request & decrypt encrypted summaries for the connected wallet.

- **Relayer / RPC**
  - Uses Zama’s FHEVM-ready node (local Hardhat + FHEVM plugin).
  - Optional: Sepolia testnet deployment.

---

## 📁 Project Structure

This repository is designed to follow Zama’s recommended layout and builds on top of their FHEVM templates.

```bash
stealth-portfolio-zama/
├── packages/
│   ├── fhevm-hardhat-template/   # Contracts & deployment (extended with StealthPortfolio.sol)
│   ├── fhevm-sdk/                # FHEVM SDK helpers for encryption/decryption
│   └── nextjs/                   # React / Next.js frontend (Stealth Portfolio UI)
└── scripts/                      # Helper scripts (deployment, seeding, etc.)
