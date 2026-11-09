# 03 – Understanding Options

An option gives the buyer the right (but not the obligation) to buy or sell an asset at a fixed price on a certain date.

## Simple explanation

- **Call option** – The right to buy the underlying at the strike price.
- **Put option** – The right to sell the underlying at the strike price.
- **Strike** – The fixed price in the contract.
- **Expiry** – The date the option expires.

If the option finishes in-the-money, it has value. If it finishes out-of-the-money, it expires worthless.

## Options on Derive

Derive offers European-style options. These can only be exercised at expiry (they settle to cash rather than delivering the underlying).

Key points from the official documentation:

- Options are marked to the USD price of the underlying and settled in the cash asset of the universe (USDC at launch).
- Settlement uses a 30-minute TWAP of the base asset price.
- The longest dated option is capped at 400 days.
- You can trade any expiry and strike that has a supporting oracle feed.

## Example (conceptual)

You buy a BTC call with a $100,000 strike that expires in 30 days.  
If BTC is above $100,000 at expiry (after the TWAP), the call has value.  
If BTC is below $100,000, the call expires worthless and you lose the premium you paid.

This is only an illustration. Actual payoff depends on the exact contract specifications and settlement rules.

## Next

[04 – Portfolio Margin](04-portfolio-margin.md)

---

*Sources: [Supported Products](https://docs.derive.xyz/supported-products)*
