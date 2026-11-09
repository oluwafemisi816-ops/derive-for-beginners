# 06 – Glossary

Short definitions of terms used in this guide. All definitions are simplified for beginners and checked against official Derive documentation.

**Call option**  
The right to buy the underlying at a fixed strike price.

**Collateral**  
Assets posted to back your positions. Can be USDC (cash asset) or supported base assets, depending on the risk universe.

**European option**  
An option that can only be exercised at expiry. Derive options settle to cash.

**Maintenance margin**  
The minimum collateral required to keep a position open. Falling below this can trigger liquidation.

**Initial margin**  
The higher collateral requirement needed to open new positions.

**Perpetual future (perp)**  
A futures contract with no expiry date. Funding payments keep its price close to spot.

**Portfolio Margin (PM / PM2)**  
A margin model that stresses the whole portfolio under many scenarios and uses the worst outcome.

**Risk universe**  
A group of assets that share the same risk boundary. Losses are contained inside the universe.

**Session key**  
A delegated key that can trade on your behalf with limited scopes and an expiry.

**Standard Margin (SM)**  
A simpler margin model that mostly assesses positions separately (with some spread offsets).

**Strike**  
The fixed price at which an option can be exercised.

**TWAP**  
Time-weighted average price. Used for option settlement and perpetual marking.

**Zero-knowledge proof (ZK proof)**  
A cryptographic proof that a computation was done correctly without revealing all the inputs. Derive uses these so Ethereum can verify margin and settlement rules efficiently.

---

[Back to README](../README.md)
