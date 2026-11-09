# 01 – Introduction to Derive

Derive is a protocol for trading crypto options and perpetual futures. Trades can match very quickly off-chain, while the rules for margin, settlement, and permissions are checked with zero-knowledge proofs and verified on Ethereum.

## Simple explanation

Think of Derive as an exchange that feels fast like a centralized exchange but still settles important parts on Ethereum. You keep control of your funds. The protocol uses math proofs so Ethereum does not have to re-run every calculation.

## What you can trade

According to the official documentation, Derive supports:

- Options (European style)
- Perpetual futures
- Spot (as collateral and for lending)

All trading happens inside **risk universes**. A risk universe is a group of assets that share the same risk boundary. Losses in one universe cannot be socialized to another universe.

## How you interact with it

There are two main ways:

1. **API (HTTP and WebSocket)** – Send signed actions from your wallet or a session key. This is how most trading and market data works.
2. **L1 transactions** – Deposit, withdraw, or set session keys by sending transactions directly to Ethereum contracts. There is also an “escape hatch” for withdrawals if the operator is offline.

Official endpoints (as documented):

| Environment | UI | WebSocket | REST |
|-------------|----------------------------|----------------------------------|--------------------------------|
| Mainnet     | https://app.derive.xyz    | wss://api.derive.xyz/v3/ws      | https://api.derive.xyz/v3     |
| Testnet     | https://testnet.app.derive.xyz | wss://testnet.api.derive.xyz/v3/ws | https://testnet.api.derive.xyz/v3 |

## SDKs

Official SDKs exist for TypeScript (`derive-ts`), Rust (`derive-rs`), and Python (`derive-py`).

## Next

[02 – Understanding Derivatives](02-understanding-derivatives.md)

---

*Sources: [Derive Introduction](https://docs.derive.xyz/getting-started/introduction), [Supported Products](https://docs.derive.xyz/supported-products)*
