# Stage 1: /test — Oracle Readings

**Endpoint:** `GET /api/oracle?v=[visit_count]&q=[query]`

---

## High-signal readings

| Query | Reading | Confidence | Notes |
|-------|---------|-----------|-------|
| `hill cipher` | "return when the lion wakes" | 0 | Direct link: hill cipher answer gated by lion state |
| `four ciphers` | "closer than most" | 0.19 | Acknowledges the direction |
| `solve` | "closer than most" | 0.19 | |
| `mercury` | "return when the lion wakes" | 0 | Same gate as hill cipher |
| `third voice` | "return when the lion wakes" | — | Third voice also gated by lion |
| `prima materia` | "you have been here before" | 0.22 | |
| `caesar` | "you have been here before" | 0.22 | |
| `test` | "patience" | 0.31 | |
| `lion` | "patience" | 0.31 | |

---

## Directional readings

| Query | Reading | Confidence |
|-------|---------|-----------|
| `vigenere` | "you are looking in the wrong direction" | 0.07 |
| `epoch 1618` | "you are looking in the wrong direction" | 0.07 |
| `seed 42` | "you have been here before" | 0.22 |
| `1617` | "Closer than most. Still wrong." | — |
| `circle square triangle circle` | "the path is longer than you think" | 0.03 |
| `rot13` | "the path is longer than you think" | 0.03 |
| `base58` | "seek elsewhere" | 0.04 |
| `cipher` | "the answer is not here" | 0 |

---

## Oracle interaction readings

| Query | Reading | Source clue |
|-------|---------|------------|
| `lion awake` | "the oracle does not repeat itself" | "the medicine is occult because it is buried in the formula itself" |
| `aurora` | "this query has been asked before" | "look until resemblance becomes method" |
| `third voice` | "return when the lion wakes" | "lineage matters more than ornament" |
| `unseal sector-7` | `INSUFFICIENT_AUTHORITY` | "the key predates the lock" |
| `mirror` | "mirror first, then combine" | — |

---

## Notes on oracle behavior

- Oracle confidence scores are loosely meaningful: 0.19–0.31 = on-track area, 0–0.07 = wrong direction or not here
- The oracle repeats `"the oracle does not repeat itself"` for queries already asked in the session
- `"return when the lion wakes"` is the most recurring gate — the lion sleeping blocks multiple branches
- `"mirror first, then combine"` — suggests sequence: submit mirror-related answer, then combine-related answer
