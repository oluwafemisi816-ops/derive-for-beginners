# 05 – Derive Architecture

Derive V3 (launched around October 2026) moved from its own chain to a zero-knowledge application that settles on Ethereum.

## Simple explanation

Matching happens off-chain so it can be fast. The rules for margin, settlement, and permissions run inside a zero-knowledge virtual machine. Ethereum only checks the proof that those rules were followed.

## Key pieces

- **Matching engine** – Off-chain, low-latency order matching and RFQ.
- **Sequencer** – Orders operations into batches and submits proofs.
- **SP1 Hypercube zkVM** – Protocol logic is compiled to RISC-V and proven off-chain.
- **Ethereum L1 contracts** – Verify the PLONK proofs, hold custody, and handle deposits and withdrawals.
- **Celestia** – Data availability layer. Every batch’s state diff is posted to Celestia so others can rebuild state and help process withdrawals if the sequencer goes offline.

Official description from the documentation:

> Margining, settlement and permissioning are defined in the protocol, compiled into a RISC-V binary, and proven off-chain with the SP1 Hypercube zkVM. Protocol operations are batched and submitted to Ethereum L1, where each batch is verified with a PLONK SNARK proof.

The V3 launch proposal states that verification on Ethereum costs a flat ~400–500k gas whether the batch contains one trade or a million. This is a design claim from the proposal; always check live transaction data for current costs. See [DIP: Launch Derive V3](https://forums.derive.xyz/t/dip-launch-derive-v3/322) and the [Introduction](https://docs.derive.xyz/getting-started/introduction).

## Contracts

The main contracts (addresses can change — always confirm on the official page) include:

- **Action Manager** – Handles deposits and some L1 actions, including the escape hatch path.
- **VAPP** – Anchors the protocol state root and verifies the zero-knowledge proofs. Described as the root of custody and settlement.
- **Withdrawal Outbox** – Claims finalized withdrawals and the escape-hatch exit if the operator is offline. Payouts are pulled from the spot vault.

Full addresses and roles: [Contracts](https://docs.derive.xyz/getting-started/contracts).

## Ownership and security

According to the V3 launch proposal, the protocol is owned by a multisig controlled by a Derive subsidiary, with timelock protections. The design aims for L2Beat Stage 1 classification. These are project statements from the official proposal. Independent audits and ongoing governance should be reviewed separately.

## Next

[06 – Glossary](06-glossary.md)

---

*Sources: [Introduction](https://docs.derive.xyz/getting-started/introduction), [Contracts](https://docs.derive.xyz/getting-started/contracts), [DIP: Launch Derive V3](https://forums.derive.xyz/t/dip-launch-derive-v3/322)*
