# BITRUBIN — Seeking Bitcoin Developers

**Burn Bitcoin. Create Bitrubin.**

BITRUBIN is an independent project exploring a Bitcoin-based issuance and accounting system using Bitcoin burn transactions. I am looking for experienced Bitcoin developers to independently review the concept, assess its feasibility and security, and potentially lead or take over its technical implementation.

## The core idea

The proposed issuance mechanism focuses on Bitcoin transactions containing **positive-value OP_RETURN outputs**:

1. A Bitcoin transaction includes an OP_RETURN output carrying a positive BTC value.
2. The value sent to that provably unspendable output is treated as a Bitcoin burn.
3. Under the proposed BITRUBIN rules, qualifying burns are used as the basis for calculating BRBN and Rubini issuance.
4. BPRL (Bitpearls) are intended to be issued proportionally to BRBN.

**A special BRBN marker is not required in the current concept:** every qualifying positive-value OP_RETURN output is intended to count. The exact transaction eligibility, parsing, attribution and accounting rules still need a rigorous technical specification and independent review.

## Current proposed monetary rules

- **BRBN (Bitrubin):** 2,100,000 public units.
- **Rubini:** the proposed smallest unit, with 1 satoshi corresponding to 1 Rubini.
- **BPRL (Bitpearls):** 700,000 public units, issued proportionally to BRBN.
- **Precision:** 38 decimal places for BRBN and BPRL.
- **Halving:** none is intended.

These are the project's current proposed rules, not a claim that a working issuance implementation already exists. The exact formulas, rounding, supply accounting and treatment of historical transactions must be documented and tested before implementation.

## Intended architecture

The project's direction is to use Bitcoin as the only blockchain and consensus foundation:

- Bitcoin Core full nodes provide the underlying Bitcoin chain data.
- BITRUBIN CORE independently parses and verifies relevant Bitcoin transactions.
- A second independently operated Bitcoin node may be used as an additional comparison and consistency check.
- BITRUBIN software calculates and records BRBN and BPRL state according to the published rules.

The project does not intend to introduce a separate blockchain, BITRUBIN mining, or a separate block-production consensus system.

## Developers wanted

I am looking for developers with experience in some of these areas:

- Bitcoin Core, Bitcoin transactions, scripts and UTXO mechanics
- OP_RETURN outputs and provably unspendable outputs
- Bitcoin chain indexing and reorganisation handling
- Deterministic transaction parsing and verification
- Secure accounting, issuance and wallet-balance interfaces
- Automated tests, threat modelling and independent code review

## First technical questions to solve

Before building a production system, the team should specify and test at least the following:

1. What exactly qualifies as a positive-value OP_RETURN burn, including policy and consensus edge cases?
2. How are transactions with multiple inputs or outputs handled?
3. How can the originating owner or recipient be attributed without making unsupported assumptions about Bitcoin addresses?
4. How are confirmations, chain reorganisations and historical transactions handled?
5. How do the issuance formulas reconcile with the stated public supplies and decimal precision?
6. How can two independent Bitcoin Core nodes be compared reliably?
7. How can balances be displayed safely without implying that BRBN or BPRL are native Bitcoin assets?

These questions are part of the work. I welcome developers who challenge assumptions and identify flaws rather than simply accepting the proposal.

## What I am asking

I am the project founder and am seeking an experienced developer or team to:

- Review the concept and its written rules.
- Produce a clear technical specification.
- Build a small, testable proof of concept.
- Audit the transaction interpretation and issuance accounting.
- Discuss taking the technical lead or coordinating further development.

The project is open to serious technical discussion and independent criticism. Cooperation, responsibilities, licensing and any handover would be discussed transparently before work begins.

## Project links

- **Website:** https://safran3388-oss.github.io/BITRUBIN-Project-/
- **GitHub repository:** https://github.com/safran3388-oss/BITRUBIN-Project-

**BITRUBIN — Burn Bitcoin. Create Bitrubin.**
