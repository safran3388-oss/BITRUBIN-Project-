[🌐 **BITRUBIN WEBSITE — OPEN THE LIVE WEBSITE**](https://safran3388-oss.github.io/BITRUBIN-Project-/)

# BITRUBIN
**Burn Bitcoin. Create BITRUBIN.**  
*A proposed digital monetary protocol built on Bitcoin.*

> **DEVELOPERS WANTED — FULL TECHNICAL PROJECT TAKEOVER**  
> The creator is looking for an experienced Bitcoin developer or team to review, specify, build, test, and take over the technical development of BITRUBIN. [Open a GitHub issue to make contact](https://github.com/safran3388-oss/BITRUBIN-Project-/issues/new).

> **Research project · Prototype stage · Not production-ready**  
> Positive-value OP_RETURN acceptance and relay have not yet been demonstrated on Signet. No live BITRUBIN issuance system is being presented.

## The central idea: Bitcoin burn → BITRUBIN

The current proposal counts positive BTC values in qualifying unspendable OP_RETURN outputs. **No special BRBN marker is required.** From a future official launch block:

1. A Bitcoin transaction includes an OP_RETURN output with a positive BTC value.
2. BITRUBIN CORE reads the confirmed Bitcoin transaction through Bitcoin Core.
3. CORE checks the output against deterministic protocol rules and prevents duplicate processing.
4. The qualifying value is accounted for as BRBN: **1 BTC = 1 BRBN** and **1 satoshi = 1 Rubini**.
5. BPRL (Pearls) is calculated proportionally to valid BRBN issuance.

**Important technical limitation:** OP_RETURN outputs are unspendable, but positive-value OP_RETURN outputs may not be accepted as standard or relayed by Bitcoin Core/network policy. This must be tested on Signet. Consensus validity, standardness, mempool acceptance, and peer relay are separate issues. The recipient/wallet attribution rule is also not finalized.

## Project architecture

- Bitcoin is the only blockchain and consensus foundation.
- No separate BITRUBIN blockchain, block production, mining, or validator network.
- BITRUBIN CORE is a deterministic verification and accounting layer over Bitcoin history.
- Each participant is intended to run their own Bitcoin Core full node; a second independent node provides an additional cross-check.
- Independent reproducible tests and security review are required before production use.

## BRBN and Pearls — current proposed rules

|  | BRBN | BPRL (Pearls) |
|---|---:|---:|
| Public target supply | 2,100,000 | 700,000 |
| Additional founder allocation (3%) | 63,000 | 21,000 |
| Additional developer allocation (2%) | 42,000 | 14,000 |
| **Planned maximum including allocations** | **2,205,000** | **735,000** |
| Decimal places | 38 | 38 |

- BPRL belongs to BITRUBIN and is issued only in connection with valid BRBN.
- Public BPRL target is proportional to public BRBN: **1 BPRL per 3 BRBN** at full target issuance.
- **No halving. No epochs.**
- Founder and developer allocations are additional to public target supplies.
- The developer allocation is intended to be available from the beginning; custody and transfer terms remain to be documented.
- These are proposed protocol rules, not proof that tokens have been issued or are available.

## Current development status

The project is in research/prototype stage. The following remain open before activation:

1. Signet testing of positive-value OP_RETURN acceptance and relay.
2. Final recipient/wallet attribution rule.
3. Official launch block and confirmation policy.
4. Duplicate prevention, malformed transaction handling, and reorganization behavior.
5. Exact 38-decimal integer arithmetic, proportional BPRL rounding/remainder rules, and supply-cap enforcement.
6. Reproducible tests across two independent Bitcoin Core nodes and independent security review.

## Project documents

| Document | Purpose |
|---|---|
| [Whitepaper v2.4 — English](WHITEPAPER_EN_v2.4.md) | Current English project rules |
| [Whitepaper v2.4 — German](WHITEPAPER_DE_v2.4.md) | Aktueller deutscher Projektstand |
| [Development status](DEVELOPMENT_STATUS.md) | Confirmed direction and unresolved questions |
| [Roadmap](ROADMAP.md) | Planned technical work |
| [Security notes](SECURITY.md) | Security assumptions and limitations |

Older whitepapers v2.2 and v2.3 are retained as historical drafts and are superseded by v2.4.

## Rights and project ownership

BITRUBIN is the creator's project. This repository is public for visibility and technical review; **no open-source license is granted**. Public visibility does not grant permission to issue BRBN/BPRL, change official rules, use the branding, or commercially exploit project materials. Any contribution, license, or transfer of technical responsibility must be agreed with the project owner in writing. A formal contribution and rights agreement should be completed before accepting outside contributions.

## Author

**Faycal Hammouti**

*This experimental project is not financial advice, an offer to sell tokens, or a promise of value, backing, redemption, or future functionality.*
