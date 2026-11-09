# 05 – Derive Architecture

Derive V3 (launched around October 2026) moved from its own chain to a zero-knowledge application that settles on Ethereum.

## Simple explanation

Matching happens off-chain so it can be fast. The rules for margin, settlement, and permissions run inside a zero-knowledge virtual machine. Ethereum only checks the proof that those rules were followed. This keeps gas costs low and constant regardless of how many trades are in a batch.

## Key pieces

- **Matching engine** – Off-chain, low-latency order matching and RFQ.
- **Sequencer** – Orders operations into batches and submits proofs.
- **SP1 Hypercube zkVM** – Protocol logic is compiled to RISC-V and proven off-chain.
- **Ethereum L1 contracts** – Verify the PLONK proofs, hold custody, and handle deposits and withdrawals.
- **Celestia** – Data availability for state diffs so withdrawals can still be processed if the sequencer goes offline (escape hatch).

Official description from the documentation:

> Margining, settlement and permissioning are defined in the protocol, compiled into a RISC-V binary, and proven off-chain with the SP1 Hypercube zkVM. Protocol operations are batched and submitted to Ethereum L1, where each batch is verified with a PLONK SNARK proof.

## Contracts (mainnet examples from docs)

- Action Manager
- VAPP (zk-vApp settlement contract that anchors the state root and verifies proofs)
- Withdrawal Outbox

Exact addresses are listed in the official contracts page and can change. Always confirm on the live documentation or block explorer.

## Ownership and security

According to the V3 launch proposal, the protocol is owned by a multisig controlled by a Derive subsidiary, with timelock protections. The design aims for L2Beat Stage 1 classification.

These are project statements from the official proposal. Independent audits and ongoing governance should be reviewed separately.

## Next

[06 – Glossary](06-glossary.md)

---

*Sources: [Introduction](https://docs.derive.xyz/getting-started/introduction), [Contracts](https://docs.derive.xyz/getting-started/contracts), [DIP: Launch Derive V3](https://forums.derive.xyz/t/dip-launch-derive-v3/322)*
