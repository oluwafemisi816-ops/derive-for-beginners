# 02 – Understanding Derivatives

A derivative is a contract whose value comes from something else (the underlying).

## Simple explanation

If you buy Bitcoin, you own the coin.  
If you trade a derivative on Bitcoin, you are trading a contract that depends on Bitcoin’s price. You do not necessarily own the Bitcoin itself.

Common reasons people use derivatives:

- **Hedging** – Reduce risk on an existing position.
- **Speculation** – Express a view on price direction or volatility with less capital.
- **Leverage** – Control a larger position than the cash you post as collateral.

## Perpetual futures

A perpetual future (or “perp”) is a futures contract with no expiry date. On Derive, funding payments are exchanged between long and short positions so the perp price stays close to the spot price.

Derive marks perps using the spot price plus a 30-minute time-weighted average of the difference between the perp and spot. Perps are settled continuously when positions change.

## Spot and collateral

You can also hold or borrow certain base assets (for example ETH or BTC tokens) as collateral. Which assets are accepted depends on the risk universe you are in.

## Risk universes

Every instrument and every collateral token belongs to exactly one risk universe. Margin nets only inside that universe. This design contains risk so a problem in one set of assets does not automatically affect every other asset on the exchange.

## Next

[03 – Understanding Options](03-understanding-options.md)

---

*Sources: [Supported Products](https://docs.derive.xyz/supported-products), [Managers & Risk Universes](https://docs.derive.xyz/trading/managers-and-risk-universes)*
