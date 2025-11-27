# stealth-portfolio-zama
Stealth Portfolio is a confidential DeFi position manager built on top of the Zama Confidential Blockchain Protocol.
It allows on-chain traders to track their real positions, PnL and risk metrics while keeping all sensitive data fully encrypted with FHE.

With Stealth Portfolio, a trader can:

connect a wallet and register positions (spot, perp, options, LP tokens etc.) into an encrypted state,

compute PnL, exposure, and risk indicators over fully homomorphically encrypted data,

selectively reveal high-level, aggregated stats (e.g. 30-day ROI range, Sharpe ratio bucket) without exposing raw positions or wallet balances.

Why Zama / FHE?
Today, on-chain traders face a trade-off between transparency and alpha leakage. Public dashboards leak strategies, while off-chain spreadsheets are non-verifiable. By using Zama’s FHE-powered confidential smart contracts, Stealth Portfolio keeps all user data encrypted at rest and in computation, while still allowing verifiable proofs that “a trader meets certain criteria” (e.g. track record, risk limits) without revealing the underlying details.

Tech outline

Smart contracts: Zama Confidential Blockchain Protocol / FHEVM used to store and update encrypted position states and compute encrypted PnL & risk metrics.

Frontend: React/Next.js dashboard for position input, visualization of decrypted summaries, and optional data sharing controls.

Integrations (stretch goals): pull prices / positions from existing DeFi protocols or chain indexers, then push into the encrypted state on Zama.

The goal of the project is to showcase a practical trading-oriented use case for Zama’s FHE stack and provide a reusable pattern for other privacy-preserving DeFi analytics tools.
