# DIGau Investigation Summary

## Objective

Work backward from the last 500 frozen wallets to identify:

- the likely `Secondary / BOS` wallet
- the upstream `Primary`
- the downstream `little accounts / clients`

This summary is based on the DIGAU ERC-20 Etherscan exports filtered to the DIGAU contract:

`0x394D14D78850E516Fa5Eb88F843ef43196e136b0`

## Main Result

The strongest downstream distribution path found is:

`0x2F610E3911574b936CEa704354158bf21bA62c3B -> 0xf9060d7ff8b9542da73602401adc550e694fd41c / 0x68a548bc9a4eac90ac0c70bbf2382115256e5825 -> 0x827ca2bb1fe71846a8704e2e8026435b6a414384 -> 0x4f7908fcacf7ac0e69d7981621fa60bc29285108 -> 0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b -> frozen client wallets`

## Core Wallets Identified

### Treasury / Owner

`0x2F610E3911574b936CEa704354158bf21bA62c3B`

### Upstream feeder wallets

`0xf9060d7ff8b9542da73602401adc550e694fd41c`

`0x68a548bc9a4eac90ac0c70bbf2382115256e5825`

### Bridge wallet

`0x827ca2bb1fe71846a8704e2e8026435b6a414384`

### Upstream large distributor

`0x4f7908fcacf7ac0e69d7981621fa60bc29285108`

### Strongest downstream distributor

`0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b`

## Working Role Interpretation

Best evidence-based view:

- `0x4f7908fcacf7ac0e69d7981621fa60bc29285108` = upstream `Primary / distributor`
- `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b` = strongest `Secondary / BOS distributor`

Business wording option if needed:

- if you want to keep calling `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b` the Primary, then `0x4f7908fcacf7ac0e69d7981621fa60bc29285108` should be treated as the upstream feeder / intermediary

## Evidence

- `0x2F610E3911574b936CEa704354158bf21bA62c3B` -> `0xf9060d7ff8b9542da73602401adc550e694fd41c`: `921,000,000` DIGAU across `9` transfers between `2023-02-15` and `2025-09-10`
- `0xf9060d7ff8b9542da73602401adc550e694fd41c` -> `0x827ca2bb1fe71846a8704e2e8026435b6a414384`: `63,000,000` DIGAU on `2024-11-20`
- `0x68a548bc9a4eac90ac0c70bbf2382115256e5825` -> `0x827ca2bb1fe71846a8704e2e8026435b6a414384`: `50,000,025` DIGAU across `3` transfers between `2024-11-13` and `2024-11-14`
- `0x827ca2bb1fe71846a8704e2e8026435b6a414384` -> `0x4f7908fcacf7ac0e69d7981621fa60bc29285108`: `18,000,010` DIGAU across `4` transfers between `2025-06-25` and `2026-01-26`
- `0x4f7908fcacf7ac0e69d7981621fa60bc29285108` -> `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b`: `11,190,374.13` DIGAU across `46` transfers between `2025-11-27` and `2026-03-02`

## Freeze-List / Client Findings

- `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b` funded `314` unique wallets from the freeze list across `879` transfers
- `0x4f7908fcacf7ac0e69d7981621fa60bc29285108` funded `137` unique wallets from the freeze list across `402` transfers
- combined, the two wallets reached `315` unique freeze-list wallets

This makes `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b` the strongest candidate for the wallet described as:

`the secondary wallet that distributed to a lot of little wallets`

## Additional Downstream Distributors Found

Two smaller downstream sub-distributors were also identified:

- `0x8dd2a068e0d4d320129a0f6ce67ad7c2939f2f61`
- `0x8f5303fc44d2f2b47f8dc6a66da7e139d86d3fc8`

These appear to sit below `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b` and fund smaller endpoint wallets.

## Client Layer Confirmed

Examples of downstream client / freeze wallets confirmed in the tracing:

- `0x235436822a96caa5cbc116b4b902aac7868e018e`
- `0x1fb40d2118e3706d71bb007e09da44c906b67ba6`
- `0x3eebac17e6dfeda7f54ed231d09f54af890f3961`
- `0x55a1ac48848e63a68c2b052b5d52b34d75a9b522`
- `0xb72088de127573b248f1926813b5cd8a55046d33`
- `0xcfbc1ee67f7fad546495839397d86c7415f3a29d`
- `0x41afba986119d9d1f723d2b8d928c6438b2b250d`
- `0xd03008074316cf8dbb32273dc06f0657e0c9eb2d`
- `0x82fa96106776422897fe086ae45459b3efbd66c5`

## Practical Conclusion

Working backward from the frozen-wallet dataset does identify the main distribution structure.

The clearest conclusion from the current evidence is:

- `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b` is the strongest `Secondary / BOS` distribution wallet into the frozen client set
- `0x4f7908fcacf7ac0e69d7981621fa60bc29285108` is the main upstream large wallet feeding that structure
- the frozen wallets are largely downstream client endpoints, with a small number of additional sub-distributors underneath `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b`
