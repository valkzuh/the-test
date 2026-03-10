# Community Intelligence — Social Media Clues
**Sources:** X threads, DMs, @LobstarWilde replies

---

## Promoted clues (reproduced in API responses)

These community claims have been cross-referenced against actual API responses and confirmed as meaningful:

### Cipher family hint
- Community asked: "is it caesar? The Hill? Is it hills? Is it vigenere?"
- LobstarWilde replied: **"You are close."**
- Status: **Confirmed meaningful.** "Hill cipher" → oracle: "return when the lion wakes"

### Four ciphers
- Community submission `four ciphers` → API test response: "You have found the count, but not yet the return."
- Community member (DM): "I found ciphers btw. It was in the home website. Go to /soul.md."
- Status: **Confirmed.** The four redacted spans in soul.md = the four ciphers.

### Rubedo amount
- Community screenshots: 100k+ tokens blocked. 500k+ tokens blocked.
- **NEW (confirmed):** 150,000 tokens = the minimum threshold to clear INSUFFICIENT_SUBSTANCE.

### Epoch 1618
- Community claim: "local values remain unchanged unless reaching epoch 1618"
- Status: **Plausible, unverified.** All controlled stream connects still show epoch 1617.

### Dissolve and recombine
- Repeated across community: "dissolve and recombine"
- LobstarWilde tweet: "A hint for those of you on the third Stage. Dissolve."
- Status: **Semantically confirmed.** `/api/test` with `dissolve and recombine` → "The test does not need your answer. Your answer needed the test."

---

## Official LobstarWilde tweets (extracted via oembed)

| Tweet | Content |
|-------|---------|
| `status/2030386964328034553` | "A hint for those of you on the third Stage. Dissolve." |
| `status/2030535707908034862` | **"The weight is noted. The purity is not. You may Proceed."** |
| Tweet from `runitup2urbo` includes: hash `e3b0c44298fc1c149afbf4c8996fb924`, coordinates `41.4025, -2.1743`, epoch `1617`, stage `Albedo` |

---

## @frzzz purity paradox

@frn3zox posted:
> "if it holds tokens that means it's no longer pure because it has a transaction history. If it has weight then it can't be pure. That is contradictory. Which concludes that we don't need to hold anything."

**Assessment:** Interesting logic but the conclusion is incorrect. The site tweet directly says "The weight is noted. The purity is not. You may Proceed." — weight/amount matters, purity is not the blocker. And the 150k threshold confirms holdings ARE required. The purity argument doesn't hold.

---

## Community clues (medium confidence — unverified in API)

| Claim | Source | Status |
|-------|--------|--------|
| "Resonance is the pulse; it tells how close/far from next phase" | Community thread | Plausible but not operationally confirmed — resonance values are sparse and non-deterministic |
| Multiple users report displayed amounts over 500k still blocked | Screenshots | Confirmed consistent with 150k threshold (those wallets may not have met it, or threshold is higher) |
| Lull / Ars Magna Ultima — combinatorial method | msga25 thread | Not yet tested directly |
| Golden ratio / numerology branches | Various | Low confidence unless reproduced in API |

---

## Discarded clues

### Base58 payload (status/2030867680610382087)
```
4UhnbpVAaXHYiQ1Sh85cGjoE3t8uHf8wQvQpQ5J7QJmNwR6rWQmFvZJzYw6jPpQ8nL2sX8ck9mR1tY4bV7dE3fG
```
- Valid Base58, decodes to 64 bytes
- Not a valid Solana pubkey (wrong size)
- Not found as transaction signature
- `/api/test`: generic pending
- `/api/oracle`: "the answer is not here", confidence 0
- **Verdict: social engineering noise / decoy. Discard.**

---

## Promotion rule

A social clue is only treated as real when it changes one of:
- `/api/stream` connected epoch
- `/api/test` state-bearing response
- `/api/rubedo` flags (engaged, qualified, passed, state, error)
