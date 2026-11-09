# 01 – Introduction to Derive

Derive is a protocol for trading crypto options and perpetual futures. Trades can match very quickly off-chain, while the rules for margin, settlement, and permissions are checked with zero-knowledge proofs and verified on Ethereum.

## Simple explanation

Think of Derive as an exchange that feels fast like a centralized exchange but still settles important parts on Ethereum. Matching happens off-chain for speed. The protocol then proves that margin rules and settlement followed the on-chain rules, and Ethereum verifies those proofs.

## Where your funds sit

Funds deposited to Derive are held in protocol smart contracts on Ethereum. The main settlement contract (VAPP) anchors the state root and verifies the zero-knowledge proofs. Payouts for withdrawals come from a spot vault through the withdrawal outbox contract.

You do not hold the tokens in your own wallet while they are inside the exchange. Instead, the protocol contracts hold them and release them only when a valid withdrawal is proven.

There are two ways to withdraw:

1. **Normal withdrawals** – You request a withdrawal through the API. Once the batch containing that withdrawal is proven on Ethereum, the funds can be claimed (subject to rate limits).
2. **Escape hatch** – If the operator or sequencer goes offline, you can still withdraw by interacting directly with the on-chain contracts. The withdrawal outbox supports this non-custodial exit path. State diffs are also posted to Celestia so others can help process withdrawals if needed.

See the official contracts page for addresses and the introduction for the high-level flow: [Contracts](https://docs.derive.xyz/getting-started/contracts) and [Introduction](https://docs.derive.xyz/getting-started/introduction).

## What you can trade

According to the official documentation, Derive supports:

- Options (European style)
- Perpetual futures
- Spot (as collateral and for lending)

All trading happens inside **risk universes**. A risk universe is a group of assets that share the same risk boundary. Losses in one universe cannot be socialized to another universe. See [Supported Products](https://docs.derive.xyz/supported-products) and [Managers & Risk Universes](https://docs.derive.xyz/trading/managers-and-risk-universes).

## How you interact with it

There are two main ways:

1. **API (HTTP and WebSocket)** – Send signed actions from your wallet or a session key. This is how most trading and market data works.
2. **L1 transactions** – Deposit, withdraw, or set session keys by sending transactions directly to Ethereum contracts. This path also supports the escape hatch for withdrawals if the operator is offline.

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

*Sources: [Derive Introduction](https://docs.derive.xyz/getting-started/introduction), [Contracts](https://docs.derive.xyz/getting-started/contracts), [Supported Products](https://docs.derive.xyz/supported-products)*
