# Development status

**Status: prototype / research. Not production-ready.**

## Confirmed project direction

- Bitcoin is the only blockchain and consensus foundation.
- BITRUBIN CORE is a deterministic verification layer over Bitcoin history.
- Participants are intended to run their own Bitcoin Core full node.
- A second independent Bitcoin Core node is intended as an additional chain-data cross-check.
- BRBN and BPRL use 38 decimal places and deterministic integer arithmetic.
- Public target supplies: 2,100,000 BRBN and 700,000 BPRL (Pearls).
- The public BRBN target is divided into four epochs of 525,000 BRBN; the BPRL allocation rate halves at each successive epoch.
- BPRL requires valid BRBN issuance and cannot be issued independently.
- Exact integer-rate representation, event-level calculation, rounding/remainder rules, and final cap enforcement remain to be specified and tested.
- Additional allocations: 3% founder allocation and 2% developer allocation, calculated on the public target supplies.
- Maximum supplies: 2,205,000 BRBN and 735,000 Pearls.

## Open technical questions

1. **Positive-value OP_RETURN compatibility:** not yet tested on Signet. Bitcoin Core standardness and relay policy must be tested; consensus validity and relay acceptance must not be conflated.
2. **Recipient rule:** OP_RETURN outputs are unspendable. A deterministic rule must identify the recipient for the derived BRBN and Pearls. A proposed rule is to use the first normal spendable output in the same transaction, but this has not been approved as final.
3. **Launch block:** an official start block must be selected and documented. Transactions before that block are excluded.
4. **Transaction validity:** specify exact output selection, value parsing, duplicate prevention, and malformed-transaction handling.
5. **Chain reorganizations:** define confirmation policy and deterministic rollback/recalculation behavior.
6. **Independent verification:** implement reproducible tests using two independently operated Bitcoin Core nodes.
7. **Arithmetic:** implement and test 38-decimal integer calculations, four-epoch BPRL halving, transaction-splitting neutrality, rounding/remainder handling, and supply caps.
8. **Security review:** independent review and testnet validation are required before any production use.

## Important distinction

The current concept counts positive BTC values in qualifying OP_RETURN outputs from the launch block onward. It does not use a special BRBN marker or hash marker in the current proposal. This remains a design proposal until the validation rules and network behavior are tested.

## Allocation note

The developer allocation is intended to be fully allocated from the beginning rather than earned through milestones. Custody, named recipients, and transfer arrangements still need to be documented.
