# BITRUBIN — Whitepaper v2.4
**Burn Bitcoin. Create BITRUBIN.**  
*A proposed digital monetary protocol built on Bitcoin*  
Author: Faycal Hammouti · 9 November 2026

> **Research and development status:** BITRUBIN is a proposal and prototype project, not production-ready. Acceptance and relay of positive-value OP_RETURN outputs have not yet been demonstrated on Signet. This document describes intended rules and open questions, not a functioning issuance system.

## 1. Purpose and core principle

BITRUBIN (BRBN) is intended to be a digital monetary protocol using Bitcoin as its only blockchain and sole consensus foundation. It is designed to complement Bitcoin without introducing a second blockchain, independent block production, or a separate mining/validator network.

The central idea is: **Burn Bitcoin. Create BITRUBIN.** The current proposal interprets positive BTC values in qualifying unspendable OP_RETURN outputs. No special BRBN marker is required. Only events from a future, officially designated launch block may count; retroactive issuance is not intended.

## 2. Bitcoin-burn and OP_RETURN mechanism

1. A Bitcoin transaction contains an OP_RETURN output with a positive BTC value.
2. BITRUBIN CORE reads the confirmed transaction from the Bitcoin chain through Bitcoin Core.
3. CORE checks whether the output qualifies under the published rules, is unique, and has not already been processed.
4. The qualifying BTC value is accounted for under the rule **1 BTC = 1 BRBN**; the smallest named unit follows **1 satoshi = 1 Rubini**.
5. BPRL (Pearls) is calculated proportionally to valid BRBN issuance.

An OP_RETURN output is unspendable. Separately, it must be tested whether Bitcoin Core treats positive-value OP_RETURN outputs as standard, accepts them into its mempool, and relays them to peers. Consensus validity, standardness policy, local mempool acceptance, and peer relay are distinct questions. This mechanism has not yet been demonstrated on Signet and must not be presented as operational.

An OP_RETURN output does not identify a recipient. The binding rule that assigns derived units to a wallet or address remains open and must be explicitly approved before activation. A recipient must not be silently inferred from an arbitrary transaction output.

## 3. Architecture and verification

Bitcoin is the only blockchain and consensus foundation. BITRUBIN CORE is a deterministic verification and interpretation layer over Bitcoin history; it does not create blocks or an independent consensus.

The intended operating model is for each participant to run their own Bitcoin Core full node and validate Bitcoin data independently. A second independently operated Bitcoin Core node provides an additional cross-check. Both nodes should derive the same BITRUBIN result from the same valid chain history.

Before activation, the protocol must specify the launch block, confirmation depth, unique event identity (TXID plus VOUT is proposed), duplicate prevention, malformed or ambiguous transactions, and rollback/recalculation behavior during chain reorganizations.

## 4. Units and precision

- **1 BTC = 1 BRBN** (nominal protocol and accounting definition).
- **1 satoshi = 1 Rubini** (nominal definition of the smallest named unit).
- BRBN and BPRL each use **38 decimal places**.
- All state-determining calculations must use deterministic integer arithmetic; floating-point arithmetic is excluded.

These unit definitions do not promise market value, BTC backing, repayment, redemption, or a guaranteed exchange rate.

## 5. Supplies and allocations

| Allocation | BRBN | BPRL (Pearls) |
|---|---:|---:|
| Public target supply | 2,100,000 | 700,000 |
| Additional founder allocation (3%) | 63,000 | 21,000 |
| Additional developer allocation (2%) | 42,000 | 14,000 |
| **Planned maximum including allocations** | **2,205,000** | **735,000** |

Founder and developer allocations are additional to the public target supplies. Under the current project direction, the full developer allocation is intended to be available from the beginning, not earned through milestones. Custody, named recipients, and transfer terms still need to be documented.

## 6. Pearls (BPRL) — proportional, no halving

BPRL belongs to the BITRUBIN system and is issued only in connection with valid BRBN issuance. The public target is 700,000 BPRL against a public BRBN target of 2,100,000 BRBN. This defines a target ratio of **1 BPRL per 3 BRBN** at full public issuance.

**There is no halving and no epoch schedule.** BPRL issuance is proportional to valid BRBN issuance. Calculation must be deterministic, use 38 decimal places, and provide no advantage through transaction splitting. Rounding/remainder rules and enforcement of the total cap must be specified exactly and tested before activation. Total planned BPRL, including founder and developer allocations, must never exceed 735,000.

## 7. Open technical work

1. Construct positive-value OP_RETURN outputs on Signet and separately test acceptance, mempool behavior, and relay.
2. Agree and formally specify the recipient/wallet attribution rule with the project owner.
3. Select the official launch block and confirmation policy.
4. Specify output eligibility, event identity, duplicate handling, and reorganization rules.
5. Implement and test 38-decimal integer arithmetic, proportional BPRL calculation, rounding, and supply caps.
6. Compare results from two independently operated Bitcoin Core nodes.
7. Publish reproducible tests and obtain an independent security review.

## 8. Development status and full technical takeover

BITRUBIN is seeking an experienced Bitcoin/protocol developer or development team willing to review the design, finalize the specification, implement the prototype, build reproducible tests, and take over the full technical development of the project. The immediate priorities are Signet research into positive-value OP_RETURN outputs, a safe recipient rule, and a reproducible BITRUBIN CORE prototype.

Until these tasks are completed and independently reviewed, BITRUBIN remains a research and prototype project. No production issuance is active, and users should not send real BTC in expectation of receiving BRBN.

## 9. Disclaimer

This document is not investment advice, an offer to sell, or a promise of value, yield, backing, or repayment. The technical feasibility of the proposed OP_RETURN issuance mechanism remains unresolved.

© 2026 Faycal Hammouti. Technical proposal; subject to revision.
