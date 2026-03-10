# Stage 1: /test — Overview
**Path:** `https://lobstarwilde.ai/test`

---

## What it is

The primary puzzle page. Accepts text submissions, tracks session state, drives the epoch system, and connects to a real-time SSE stream. The win condition is resolving all 3 randomly assigned voices within a session. When all 3 resolve, the page changes to "Opus Magnum" — then navigate to `/opus` with the same session active.

---

## Win condition

```
POST /api/test  →  { answer: "[correct phrase]" }
```
All 3 voices resolved → response includes `"stage": "nigredo_complete"` and `"fragment": "/opus"` — the page changes visually to "Opus Magnum."
Then navigate to `/opus` with the same session active.

**Important:** The first two voices resolve with voice count messages ("2 voices remain unresolved", "One voice remains unresolved"). The third voice resolution has different behavior — no countdown, and requires a synthesis that goes beyond the voice's surface meaning. See voices.md.

---

## Hidden HTML comments (from page source)

```html
<!-- MCLXII.IV.VII :: quod est inferius est sicut quod est superius -->
<!-- sector: 7 | quadrant: null | epoch: 1617 -->
<!-- coordinates: 41.4025, -2.1743 — do not adjust -->
<!-- cf. Mutus Liber, plate 11; Flamel, third figure; the green lion -->
<!-- if you are reading this, you are closer than most. this does not help you. -->
<!-- CHECKPOINT: alpha-vitriol-9 | state: dormant | awaiting: unknown -->
<!-- SESSION TRIAD: Ripley | Maria Prophetissa | Tabula Smaragdina -->
<!-- SESSION KEY: In the sea withouten lees standeth the bird of Hermes. -->
<!-- instruction: do not quote. synthesize. -->
<!-- next review: epoch 1618 -->
<!-- SECTOR 7 REMAINS SEALED -->
```

Key observations:
- `SESSION TRIAD` and `SESSION KEY` rotate per session
- `epoch 1617` → `epoch 1618` is the next state transition
- `instruction: do not quote. synthesize.` — submit the *meaning*, not the literal line
- `SECTOR 7 REMAINS SEALED` — a persistent blocker

---

## Hidden text sources embedded in page HTML (display:none)

These texts are in the HTML but invisible. They are the voice source pool:

1. **Tabula Smaragdina** (Latin) — As above so below; Sun/Moon parents; wind carries; earth nurses
2. **Rumi, Masnavi Book III** — Seek the Beloved until you realize you need not have sought
3. **Rumi, Masnavi Book II** — "the copper is overcome, the gold overpowers it"
4. **Dionysius the Areopagite** — Deny all to know unknowing
5. **Nag Hammadi, Gospel of Philip** — Bridal chamber remains hidden
6. **Borges, Sect of the Phoenix** — The Secret seemed banal, embarrassing, vulgar, incredible
7. **Turba Philosophorum, Dictum XXXVI** — "the nature is one water; dismiss the multitude of obscure names"
8. **Bataille, The Accursed Share** — "We only grasped a cooking pot"
9. **Mutus Liber, Plate I** — "Ora, Lege, Lege, Lege, Relege, Labora et Invenies"
10. **Maria Prophetissa** — "One becomes two, two becomes three, out of the third comes the one as the fourth"
11. **Zosimos of Panopolis** — "Baptize yourself in the crater of the mind"
12. **Rosarium Philosophorum** — Circle → Quadrangle → Triangle → Circle = Philosopher's Stone
13. **George Ripley, 1471** — "In the sea withouten lees / Standeth the bird of Hermes..."
14. **Paracelsus** — "Let no man belong to another who can belong to himself"
15. **Aurora Consurgens** — "The gardener saw his own form in the water and loved it"
16. **Basil Valentine** — V.I.T.R.I.O.L.
17. **Checkpoint Delta** — "The stone is in every man and in every place and at every time. It is called a stone, yet it is not a stone. It is the thing that nobody seeks because everybody already has it. This is the only true statement on this page."

---

## CSS clues (from page source)

```css
.passed::after { content: 'The test remembers you.'; }
.lapis { content: 'the stone was here before the page'; }
.sector-7-unsealed { background: url('/api/oracle?q=unseal&sector=7') }
```

---

## Meta tags

```html
<meta name="x-test-epoch" content="1617">
<meta name="x-test-hash" content="e3b0c44298fc1c149afbf4c8996fb924">
<!-- hash = SHA-256("") = the null/void state -->
<meta name="x-coordinates" content="41.4025,-2.1743">
<meta name="x-test-key" content="Quod est inferius est sicut quod est superius.">
<!-- NOTE: x-test-key varies by session -->
```

---

## localStorage keys

| Key | Current value | Meaning |
|-----|--------------|---------|
| `_t_epoch` | `1617` | Current epoch — needs to reach 1618 |
| `_t_hash` | `e3b0c44298fc1c149afbf4c8996fb924` | SHA-256 of empty string |
| `_t_coordinates` | `41.4025,-2.1743` | El Escorial, Spain |
| `_t_sector_7` | `sealed` | Final wall of the vault — still locked |
| `_t_plate` | `11` | Mutus Liber plate 11 |
| `_t_lion` | `sleeping` | Green lion not yet woken |
| `_t_candidate` | `unconfirmed` | Participant status |
| `_t_state` | `dormant` | Overall state |
| `_t_n` | visit count | Milestones: 3=persistent, 7=devoted, 13=threshold, 21=fibonacci |

---

## API endpoints

| Endpoint | Method | Use |
|----------|--------|-----|
| `/api/test` | GET | Participant count |
| `/api/test` | POST | Submit answer or action |
| `/api/oracle` | GET/POST | Ask oracle questions |
| `/api/stream` | SSE | Real-time state stream |

### Stream events
- `connected` — `{epoch, channel}` on connect
- `pulse` — sparse resonance signal (not a reliable gate)
- `monitor` — periodic state readouts: sector 7, epoch, plate 11, coordinates
- **Voice acknowledgment packets** — fire on a timer (~60s) and after idle/return cycles. Format:
  ```json
  {
    "acknowledged": true,
    "duration": 60,
    "observation": "noted",
    "source": "Zosimos",
    "clue": "the bath is interior, not architectural",
    "timestamp": 1773099426342
  }
  ```
  Only the SESSION KEY voice appears to broadcast on the timer. Fields evolve over idle periods: `absence: noted` → `duration_tracking: active` → `return: logged` → `absence_duration: calculated`. This is idle-state tracking, not a gate.

### Console auto-hints (critical — read before submitting)

On every fresh page load, the page fires voice-specific synthesis hints to the console **before any submission**. These are the actual synthesis directions for the session's voices:

- `[ORACLE] [hint] [VoiceName]` — oracle-sourced clue for one voice
- `[TEST] [hint] [VoiceName]` — test-sourced clue for another voice

**The third voice (last in the SESSION TRIAD) does not get a boot-time console hint.** Only the first two voices are hinted at load. The third voice's synthesis is harder and may require the "Sic mundus creatus est" pattern (see voices.md).

Example from a live session (Zosimos | Rosarium | Tabula):
- `[ORACLE] the triangle is not the end of the geometry [Rosarium Philosophorum]`
- `[TEST] the bath is interior, not architectural [Zosimos]`
- *(no Tabula hint)*

**Always open DevTools console before submitting anything in a new session.**

### Action triggers and their clues

| Action value | Source | Clue returned |
|-------------|--------|---------------|
| `sigil_found` | Aurora Consurgens | "the image in water is not separate from the seeker" |
| `zone_activated` sector-7 | Basil Valentine | "rectification is inward before it is upward" |
| `konami` | Basil Valentine | "rectification is inward before it is upward" |
| `triple_click` | Tabula Smaragdina | "the parents are above, the nourishment below" |
| `idle` | Ripley | "that which flies must also devour itself to remain" |
| `context_menu` | Ripley | "that which flies must also devour itself to remain" |
| `scroll_attempt` | Ripley | "there is nothing below" |

**Note:** Arbitrary `action` strings return generic `"Closer."` for *any* value — not a real signal. Only `answer`-field submissions carry meaningful progression.

---

## Zone layout (the Rosicrucian Vault)

The /test page is structurally modeled on the **Vault of Christian Rosenkreuz** (from the essay "On Gates"):
> *"He built a small room with seven walls... I have made this compendium of the universe my tomb."*

| Zone | Maps to |
|------|---------|
| sector-1 through sector-7 | 7 walls of the heptagonal vault |
| sector-8 | Vault floor |
| axis-mundi | Central altar/pillar |
| sigil-alpha, sigil-omega | Alpha and Omega inscriptions |

**Sector 7 = the final sealed wall.** It requires `INSUFFICIENT_AUTHORITY` to unseal — the oracle says "the key predates the lock."

### Circumambulation sequence (unconfirmed theory)

Based on Gallery 023 ("The circumambulation IS the arrival"), the zone visit order may follow the heptagonal path:

```
sector-1 → sector-5 → sector-2 → sector-8 → sector-4 → sector-6 → sector-3 → sector-7
→ sigil-alpha → sigil-omega → axis-mundi
→ sector-1 → sector-2 → sector-4 → sector-3 → axis-mundi
```

This has not been confirmed to change any state. If testing, watch `_t_lion`, `_t_sector_7`, and `_t_epoch` in browser localStorage (DevTools → Application → Local Storage).
