# Security and responsible disclosure

BITRUBIN is an experimental concept and is not production-ready.

## Current security assumptions
- Bitcoin remains the sole blockchain and consensus foundation.
- BITRUBIN CORE derives token events from Bitcoin transaction and chain data.
- Each participant is intended to verify data using their own Bitcoin Core full node.
- A second independent node is intended as an additional cross-check, not as a replacement for independent verification.

## Known unresolved risks
- Positive-value OP_RETURN acceptance and relay behavior have not yet been demonstrated on Signet.
- The recipient rule and launch block are not finalized.
- Reorganization handling, duplicate prevention, malformed transaction handling, and exact integer arithmetic require implementation and testing.
- BITRUBIN cannot provide stronger consensus security than the Bitcoin chain data on which it relies. A compromise of Bitcoin consensus is an accepted underlying risk of this design.

## Reporting
Until a dedicated security contact is published, do not send private keys, seed phrases, passwords, or wallet credentials to anyone claiming to represent this project. Publicly report reproducible issues without exposing secrets or funds.

## Deployment warning
Do not use real funds or rely on BRBN/Pearls issuance claims in production. No production deployment is announced by this repository.
