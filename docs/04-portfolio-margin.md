# 04 – Portfolio Margin

Margin is the collateral you must keep in your account so the protocol can cover potential losses.

## Simple explanation

There are two margin models on Derive:

- **Standard Margin (SM)** – Positions are mostly margined separately. Spreads in the same expiry can get some offsets.
- **Portfolio Margin (PM / PM2)** – The whole portfolio is stressed under many price and volatility scenarios. The worst outcome drives the margin requirement. This is usually more capital-efficient for hedged or complex books.

You choose the model by picking a manager when you create a subaccount. Each risk universe has at most one Standard and one Portfolio manager. See [Managers & Risk Universes](https://docs.derive.xyz/trading/managers-and-risk-universes).

## How Portfolio Margin works (high level)

The protocol looks at your options, perpetuals, and certain collateral under a grid of scenarios:

- Regular scenarios (spot and volatility shocks)
- Tail scenarios (larger moves, with dampening)
- Skew scenarios (changes in the shape of the volatility surface)
- Forward basis scenarios

It takes the worst loss from these scenarios (called maxLoss), adds contingency margin for risks the scenarios do not fully capture, and combines that with the current value of the portfolio.

Official formula (simplified from the docs):

- Portfolio MtM = current mark-to-market value of cash, collateral, options, and perpetual PNL/funding.
- Maintenance Margin = Portfolio MtM + (mm_factor × maxLoss + contingencies) + collateral contingency.

Because maxLoss is a loss (negative number), the second part reduces the total. When the calculated Maintenance Margin falls below zero, the account can be liquidated.

In other words, the account’s equity (Portfolio MtM) is no longer high enough relative to the stressed requirement the protocol calculates. See the full explanation and formulas in the official [Portfolio Margin](https://docs.derive.xyz/portfolio-margin) page.

Important detail from the documentation: in V3, portfolio margin is cross-currency inside a universe (for example BTC and ETH together in the Prime universe), but losses in one currency do not offset gains in another. Netting stops at the universe boundary.

## Simple conceptual example

Imagine a portfolio that currently has $10,000 of equity (Portfolio MtM). Under the worst scenario the protocol tests, the positions could lose $9,500. After applying the maintenance factor and contingencies, the calculated Maintenance Margin ends up at –$200.

Because it is below zero, the account is eligible for liquidation. A liquidator can start an auction that sells part of the portfolio until the remaining account is safely above the buffer margin.

This is only a teaching illustration. Real numbers depend on live prices, the exact scenario grid, and current parameters. Never use this example to decide whether to trade.

## Why it matters

Portfolio margin can require less collateral for portfolios that hedge each other. It can require more collateral for concentrated or naked short option positions. The exact numbers depend on current parameters and live prices.

Always check the official margin documentation and the live `public/get_margin` or private margin endpoints for actual calculations. Liquidation rules are also detailed in the official [Liquidations](https://docs.derive.xyz/liquidations) page.

## Next

[05 – Derive Architecture](05-derive-architecture.md)

---

*Sources: [Portfolio Margin](https://docs.derive.xyz/portfolio-margin), [Managers & Risk Universes](https://docs.derive.xyz/trading/managers-and-risk-universes), [Liquidations](https://docs.derive.xyz/liquidations), [SM vs PM Comparison](https://docs.derive.xyz/sm-v-pm-comparison)*
