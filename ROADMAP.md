# BITRUBIN roadmap

**Status: provisional research and prototype plan.**  
The project is seeking an experienced Bitcoin developer or team for full technical development/takeover. Items are not complete unless evidence and reproducible tests are published.

## Phase 1 — Confirm protocol specification with the project owner

- Confirm the current rule: positive BTC values in qualifying OP_RETURN outputs; no special BRBN marker.
- Confirm nominal units: 1 BTC = 1 BRBN and 1 satoshi = 1 Rubini.
- Confirm 38-decimal deterministic integer arithmetic.
- Implement proportional BPRL issuance: public target 700,000 BPRL against 2,100,000 public BRBN (target ratio 1:3).
- No halving and no epoch schedule.
- Specify rounding/remainder handling, transaction-splitting neutrality, and supply-cap behavior.
- Agree the recipient/wallet attribution rule; do not assume OP_RETURN identifies a recipient.
- Select and document the official launch block and confirmation policy.
- Specify event identity, duplicate prevention, malformed transaction handling, and reorganization behavior.

## Phase 2 — Bitcoin Signet research

- Test construction of positive-value OP_RETURN transactions.
- Check consensus validity separately from standardness policy.
- Record local Bitcoin Core mempool acceptance and peer relay behavior.
- Record Bitcoin Core versions, commands, transaction IDs, and observed results.
- Document any restrictions or required alternatives before claiming feasibility.

## Phase 3 — BITRUBIN CORE prototype

- Read and independently validate Bitcoin chain data through Bitcoin Core.
- Detect qualifying OP_RETURN outputs according to the approved specification.
- Derive BRBN and proportional BPRL events deterministically.
- Add duplicate prevention and reorganization-safe state recalculation.
- Implement 38-decimal integer arithmetic and exact supply caps.
- Compare results from two independently operated Bitcoin Core nodes.
- Publish reproducible automated tests.

## Phase 4 — Independent review

- Review transaction parsing, recipient attribution, and state derivation.
- Review arithmetic, proportional BPRL calculations, rounding, and supply caps.
- Review chain reorganization and duplicate handling.
- Resolve critical findings and publish test evidence.

## Phase 5 — Public test release

- Publish source, test instructions, known limitations, and reproducible evidence.
- Keep the system clearly labeled experimental until tests and reviews are complete.
- Do not announce production readiness or invite real-BTC use before the project owner approves the release.
