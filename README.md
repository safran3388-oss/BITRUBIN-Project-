# BITRUBIN

[**Open the BITRUBIN website**](https://safran3388-oss.github.io/BITRUBIN-Project-/) · [View the public GitHub repository](https://github.com/safran3388-oss/BITRUBIN-Project-)

<p align="center">

**BURN BITCOIN. CREATE BITRUBIN.**

*A proposed digital monetary system built on Bitcoin.*

</p>

---

> **Research project · Prototype stage · Not production-ready**
>
> BITRUBIN is an experimental protocol proposal. Its central positive-value OP_RETURN issuance mechanism has **not yet been proven compatible with Bitcoin Core standardness and relay policy on Signet**. No live issuance system is being presented.

## Welcome to BITRUBIN

BITRUBIN (BRBN) is being designed as an independent digital monetary protocol that uses **Bitcoin as its only blockchain and consensus foundation**.

The idea is to derive a transparent and reproducible BRBN and Pearls ledger from qualifying Bitcoin transactions. The project aims to complement Bitcoin—not replace it with another blockchain.

## Explore the project

| Start here | What you will find |
|---|---|
| **[German whitepaper v2.3](WHITEPAPER_DE_v2.3.md)** | Aktueller abgestimmter Konzeptstand |
| **[English whitepaper v2.3](WHITEPAPER_EN_v2.3.md)** | Current aligned project concept |
| [Development status](DEVELOPMENT_STATUS.md) | What is decided and what still needs to be tested |
| [Roadmap](ROADMAP.md) | Planned development steps |
| [Security notes](SECURITY.md) | Security assumptions, risks and safeguards |

## The idea in a nutshell

- **One blockchain:** Bitcoin is the only blockchain and consensus layer.
- **Independent verification:** Participants are intended to run their own Bitcoin Core full node.
- **BITRUBIN CORE:** A deterministic verification and interpretation layer that reads Bitcoin history and derives the BITRUBIN state.
- **Two units:** BRBN (Bitrubin) and Pearls (BPRL), following defined supply and allocation rules.
- **Verifiable rules:** Transaction checks, supply limits and calculations must be deterministic and independently reproducible.

There is no separate BITRUBIN blockchain, no separate mining or validator network, and no independent BITRUBIN consensus.

## BRBN and Pearls — proposed supply

|  | BRBN | Pearls |
|---|---:|---:|
| Public target supply | 2,100,000 | 700,000 |
| Founder allocation | 63,000 | 21,000 |
| Developer allocation | 42,000 | 14,000 |
| **Maximum planned supply** | **2,205,000** | **735,000** |
| Decimal places | 38 | 38 |

BPRL (Pearls) requires valid BRBN issuance and is not issued independently. The public BRBN target is divided into four epochs of 525,000 BRBN; the BPRL allocation rate halves at each successive epoch. Exact integer-rate, rounding and remainder rules must be frozen and tested before activation. All calculations use deterministic integer arithmetic.

**Precision and unit definitions:** BRBN and BPRL use **38 decimal places**. 1 BTC = 1 BRBN and 1 satoshi = 1 Rubini are nominal accounting definitions only; they do not promise market value, BTC backing, redemption, or a guaranteed exchange rate. One Rubini equals 10⁻⁸ BRBN, or 10³⁰ smallest BRBN accounting units at 38 decimals.

These figures and rules describe the current proposal; they do not mean that tokens have already been issued or are available.

## How issuance is proposed to work

The current proposal would count positive BTC values in qualifying unspendable OP_RETURN outputs, beginning only at a future, officially designated BITRUBIN launch block. Earlier Bitcoin transactions would not count retroactively.

Several essential details remain open, including:

- whether Bitcoin Core accepts and relays positive-value OP_RETURN outputs under its standardness policy;
- how the recipient is determined, since an OP_RETURN output is unspendable;
- the official launch block and confirmation policy;
- duplicate prevention, malformed transactions and chain reorganizations.

**The Signet test is a necessary next step.** Until the rules have been tested, specified and independently reviewed, the issuance mechanism remains a proposal.

## Security and transparency

BITRUBIN relies on Bitcoin's consensus. It does not create a second consensus system and cannot protect users if Bitcoin's own consensus security is fundamentally compromised. The project therefore focuses on independent Bitcoin data verification, deterministic rules, reproducible tests and clear documentation of limitations.

## Project status

**Current status: research and prototype development.**

The architecture and proposed token rules are documented. Important technical questions—especially positive-value OP_RETURN acceptance and relay on Signet—remain unresolved. BITRUBIN is not ready for production use.

For details, see the [development status](DEVELOPMENT_STATUS.md) and [security notes](SECURITY.md).

---

## Author

**Faycal Hammouti**

*BITRUBIN is an experimental research project. This repository is for technical and informational purposes only. It is not financial advice, an offer to sell tokens, a promise of value, or a guarantee of future functionality.*
