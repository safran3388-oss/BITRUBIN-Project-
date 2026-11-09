# Development status

**Status: research / prototype. Not production-ready.**  
Last aligned with the current project direction: 9 November 2026.

## Current project direction

- Bitcoin is the only blockchain and consensus foundation.
- No separate BITRUBIN blockchain, block production, mining, validator network, or independent consensus.
- BITRUBIN CORE is intended as a deterministic verification and accounting layer over Bitcoin history.
- Each participant is intended to operate their own Bitcoin Core full node.
- A second independently operated Bitcoin Core node is an additional chain-data cross-check.
- The current issuance proposal counts positive BTC values in qualifying unspendable OP_RETURN outputs from a future official launch block.
- No special BRBN marker or hash marker is required by the current proposal.
- Nominal unit definitions: 1 BTC = 1 BRBN; 1 satoshi = 1 Rubini.
- BRBN and BPRL use 38 decimal places and deterministic integer arithmetic.
- Public target supplies: 2,100,000 BRBN and 700,000 BPRL.
- BPRL is proportional to valid BRBN issuance: target ratio 1 BPRL per 3 BRBN at full public issuance.
- **There is no BPRL halving and no epoch schedule.**
- Additional allocations on top of public targets: 63,000 BRBN + 21,000 BPRL for founder (3%); 42,000 BRBN + 14,000 BPRL for developers (2%).
- Planned maximum including these allocations: 2,205,000 BRBN and 735,000 BPRL.
- Developer allocation is intended to be available from the beginning; custody, recipients, and transfer terms remain open.

## Open technical questions

1. **Positive-value OP_RETURN compatibility:** not yet demonstrated on Signet. Test transaction construction, consensus validity, standardness policy, local mempool acceptance, and peer relay separately.
2. **Recipient attribution:** OP_RETURN does not identify a recipient. The wallet/address assignment rule must be explicitly approved; no provisional output-selection rule is official.
3. **Launch block and confirmations:** select the official start block and define required confirmation depth.
4. **Event processing:** define exact output qualification, amount parsing, TXID+VOUT identity, duplicate prevention, and malformed/ambiguous transaction handling.
5. **Reorganizations:** specify deterministic rollback and state recalculation.
6. **Arithmetic:** specify 38-decimal integer units, proportional BPRL formula, rounding/remainder handling, transaction-splitting neutrality, and final caps. No halving/epoch logic is part of the current rules.
7. **Independent verification:** compare identical results from two independently operated Bitcoin Core nodes.
8. **Security review:** publish reproducible tests and obtain independent review before production use.

## Important distinction

The issuance mechanism is a proposal, not a demonstrated feature. Positive-value OP_RETURN outputs may face standardness and relay-policy restrictions even where a transaction might be consensus-valid. No real BTC should be sent in expectation of BRBN issuance.

## Project takeover

The creator is seeking a Bitcoin/protocol developer or development team to review the design, finalize unresolved protocol details with the creator, implement BITRUBIN CORE, create reproducible tests, and take over the technical development. The official BRBN/BPRL rules remain under the project owner's control and must not be changed unilaterally.

