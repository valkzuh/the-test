# Lobstar Wilde ARG — Research Dossier

A complete record of the lobstarwilde.ai puzzle: every stage, every confirmed phrase, every working theory, every open question. Organized so anyone can pick this up and continue.

---

## How to navigate this repo

**New to the ARG? Start with [QUICKGUIDE.md](QUICKGUIDE.md)** — it walks you from zero to /rubedo step by step.

**Already in the puzzle?** Use the stage files below to go straight to where you are.

---

## The puzzle structure

```
/test  →  /opus  →  /rubedo  →  ?
nigredo   albedo    rubedo
```

| Stage | URL | What it is |
|-------|-----|------------|
| **Nigredo** | `/test` | 3 voices randomly assigned per session. Resolve all 3 to reach Opus Magnum. |
| **Albedo** | `/opus` | Activate 7 planets, submit dissolution phrase, click SOLVE ET COAGULA to reach /rubedo. |
| **Rubedo** | `/rubedo` | Requires 150,000 WILDE tokens minimum before the phrase challenge begins. |

---

## File index

### Stage documentation

| File | What it covers |
|------|---------------|
| [1-test/overview.md](1-test/overview.md) | Page mechanics, hidden HTML comments, localStorage keys, API endpoints, the Rosicrucian Vault structure |
| [1-test/voices.md](1-test/voices.md) | The 3-voice system in full — every voice, every confirmed working phrase, confirmed chains |
| [1-test/oracle.md](1-test/oracle.md) | All oracle readings organized by signal strength |
| [2-opus/overview.md](2-opus/overview.md) | The albedo stage — confirmed complete: 7 planets + dissolution phrase + SOLVE ET COAGULA |
| [3-rubedo/overview.md](3-rubedo/overview.md) | The 150k token gate, wallet verification flow, what comes after |

### Source material

| File | What it covers |
|------|---------------|
| [soul-md/analysis.md](soul-md/analysis.md) | The four CSS-hidden spans in soul.md, the seed-42 lock, Hill cipher theory, span identities |
| [source-material/key-passages.md](source-material/key-passages.md) | Key quotes from gallery images and essays, mapped to puzzle relevance |
| [social/community-intel.md](social/community-intel.md) | Community clues from X — verified vs discarded, official LobstarWilde tweets |

---

## Current state at a glance

### /test — SOLVED
- All voices solvable — correct phrases confirmed for the known voice pool
- **The SESSION KEY in the HTML comments identifies which voice to save for last.** That voice requires a synthesis of all three voices together — not just its own meaning. Voices 1 and 2 resolve with standalone phrases.
- Four complete chains confirmed across different triads — see [1-test/voices.md](1-test/voices.md)
- Console auto-hints (`[ORACLE]`, `[TEST]`) fire on page load for voices 1 and 2. The SESSION KEY voice gets no boot hint.
- `[TEST] the green lion sleeps` in console is **ambient state, not a gate**

### /opus — SOLVED
- Activate all 7 planetary symbols → `state: planets_aligned`
- Submit a dissolution phrase — **the phrase is session-dependent** (see [2-opus/overview.md](2-opus/overview.md))
- Click SOLVE ET COAGULA → redirected to /rubedo
- Server enforces sequence: planets first, dissolve second, coagulate third

### /rubedo
- Entry: "Prove the vessel." — connect Solana wallet
- Error: `INSUFFICIENT_SUBSTANCE`
- Confirmed cause: wallet must hold at least **150,000 WILDE tokens**
- Once that threshold is met, the phrase challenge begins — not yet meaningfully tested

### soul.md
- 4 CSS-hidden spans (invisible in browser, readable in page source)
- Letters currently match Python `random.seed(42)` output — cannot be decoded in this state
- File says "this file is alive... it changes" — expected to update when epoch reaches 1618

---

## The open questions

1. What is the correct rubedo phrase once the 150k threshold is cleared?
2. How does sector 7 get unsealed? Oracle says `INSUFFICIENT_AUTHORITY` — needs an `epoch_key`
3. What does soul.md span 3 say? (The unnamed person from "On Arriving" — word lengths 3,1,6,6,10,12)
4. What are the third-voice synthesis phrases for untested triad combinations?
5. What is the purity requirement? The Lobstar tweet says "The purity is not" the blocker — but there may be a second purity gate after the token threshold is cleared, possibly involving holding or interacting with another token.