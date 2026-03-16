# DIGau Early Holder Link Analysis

## Objective

Identify which early DIGAU receivers can be linked to:

- the later `Primary / BOS` distribution structure
- the current frozen client subset
- the exchange-linked staging cluster

This note is based on the DIGAU token transfer history since May 07, 2021:

## Main Conclusion

The data supports a two-layer interpretation:

- `0x5434bb2510bb142774e37a0a2855d04291525f04` is the strongest `genesis-era / founder-side` major receiver found in the supplied DIGAU transfer exports.
- `0x4f7908fcacf7ac0e69d7981621fa60bc29285108` is the later `operational Primary / distributor` for the BOS structure.

The strongest early-holder bridge into the later BOS chain is:

`0x5434bb2510bb142774e37a0a2855d04291525f04 -> 0x2652d18675cad0177f5dd04fdbf2afd1f61a8615 -> 0x68a548bc9a4eac90ac0c70bbf2382115256e5825 -> 0x827ca2bb1fe71846a8704e2e8026435b6a414384 -> 0x4f7908fcacf7ac0e69d7981621fa60bc29285108 -> 0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b`

That path is chronologically valid, but the first step is weak in size:

- `0x5434bb2510bb142774e37a0a2855d04291525f04` sent only `20,000 DIGAU` total to `0x2652d18675cad0177f5dd04fdbf2afd1f61a8615`

So this is evidence of a connection, but not strong evidence that `0x5434bb2510bb142774e37a0a2855d04291525f04` directly established the later BOS chain.

## Genesis-Era Major Receiver

The strongest early receiver identified is:

`0x5434bb2510bb142774e37a0a2855d04291525f04`

Initial establishment:

- `2021-05-16 21:47:13 UTC`
- `0x2F610E3911574b936CEa704354158bf21bA62c3B -> 0x5434bb2510bb142774e37a0a2855d04291525f04`
- `100 DIGAU`

Main funding:

- `2021-05-16 21:52:32 UTC`
- `0x2F610E3911574b936CEa704354158bf21bA62c3B -> 0x5434bb2510bb142774e37a0a2855d04291525f04`
- `999,999,900 DIGAU`

Total initial treasury funding:

- `1,000,000,000 DIGAU`

This makes `0x5434bb2510bb142774e37a0a2855d04291525f04` the strongest founder-side large wallet in the supplied ERC-20 data.

## Later Operational BOS Structure

The later BOS chain identified in the current investigation remains:

`0x2F610E3911574b936CEa704354158bf21bA62c3B -> 0xf9060d7ff8b9542da73602401adc550e694fd41c / 0x68a548bc9a4eac90ac0c70bbf2382115256e5825 -> 0x827ca2bb1fe71846a8704e2e8026435b6a414384 -> 0x4f7908fcacf7ac0e69d7981621fa60bc29285108 -> 0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b -> frozen client wallets`

Key role interpretation:

- `0x4f7908fcacf7ac0e69d7981621fa60bc29285108` = later operational `Primary / distributor`
- `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b` = strongest `Secondary / BOS`

Important timing point:

- `0x4f7908fcacf7ac0e69d7981621fa60bc29285108` first appears only on `2025-06-25 08:25:35 UTC`

That means it is not a genesis-era wallet in the supplied DIGAU transfer exports.

## Early Wallets With Meaningful BOS Relevance

### 1. `0x5434bb2510bb142774e37a0a2855d04291525f04`

Status:

- strongest founder-side early receiver
- no direct transfers to the current frozen-client subset in the supplied file
- indirect chronological path into the later BOS chain exists

Evidence:

- funded by treasury with `1,000,000,000 DIGAU` on `2021-05-16`
- later sends `20,000 DIGAU` total to `0x2652d18675cad0177f5dd04fdbf2afd1f61a8615`

Assessment:

- strong early-root wallet
- indirect BOS linkage present
- direct BOS establishment not proven

### 2. `0x2652d18675cad0177f5dd04fdbf2afd1f61a8615`

Status:

- strongest newly confirmed early bridge into the later BOS chain

Evidence:

- first inbound: `2021-10-27 21:21:53 UTC`
- first source: `0x5434bb2510bb142774e37a0a2855d04291525f04`
- first amount: `1,000 DIGAU`
- total inbound: `7,161,450.1221011 DIGAU`
- total outbound: `7,161,450.1221011 DIGAU`

Critical downstream link:

- `2023-09-21 04:06:23 UTC`
- `0x2652d18675cad0177f5dd04fdbf2afd1f61a8615 -> 0x68a548bc9a4eac90ac0c70bbf2382115256e5825`
- `4,780,808.1221011 DIGAU`

Assessment:

- meaningful early-to-BOS bridge
- more relevant than many other large 2021 holders

### 3. `0x68a548bc9a4eac90ac0c70bbf2382115256e5825`

Status:

- major upstream BOS bridge

Evidence:

- first inbound: `2023-09-21 04:06:23 UTC`
- first source: `0x2652d18675cad0177f5dd04fdbf2afd1f61a8615`
- total inbound: `204,999,548.5161011 DIGAU`
- total outbound: `204,999,548.5161011 DIGAU`

Critical BOS link:

- `0x68a548bc9a4eac90ac0c70bbf2382115256e5825 -> 0x827ca2bb1fe71846a8704e2e8026435b6a414384`
- `50,000,025 DIGAU`
- across `3` transfers between `2024-11-13` and `2024-11-14`

Assessment:

- important BOS feeder wallet
- clearly part of the later operational structure

### 4. `0xf9060d7ff8b9542da73602401adc550e694fd41c`

Status:

- parallel BOS feeder wallet

Evidence:

- first inbound: `2023-02-15 02:27:23 UTC`
- first source: `0x2F610E3911574b936CEa704354158bf21bA62c3B`
- first amount: `10 DIGAU`
- total inbound: `1,021,000,100 DIGAU`
- total outbound: `983,001,100 DIGAU`

Critical BOS link:

- `0xf9060d7ff8b9542da73602401adc550e694fd41c -> 0x827ca2bb1fe71846a8704e2e8026435b6a414384`
- `63,000,000 DIGAU`
- on `2024-11-20`

Assessment:

- major BOS feeder
- not a 2021 early-holder wallet

### 5. `0x03ae24d5675f4d09e89528c47aeabf9900e6a9a8`

Status:

- early-cluster wallet worth watching
- not yet proven as a causal BOS bridge

Evidence:

- first inbound from `0x5434bb2510bb142774e37a0a2855d04291525f04` on `2021-05-25 21:54:18 UTC`
- total inbound from `0x5434bb2510bb142774e37a0a2855d04291525f04`: `21,200,000 DIGAU`

Later link:

- `2025-09-10 01:59:47 UTC`
- `0x03ae24d5675f4d09e89528c47aeabf9900e6a9a8 -> 0xf9060d7ff8b9542da73602401adc550e694fd41c`
- `100,000,000 DIGAU`

Why this is weaker than it looks:

- `0xf9060d7ff8b9542da73602401adc550e694fd41c` had already funded `0x827ca2bb1fe71846a8704e2e8026435b6a414384` in `2024`
- so this `2025` transfer does not establish the original BOS path

Assessment:

- cluster-linked
- not yet strong enough to classify as a BOS root

## Early Wallets That Currently Look Weak

These large or notable early receivers did not show a meaningful direct or chronological path into the later BOS chain in the supplied DIGAU exports:

- `0xe68b4926a4ff44a99fc73f49807b3a15a4e3abd2`
- `0x2d8023230653195994810560a500522f65d2a3f5`
- `0x5e7dec1636a5554279684d2a94c4822b4d79175d`

Current reading:

- they are real early DIGAU receivers
- but the supplied exports do not currently support them as strong BOS roots

## Links To Frozen Wallets

Using the current frozen-client subset file:

- `0x4f7908fcacf7ac0e69d7981621fa60bc29285108` directly funded `135` unique frozen-client wallets across `400` transfers
- `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b` directly funded `87` unique frozen-client wallets across `114` transfers

In the supplied DIGAU yearly exports, I did **not** find direct transfers from these earlier wallets into that current frozen-client subset:

- `0x5434bb2510bb142774e37a0a2855d04291525f04`
- `0x2652d18675cad0177f5dd04fdbf2afd1f61a8615`
- `0x68a548bc9a4eac90ac0c70bbf2382115256e5825`
- `0xf9060d7ff8b9542da73602401adc550e694fd41c`
- `0x827ca2bb1fe71846a8704e2e8026435b6a414384`

That means direct frozen-client funding starts later in the chain, mainly at:

- `0x4f7908fcacf7ac0e69d7981621fa60bc29285108`
- `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b`

## Links To Exchange-Related Wallets

Known exchange-linked staging cluster from the earlier notes:

- `0x0e747eb2ff0f26fb77c3a1ea67ee07fac2dbb783`
- `0xD96342BAB6d87b9DcA847Ba51BFe54C34A5ABC6F`
- `0x6c8c3154450722ea6550f2c537ef6f2695e7c4c0`

Known XT deposit or exchange-related wallets from the notes:

- `0x14c33c9c95a1dde33ff2b66fa398658a47e929d4`
- `0x4a4adac8c995d36a152a4debc5c5f151eaa6dfdd`
- `0xda08cd5c8dafdb2cbabd61ed33eca14ac361f5e7`
- `0x46fdbee1327536a10a517810963c4f3ba555c642`
- `0x713c37a2e23dd51a7ede30e4ab0830fbc31c9359`
- `0xdb3ded7731c781224ec292e2163d9554c094fd7c`

Direct exchange-related touch found in the supplied DIGAU yearly exports:

- `2025-06-11 04:25:11 UTC`
- `0x5434bb2510bb142774e37a0a2855d04291525f04 -> 0x6c8c3154450722ea6550f2c537ef6f2695e7c4c0`
- `10 DIGAU`

Interpretation:

- this is a real touchpoint between the founder-side wallet and the later exchange-linked staging cluster
- but the amount is too small to treat as strong sell-pressure evidence by itself

## Best Current Watchlist

If the goal is to find early receivers that matter for BOS / exchange analysis, the best watchlist from the supplied data is:

1. `0x5434bb2510bb142774e37a0a2855d04291525f04`
2. `0x2652d18675cad0177f5dd04fdbf2afd1f61a8615`
3. `0x68a548bc9a4eac90ac0c70bbf2382115256e5825`
4. `0xf9060d7ff8b9542da73602401adc550e694fd41c`
5. `0x827ca2bb1fe71846a8704e2e8026435b6a414384`
6. `0x4f7908fcacf7ac0e69d7981621fa60bc29285108`
7. `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b`

## Practical Conclusion

The supplied DIGAU yearly exports do not support the idea that most early holders directly funded the current frozen-client subset or directly deposited into exchange wallets.

What they do support is:

- a strong founder-side early receiver at `0x5434bb2510bb142774e37a0a2855d04291525f04`
- a real but weak indirect bridge from that early cluster into the later BOS path
- a clearer later operational BOS structure centered on:
  - `0x68a548bc9a4eac90ac0c70bbf2382115256e5825`
  - `0xf9060d7ff8b9542da73602401adc550e694fd41c`
  - `0x827ca2bb1fe71846a8704e2e8026435b6a414384`
  - `0x4f7908fcacf7ac0e69d7981621fa60bc29285108`
  - `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b`

So the current best read is:

- `0x5434bb2510bb142774e37a0a2855d04291525f04` = strongest founder-side root candidate
- `0x4f7908fcacf7ac0e69d7981621fa60bc29285108` = later operational Primary
- `0x6D41C323b9BE23A6c4f6889F4FA9ED9d05E0ae5b` = strongest BOS / Secondary
