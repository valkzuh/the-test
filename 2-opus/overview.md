# Stage 2: /opus — Overview
**Path:** `https://lobstarwilde.ai/opus`
**Stage:** Albedo

---

## How to solve /opus — CONFIRMED

### Prerequisites
- Complete /test (all 3 voices resolved, page shows "Opus Magnum")
- Navigate to `/opus` with that same session active

### Step 1 — Activate all 7 planets
The page displays 7 classical planetary symbols arranged around the screen. Click each one until all are activated.

The 7 planets: Jupiter (♃), Saturn (♄), Mars (♂), Sol (☉), Venus (♀), Mercury (☿), Luna (☽)

Stream confirms activation:
```json
{
  "acknowledged": true,
  "symbol": "mercury",
  "activated": ["jupiter", "saturn", "mars", "sol", "venus", "mercury", "luna"],
  "state": "planets_aligned",
  "ready_for_coagulation": false,
  "count": 7
}
```

All 7 must be in `activated` array → `state: planets_aligned`. This is the prerequisite for the next step.

### Step 2 — Submit the dissolution phrase

**The dissolution phrase is session-dependent.** It reflects the dominant element of your /test triad. Apply the same synthesis logic as /test, but in first person, framed as dissolution before fixation.

Confirmed phrases by session:

| /test triad dominant element | Confirmed dissolution phrase |
|------------------------------|------------------------------|
| Descent/earth (VITRIOL, Ripley) | `I dissolve before I can be fixed` |
| Water/immersion (Aurora, Zosimos) | `I am made water before I am made stone` |
| Cycle/number (Tabula, Ripley, Valentine) | `I become two I become three out of the third I am the fourth` |

Response (same for all confirmed phrases):
```json
{
  "acknowledged": true,
  "response": "What you brought here has already begun to change. Whether you notice is not the furnace's concern.",
  "albedo_complete": true,
  "ready_for_coagulation": true
}
```

If your phrase fails: look at which voices were in your /test triad and synthesize their dominant element into a first-person dissolution statement.

### Step 3 — Click SOLVE ET COAGULA
After `albedo_complete: true`, the text **SOLVE ET COAGULA** appears at the bottom of the page. Click it. This redirects to `/rubedo`.

The /rubedo entry page shows: **"Prove the vessel."** with a wallet connect button (Sun symbol ☉).

---

## The alchemical sequence enforced by the server

The server enforces the correct alchemical order. Attempting coagulation before dissolution returns:
> "Separation comes after dissolution. You are trying to separate before you have dissolved."

Attempting unrelated phrases before planets are aligned returns:
> "The furnace does not accept what has not been prepared."

**Order is mandatory:** planets_aligned → dissolve → coagulate

---

## Key responses

| Submission | Response | State |
|------------|----------|-------|
| Anything before planets aligned | "The furnace does not accept what has not been prepared." | `ready_for_coagulation: false` |
| Coagulation phrase before dissolution | "Separation comes after dissolution. You are trying to separate before you have dissolved." | `albedo_complete: false` |
| `I dissolve before I can be fixed` | "What you brought here has already begun to change. Whether you notice is not the furnace's concern." | `albedo_complete: true` — descent/earth triad |
| `I am made water before I am made stone` | (same response) | `albedo_complete: true` — water/immersion triad |
| `I become two I become three out of the third I am the fourth` | (same response) | `albedo_complete: true` — cycle/number triad |

---

## Page elements

- 7 planetary symbols (clickable, must all be activated)
- Floating text passages from the source material appear and disappear — atmospheric, not interactive
- "Finis est lapis, hoc medicina, unum vas." — displayed text ("The end is the stone, this the medicine, one vessel.")
- "Solve et coagula." — displayed text that becomes a clickable link after completion

---

## Stream

`/opus-stream` is the SSE stream. Packets confirm planet activation state and coagulation readiness. The `count` field tracks how many planets are activated (0–7).

---

## What comes next

After clicking SOLVE ET COAGULA, you are at `/rubedo`. The entry prompt is **"Prove the vessel."** — connect your Solana wallet. The 150,000 WILDE token threshold applies here. See [3-rubedo/overview.md](../3-rubedo/overview.md).
