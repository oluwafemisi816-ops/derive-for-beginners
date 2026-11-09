# 04 – Portfolio Margin

Margin is the collateral you must keep in your account so the protocol can cover potential losses.

## Simple explanation

There are two margin models on Derive:

- **Standard Margin (SM)** – Positions are mostly margined separately. Spreads in the same expiry can get some offsets.
- **Portfolio Margin (PM / PM2)** – The whole portfolio is stressed under many price and volatility scenarios. The worst outcome drives the margin requirement. This is usually more capital-efficient for hedged or complex books.

You choose the model by picking a manager when you create a subaccount. Each risk universe has at most one Standard and one Portfolio manager.

## How Portfolio Margin works (high level)

The protocol looks at your options, perpetuals, and certain collateral under a grid of scenarios:

- Regular scenarios (spot and volatility shocks)
- Tail scenarios (larger moves, with dampening)
- Skew scenarios (changes in the shape of the volatility surface)
- Forward basis scenarios

It takes the worst loss from these scenarios, adds contingency margin for risks the scenarios do not fully capture, and compares the result to your mark-to-market value.

If maintenance margin falls below zero, the account can be liquidated.

Important detail from the documentation: in V3, portfolio margin is cross-currency inside a universe (for example BTC and ETH together in the Prime universe), but losses in one currency do not offset gains in another. Netting stops at the universe boundary.

## Why it matters

Portfolio margin can require less collateral for portfolios that hedge each other. It can require more collateral for concentrated or naked short option positions. The exact numbers depend on current parameters and live prices.

Always check the official margin documentation and the live `public/get_margin` or private margin endpoints for actual calculations.

## Next

[05 – Derive Architecture](05-derive-architecture.md)

---

*Sources: [Portfolio Margin](https://docs.derive.xyz/portfolio-margin), [Managers & Risk Universes](https://docs.derive.xyz/trading/managers-and-risk-universes), [SM vs PM Comparison](https://docs.derive.xyz/sm-v-pm-comparison)*
