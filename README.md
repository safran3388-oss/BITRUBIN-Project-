# BITRUBIN

**Burn Bitcoin. Create BITRUBIN.**

*A new digital monetary system built on Bitcoin.*

BITRUBIN is a proposed Bitcoin-based monetary protocol. Bitcoin is intended to remain its only blockchain and consensus foundation. BITRUBIN CORE is designed to independently verify Bitcoin data and derive the BRBN and Pearls token state from qualifying Bitcoin transactions.

## Project status

**Prototype / research stage — not production-ready.**

The project is documenting and testing a proposed issuance mechanism based on positive-value, unspendable Bitcoin OP_RETURN outputs. This mechanism has not yet been demonstrated to work with Bitcoin Core standardness and relay policy. No claim is made that it is currently operational.

## Design principles

- Bitcoin is the only blockchain and consensus foundation.
- No separate BITRUBIN blockchain, mining network, validator network, or independent consensus.
- Each participant is intended to run and verify with their own Bitcoin Core full node.
- A second independently operated Bitcoin Core node is intended as an additional chain-data cross-check.
- BRBN and Pearls state is to be derived deterministically from Bitcoin history.

## Proposed token parameters

| Parameter | BRBN | Pearls |
|---|---:|---:|
| Public target supply | 2,100,000 | 700,000 |
| Founder allocation (additional) | 63,000 | 21,000 |
| Developer allocation (additional) | 42,000 | 14,000 |
| Maximum supply | 2,205,000 | 735,000 |
| Decimal places | 38 | 38 |

There is no halving in the current model. Pearls are intended to be allocated proportionally to valid BRBN issuance, using deterministic integer arithmetic and never exceeding the maximum supply.

The unit statements **1 BTC = 1 BRBN** and **1 satoshi = 1 Rubini** are nominal accounting definitions only. They do not imply market value, BTC backing, redemption rights, or guaranteed exchange value. One Rubini is 10^-8 BRBN.

## Issuance concept under development

The current proposal counts positive BTC values in qualifying unspendable OP_RETURN outputs only from an officially designated BITRUBIN launch block onward. Earlier Bitcoin transactions are not counted retroactively.

The following rules are not yet finalized:
- the official launch block;
- how the recipient of BRBN and Pearls is determined for a transaction whose OP_RETURN output is unspendable;
- whether positive-value OP_RETURN outputs are accepted by Bitcoin Core standardness and relay policy;
- the complete deterministic validation, duplicate-prevention, and reorganization rules.

Until these points are resolved and independently tested, this is a proposal, not a live issuance system.

## Documentation

- [Development status](DEVELOPMENT_STATUS.md)
- [Roadmap](ROADMAP.md)
- [Security notes](SECURITY.md)

## Author

Faycal Hammouti

## Disclaimer

This repository describes an experimental concept. It is not financial advice, an offer, a promise of value, or a claim of production readiness. Token parameters and technical rules may change before any productive deployment.
