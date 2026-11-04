# BITRUBIN — Whitepaper v2.3
**Burn Bitcoin. Create BITRUBIN.**  
*A proposed digital monetary protocol built on Bitcoin*  
Author: Faycal Hammouti · 4 November 2026

> **Research notice:** BITRUBIN is a proposal and prototype project, not production-ready. Positive-value OP_RETURN acceptance and relay have not yet been demonstrated on Signet.

## 1. Purpose

BITRUBIN (BRBN) is designed as an independent digital monetary protocol using Bitcoin as its only blockchain and sole consensus foundation. It is intended to complement Bitcoin, not replace it with a second chain.

## 2. Architecture

There is no separate BITRUBIN blockchain, block production, mining network, validator network, or independent consensus. Bitcoin determines the valid chain. BITRUBIN CORE is a deterministic verification and interpretation layer over Bitcoin history.

The intended operating model is that each participant runs their own Bitcoin Core full node and validates Bitcoin data independently. A second independently operated Bitcoin Core node is an additional cross-check, not a substitute for the participant's own verification.

## 3. Proposed Bitcoin issuance event

The current repository proposal counts positive BTC values in qualifying unspendable OP_RETURN outputs from an officially designated BITRUBIN launch block onward. Earlier transactions are excluded. The current proposal does not require a special BRBN marker or hash marker.

An OP_RETURN output is unspendable. However, whether positive-value OP_RETURN outputs are accepted as standard and relayed by Bitcoin Core and the network is an open technical question. This has not yet been demonstrated on Signet. Consensus validity, standardness policy, local mempool acceptance, and peer relay must be tested separately.

An OP_RETURN output does not identify a recipient. A deterministic recipient rule, launch block, confirmation policy, duplicate prevention, malformed-transaction handling, and reorganization behavior must be finalized before issuance logic is activated.

## 4. Units and precision

BRBN and BPRL use **38 decimal places**. All protocol arithmetic must use deterministic integer arithmetic; floating-point calculations must not determine token state.

The nominal accounting definitions are **1 BTC = 1 BRBN** and **1 satoshi = 1 Rubini**. These are unit definitions only and do not promise market value, backing, redemption, or convertibility.

One Rubini is 0.00000001 BRBN (10^-8 BRBN). With 38 decimal places, one Rubini equals 10^30 smallest BRBN accounting units.

## 5. Public supplies and allocations

| Allocation | BRBN | BPRL (Pearls) |
|---|---:|---:|
| Public target supply | 2,100,000 | 700,000 |
| Founder allocation (additional 3%) | 63,000 | 21,000 |
| Developer allocation (additional 2%) | 42,000 | 14,000 |
| **Maximum planned supply** | **2,205,000** | **735,000** |

The full developer allocation is intended to be allocated from the beginning, rather than earned gradually through milestones. Custody, named recipients, and transfer arrangements must be documented before activation.

## 6. Pearls (BPRL) issuance

BPRL belongs to the BITRUBIN system and requires valid BRBN issuance; BPRL cannot be created independently of a valid BRBN event. The public BPRL target is 700,000.

The public BRBN target is divided into four epochs of 525,000 BRBN each. The BPRL allocation rate is halved at each successive epoch. The exact integer-rate representation, event-level calculation, rounding/remainder treatment, and final cap enforcement must be specified in the protocol rules and covered by reproducible tests before activation. Transaction splitting must not create an allocation advantage. The total BPRL supply, including founder and developer allocations, must never exceed 735,000.

## 7. Verification and safety requirements

BITRUBIN CORE must deterministically verify qualifying Bitcoin transactions and outputs, chain inclusion, confirmation depth, unique event identity (TXID plus VOUT is the proposed identifier), duplicate processing, and reorganization effects. Two independently operated Bitcoin Core nodes should produce the same derived result from the same accepted chain history.

BITRUBIN relies on Bitcoin consensus and cannot provide stronger consensus security than Bitcoin itself. If Bitcoin consensus is compromised, BITRUBIN cannot fully protect its foundation.

## 8. Open work

1. Test positive-value OP_RETURN standardness and relay on Signet.
2. Freeze the recipient rule and official launch block.
3. Specify confirmation, duplicate, malformed-transaction, and reorganization rules.
4. Freeze exact 38-decimal integer arithmetic and BPRL epoch/rounding rules.
5. Implement BITRUBIN CORE and compare independent-node results.
6. Publish reproducible tests and obtain independent security review.

## 9. Status and disclaimer

BITRUBIN remains at the research and prototype stage. The issuance mechanism is not proven or activated, and no production deployment is announced. Do not use real funds or rely on token issuance claims in production. This document is not investment advice, an offer to sell, or a promise of value, yield, backing, or redemption.

© 2026 Faycal Hammouti. Technical proposal; subject to revision.
