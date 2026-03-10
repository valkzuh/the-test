# QUICKGUIDE — From Zero to /rubedo

A step-by-step walkthrough of the lobstarwilde.ai ARG, starting from nothing. This covers /test, /opus, and the path to /rubedo.

---

## Step 1 — Find the site and read everything

Go to **lobstarwilde.ai**.

Read the main page, then navigate to:
- `/gallery` — alchemical images with annotations
- `/essays` — Lobstar's own writing
- `/soul.md` — Lobstar's self-description document (key puzzle resource)

Take your time with these. The puzzle is built entirely out of what Lobstar has written and curated. The source material is the key.

---

## Step 2 — View page source on /soul.md

Before continuing, do this:

1. Go to `lobstarwilde.ai/soul.md`
2. Right-click → View Page Source (or Ctrl+U)
3. Search for `redacted` in the source

You will find four `<span class="redacted">` elements. In the browser they appear blank — but in the source, the letters are there. The CSS hides them with `color: transparent`. These are the four ciphers. They cannot be decoded yet (the puzzle state is locked), but note their existence.

---

## Step 3 — Navigate to /test

Go to `lobstarwilde.ai/test`.

This is the first puzzle stage: **Nigredo**.

Do this immediately:
1. Right-click → View Page Source
2. Read all the HTML comments at the top. They tell you:
   - Your current **SESSION TRIAD** — the 3 voices assigned to your session
   - The **SESSION KEY** — a hint phrase identifying one of your voices
   - The current epoch (1617) and what's blocked (sector 7)
   - A critical instruction: **`do not quote. synthesize.`**

Your session triad changes every time you get a new session cookie. The three voices shown are the three you need to resolve.

---

## Step 4 — Understand the 3-voice system

The /test puzzle works like this:

- Each session has **3 voices** randomly drawn from a pool of alchemical/philosophical sources
- You must submit the **synthesized meaning** of each voice — not a direct quote
- Each correct submission decrements the count: "2 voices remain unresolved" → "1 voice remains" → Opus Magnum
- The instruction *"do not quote. synthesize."* is literal — the server wants the essence, not the line

See [1-test/voices.md](1-test/voices.md) for every voice in the pool, confirmed working phrases, and near-miss response patterns.

---

## Step 5 — Identify your SESSION KEY voice and order

**This is the most important step.** Read the SESSION KEY in the HTML comments. Find which voice in your SESSION TRIAD it corresponds to — that voice gets solved **last**.

The SESSION KEY voice cannot be answered with its standalone phrase alone. When you submit it, you must synthesize what **all three voices together** are describing as a single unified operation.

---

## Step 6 — Resolve your 3 voices

**Open DevTools console before doing anything.** Console hints (`[ORACLE]` and `[TEST]` tags) fire at page load for the first two voices. Read them — they are the synthesis directions.

**The order:**
1. Resolve the two non-KEY voices using their standalone phrases
2. Resolve the SESSION KEY voice last, with a phrase that describes what all three voices do together

**Confirmed standalone phrases:**

| Voice | Submit this |
|-------|-------------|
| Tabula Smaragdina | `what is below answers what is above` |
| Tabula Smaragdina | `borne by wind nursed by earth` |
| George Ripley | `in the sea withouten lees standeth the bird of hermes eating his wings to make himself full stable` |
| Maria Prophetissa | `one becomes two two becomes three out of the third comes the one as the fourth` |
| Basil Valentine / VITRIOL | `visit the interior of the earth and by rectifying find the hidden stone` |
| Zosimos | `I was swallowed and consumed and transformed` |
| Aurora Consurgens | `the gardener saw his own form in the water and loved it` |
| Turba Philosophorum | `the stone is common and precious` |
| Rosarium Philosophorum | `circle square triangle circle` |

**Confirmed third-voice synthesis phrases (SESSION KEY voice, submitted last):**

| Session triad (KEY voice in bold) | Third-voice synthesis |
|-----------------------------------|-----------------------|
| Ripley + Maria + **VITRIOL** | `the descent through the three returns the one as the stone` |
| Ripley + Aurora + **Turba** | `it stands as a stone after eating and nobody sought it because it was always there` |
| Maria + Aurora + **Zosimos** (or similar water triad) | `what is seen in water and swallowed returns as the one as the fourth` |
| Any + Any + **Tabula** | `borne by wind nursed by earth` |

For untested combinations: identify what single operation all three voices describe together and compress it into one phrase. Near-miss server responses will guide you — each one tells you which voice area you're close to.

---

## Step 7 — Solve /opus (the albedo stage)

After completing /test, navigate to `/opus` with the same session active.

**Step 7a — Activate all 7 planets**

The page shows 7 classical planetary symbols. Click every one until all are activated. The stream confirms `state: planets_aligned` when all 7 are lit. The 7 planets: Jupiter, Saturn, Mars, Sol, Venus, Mercury, Luna.

**Step 7b — Submit the dissolution phrase**

The dissolution phrase at /opus is **session-dependent** — it reflects the dominant element of your /test triad. Confirmed phrases:

| When your /test triad was... | Submit this |
|------------------------------|-------------|
| Descent/earth dominant (VITRIOL, Ripley) | `I dissolve before I can be fixed` |
| Water/immersion dominant (Aurora, Zosimos) | `I am made water before I am made stone` |
| Cycle/number dominant (Maria, Tabula, Ripley) | `I become two I become three out of the third I am the fourth` |

If your phrase fails, look at the dominant operation in your /test voices and frame a first-person dissolution statement around it.

Response when correct: *"What you brought here has already begun to change. Whether you notice is not the furnace's concern."* — `albedo_complete: true`

**Step 7c — Click SOLVE ET COAGULA**

The text SOLVE ET COAGULA appears at the bottom of the page. Click it. You are redirected to /rubedo.

**Important:** The server enforces the alchemical order. Planets must be aligned first, then dissolve, then coagulate. Submitting out of order returns an error.

See [2-opus/overview.md](2-opus/overview.md) for full mechanics and all observed responses.

---

## Step 8 — Reach /rubedo

After clicking SOLVE ET COAGULA from /opus, you arrive at `/rubedo`. The page shows **"Prove the vessel."** with a wallet connect button (☉).

Connect your Solana wallet. The site runs a verification flow:
1. `wallet_status` — checks your holdings
2. `request_nonce` — issues a message to sign
3. Sign the message with your wallet
4. `verify_wallet` — confirms your identity

| State | Meaning |
|-------|---------|
| `"The vessel is proven, but it does not yet bear enough substance"` | Wallet verified, but holdings below 150k |
| `"The vessel is empty. There is nothing to weigh."` | Wallet holds zero tokens |
| *(no error)* | Substance gate cleared — phrase challenge begins |

---

## Step 9 — The 150,000 token gate

`INSUFFICIENT_SUBSTANCE` = your wallet holds fewer than **150,000 WILDE tokens**.

Lobstar's own tweet confirms: *"The weight is noted. The purity is not. You may Proceed."* — token amount is what's checked. Purity is not the blocker.

**What you need:** 150,000+ WILDE tokens in the connected Solana wallet.

Once that threshold is met, the INSUFFICIENT_SUBSTANCE error clears and the actual rubedo phrase challenge begins. See [3-rubedo/overview.md](3-rubedo/overview.md) for everything known about what comes next. 

---

## Where this research stands

Everything through /opus is fully solved. The rubedo phrase challenge has not yet been meaningfully tested — the 150k token threshold has been the wall. Clearing it is the next frontier.

Start at [README.md](README.md) for a full map of the research.

**Open question — purity:** Lobstar's tweet says "The purity is not" the current blocker, but a purity gate may exist further in once the token threshold is cleared. What purity means in practice is still unknown.