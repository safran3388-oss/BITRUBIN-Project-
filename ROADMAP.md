# BITRUBIN roadmap

This roadmap is provisional. Items are not complete unless evidence and reproducible tests are published.

## Phase 1 — Freeze the protocol rules
- Confirm the recipient rule for each qualifying transaction.
- Select and document the launch block.
- Specify exact OP_RETURN eligibility and amount handling.
- Specify 38-decimal integer arithmetic for BRBN and BPRL.
- Freeze four-epoch BPRL halving calculations, rounding/remainder rules, transaction-splitting neutrality, and supply-cap behavior.
- Specify confirmation and reorganization handling.

## Phase 2 — Bitcoin testnet research
- Test positive-value OP_RETURN transaction construction on Signet.
- Check local Bitcoin Core acceptance, mempool policy, and peer relay behavior.
- Record Bitcoin Core versions, commands, transaction IDs, and observed results.
- Distinguish consensus validity from standardness and relay policy.

## Phase 3 — BITRUBIN CORE prototype
- Read and independently validate Bitcoin chain data through Bitcoin Core.
- Derive qualifying events deterministically.
- Add duplicate prevention and reorganization-safe state recalculation.
- Compare results from two independent Bitcoin Core nodes.
- Publish reproducible automated tests.

## Phase 4 — Independent review
- Security review of transaction parsing and state derivation.
- Arithmetic and supply-cap review.
- Reproducibility review by independent developers.
- Resolve all critical findings before considering production use.

## Phase 5 — Public test release
- Publish source, test instructions, known limitations, and test evidence.
- Do not describe the system as production-ready until the required tests and reviews are complete.
