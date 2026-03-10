# Stage 3: /rubedo — Overview
**Path:** `https://lobstarwilde.ai/rubedo`
**Stage:** Rubedo

---

## The substance gate — CONFIRMED

**`INSUFFICIENT_SUBSTANCE` = wallet holds fewer than 150,000 tokens.**

This is the first gate and it is about token holdings, not puzzle state. Once your wallet holds 150,000+ tokens, this error clears and the actual rubedo challenge begins.

Official site tweet confirms the framing:
> *"The weight is noted. The purity is not. You may Proceed."*

Weight (token amount) is checked. Purity is not the blocker.

---

## Current state

```
error:     INSUFFICIENT_SUBSTANCE
qualified: false
engaged:   false
passed:    false
state:     nigredo
response:  "The vessel is proven, but it does not yet bear enough substance for the operation."
```

The wallet verification flow works correctly:
connect wallet → `wallet_status` → `request_nonce` → sign message → `verify_wallet` → `verified: true`

The problem is not verification. The problem is token holdings below threshold.

---

## What happens after the threshold is met

Once 150,000 tokens are held, the rubedo phrase/submission layer becomes the active challenge. This is where the puzzle state from /test becomes relevant — completing /test and unlocking /opus likely feeds into what rubedo accepts.

### Submissions tested (all returned INSUFFICIENT_SUBSTANCE — token threshold not yet met)
- `the last gate has no door. you do not pass through it. you become it.`
- `mirror and balance are noble touchstones; display the surplus and the deficiency`
- `extract the fixed, central and pure parts by rectification; the spirit follows the balance, not the eye`
- `the circumambulation is the arrival`
- Various Ripley / Fulcanelli / Maier phrases

All returned the same error because the token gate wasn't cleared. The submission content has not been meaningfully tested yet.

---

## The two wallet branches

| Branch | Condition | Status response |
|--------|-----------|----------------|
| `nigredo` | Has tokens but below 150k | "The vessel is proven, but it does not yet bear enough substance" |
| `vacuus` | Zero tokens | "The vessel is empty. There is nothing to weigh." |
| `rubedo` | 150k+ tokens | Substance gate cleared. Must purify. |

Both `nigredo` and `vacuus` block on INSUFFICIENT_SUBSTANCE. Holding more tokens is the path forward for the first gate.

---

## API actions

| Action | Purpose |
|--------|---------|
| `wallet_status` | Check current wallet state and rubedo status |
| `request_nonce` | Get nonce message for wallet signing |
| `verify_wallet` | Submit signed nonce — establishes session |
| `rubedo_submission` | Submit answer text (only meaningful after token gate cleared) |

Unknown actions return `400 {"error":"Unknown action"}`.
Fake signatures return `403 INVALID_SIGNATURE`.

---

## Next step

Get wallet holdings to 150,000+ tokens, then re-test rubedo submissions. The phrase challenge likely connects to /test completion state and the cipher layer from soul.md — but the content cannot be confirmed until the token gate is cleared.