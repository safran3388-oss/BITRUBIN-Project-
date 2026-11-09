> **HISTORICAL DRAFT — SUPERSEDED.** This v2.2 version is retained only to document an earlier development stage. It is not the current BITRUBIN specification. The current documents are [Whitepaper v2.4 (English)](WHITEPAPER_EN_v2.4.md) and [Whitepaper v2.4 (German)](WHITEPAPER_DE_v2.4.md). Recipient attribution and technical issuance rules are explicitly marked as unresolved in v2.4.

---

# BITRUBIN – Whitepaper v2.2 (Prototype / Research Status)

**Burn Bitcoin. Create BITRUBIN.**  
*A digital monetary system built on Bitcoin*  
Author: Faycal Hammouti · 4 November 2026

> **Important notice:** This document describes a proposal and research project. BITRUBIN is not a finished or production-ready system. In particular, acceptance and relay of positive-value OP_RETURN outputs have not yet been demonstrated on Bitcoin Signet.

## 1. Purpose and core idea

BITRUBIN (BRBN) is designed as an independent digital monetary and issuance protocol using Bitcoin as its only blockchain and sole consensus foundation. Its goal is a transparent, scarce digital unit with up to 38 decimal places. BITRUBIN is intended to complement Bitcoin, not replace it with a second blockchain.

Issuance is proposed to be triggered by verifiable Bitcoin transactions containing a positive BTC value in a qualifying unspendable OP_RETURN output. BITRUBIN CORE reads and verifies Bitcoin history and derives protocol state deterministically.

## 2. Architecture: Bitcoin as the only foundation

There is no separate BITRUBIN blockchain, no BITRUBIN block production, no BITRUBIN miners or validators, and no separate consensus. Bitcoin determines which transactions and blocks belong to the valid Bitcoin chain. BITRUBIN CORE is an additional verification and interpretation layer, not a replacement for Bitcoin consensus.

The target model expects each participant to run their own Bitcoin Core full node and validate Bitcoin data independently. A second independently operated Bitcoin node provides an additional cross-check and chain-data comparison. The precise operating and synchronization design still needs implementation and testing.

## 3. Issuance proposal and OP_RETURN rule

The current proposal counts every positive BTC value in a qualifying unspendable OP_RETURN output from a designated official BITRUBIN start block onward. Transactions before that start block are not counted retroactively. No special BRBN marker or additional BRBN hash is part of the current proposal.

The OP_RETURN output is unspendable. Its assigned value is therefore permanently unspendable under the normal Bitcoin output model. However, whether Bitcoin nodes accept, consider standard, and relay outputs with a positive value is an open technical question. This rule has not yet been demonstrated on Signet and must not be presented as working.

An OP_RETURN script does not identify a recipient. One possible, not-yet-approved approach is to use the first normal spendable output in the same transaction as the recipient. This is only a proposal and must be decided before protocol release.

## 4. Units and decimal places

The nominal accounting definitions are: **1 BTC = 1 BRBN** and **1 satoshi = 1 Rubini**. These are unit definitions only. They do not promise market value, backing, redemption, or convertibility.

BRBN and Pearls each use **38 decimal places**. One Rubini equals 0.00000001 BRBN (10⁻⁸ BRBN), or 10³⁰ smallest BRBN accounting units at 38 decimal places. All protocol calculations must use deterministic integer arithmetic; floating-point arithmetic is unsuitable for consensus rules.

## 5. Supply and allocations

- Public target supply: **2,100,000 BRBN** and **700,000 Pearls**.
- Additional founder allocation: **63,000 BRBN** and **21,000 Pearls** (3% of each public target supply).
- Additional developer allocation: **42,000 BRBN** and **14,000 Pearls** (2% of each public target supply).
- Maximum total supplies including allocations: **2,205,000 BRBN** and **735,000 Pearls**.

The full developer allocation is intended to be available from the beginning; custody, recipients, and transfer terms still need to be documented clearly.

Pearls are calculated proportionally to valid public BRBN issuance. The target ratio at full public issuance is 1 Pearl per 3 BRBN. Calculation must be deterministic, use 38 decimal places, and provide no advantage through transaction splitting. The maximum supply must never be exceeded. No halving is planned.

## 6. Verification and safeguards

BITRUBIN CORE must at minimum verify the Bitcoin transaction, output index, output script, positive BTC value, inclusion in the valid Bitcoin chain, and required confirmation depth. Each issuance event must have a unique identity; TXID plus VOUT is a candidate technical event identifier.

The system must prevent duplicate processing, reject malformed or ambiguous transactions, and handle Bitcoin reorganizations correctly. If a reorganization occurs, affected events must be rolled back and derived state recalculated reproducibly. The exact confirmation depth and error rules remain to be specified.

Independent node verification reduces reliance on a single data provider but does not replace Bitcoin consensus security. If Bitcoin consensus itself is compromised, BITRUBIN cannot fully protect its foundation.

## 7. Open issues and development plan

Before a public prototype release, the following points must be resolved:

1. Acceptance and relay of positive-value OP_RETURN outputs on Signet and the Bitcoin network.
2. Binding recipient rule.
3. Official start block.
4. Transaction and confirmation rules.
5. Reorganization and duplicate handling.
6. Exact integer and rounding rules.
7. Reproducible tests and independent security review.

The next step is an isolated Signet test to investigate OP_RETURN standardness and relay policy. Only after that should the issuance and recipient rules be finalized and implemented in BITRUBIN CORE.

## 8. Status and disclaimer

BITRUBIN remains at the concept, research, and prototype stage. There is no assurance that the proposed issuance format will be accepted or relayed by the Bitcoin network. This whitepaper is not investment advice, an offer to sell, or a promise of token value, yield, backing, or redemption. Use with real BTC should only be considered after implementation, testing, and independent review.

© 2026 Faycal Hammouti. Prototype document; subject to technical revision.
