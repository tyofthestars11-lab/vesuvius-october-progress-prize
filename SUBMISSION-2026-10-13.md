# Vesuvius Challenge — October Progress Prize Packet (DRAFT — held for Tyree's word)

**Nothing in this packet has been submitted.** It is assembled only from work already finished, for Tyree's review.
**Deadline (verified on scrollprize.org/prizes, read October 13, 2026): October 31, 2026, 11:59pm Pacific.**
Progress Prizes are monthly: Best Submission of the Month $20,000 guaranteed; further awards typically $20,000 / $10,000 / $5,000 / $2,500 / $1,000 / $500 / $250. Submissions go through the form linked from the prizes page. Multiple submissions per month are permitted.
Paris 4 Title is a separate entry and is **not** part of this packet.

---

## 1. Title

PHerc.1667 unwrapping geometry and ink-detection validation: 26,932 vertex hits across 14 patches, a validated flattened-mesh correspondence, and the completed First Letters pipeline

## 2. Contribution statement (plain)

My contribution is scroll unwrapping geometry and ink-detection validation on the public Herculaneum data. On PHerc.1667 I measured where a published transcription's columns fall on the scroll's surface geometry, tested how strongly the surface signal tracks the text, and validated how the community's flattened mesh maps back to the original surface — including exactly where that mapping is blocked and why. On PHerc1447 I completed the First Letters pipeline end to end. Everything below is measured and reproducible from the public data and the public code; where a result is partial or exploratory, it says so.

## 3. Problem addressed

Virtual unwrapping work needs checkable answers to three practical questions: (1) does a segmentation's surface geometry line up with the text columns scholars have transcribed, (2) does the surface carry a signal that tracks ink at all, and (3) can results computed on a flattened mesh be carried back to the original curled surface without error. This packet answers all three on PHerc.1667 with numbers, and states the one transfer that remains blocked — on the unpublished straightening deformation field — so no one else has to rediscover the wall.

## 4. The work (finished results only)

**PHerc.1667 — full 14-patch geometry.** All 26,932 vertex hits partition into the 14 original-mesh patches; 0 hits fall outside. Spiral center (mean of the 14 patch centroids): (9535.0673, 4350.7686, 2487.9621). Patch-to-column assignment (fallback mapping, columns 13–21) is near-monotonic: Pearson 0.9916404225, Spearman 0.9944903162 — noted in the source work as structural (both orderings derive from original-mesh u), not independent evidence.

**Text-derived correlations (exploratory, honestly labeled).** Per-column vertex-hit counts against text-derived proxies for columns 13–21: Greek slots (letters + lacuna dots) r = 0.3567195097; Greek letters only r = 0.3295027068; stroke-area proxy r = 0.3235407617; whitespace fraction r = −0.1311353728. No proxy exceeds r = 0.357. These are text-derived proxies — not measured ink density, and not a character-decoding result. The published Greek was aligned using fallback bins; it was not decoded from the surface states.

**Binary-state distribution.** State-0 fraction per patch ranges 0.461715–0.605263, with a linear fit against patch index of slope +0.0059328561 per patch (intercept 0.4588228289): deeper patches skew toward state 0, particularly patches 11–14; the pattern is not strictly monotonic.

**Flattened-OBJ correspondence — verdict PARTIAL, with the validated half exact.** The flattened OBJ (1,060,041,328 bytes, verified byte-complete, zero null bytes) holds 4,406,818 vertices. A 3D nearest-neighbor match between curled-mesh hit positions and straightened OBJ positions is invalid (mean distance 6797.621; 0.00% within 320 units) — the two live in different spaces, and the source work says so plainly. The validated correspondence runs through texture coordinates: flat_u = vt_u / 20, flat_v = vt_v / 20 — a perfect 1:1 map between all 4,406,818 OBJ vertices and a 67.5% subset of flattened-grid cells (u = 0…9203, v = 80…707), zero duplicates, zero non-integer values. The map is kept as a 4,406,818-row CSV (obj_idx, flat_u, flat_v). The remaining blocker: transferring original-mesh hits into flattened (u,v) needs the flatboi straightening deformation field, which is not in the public release.

**Column pipeline (the September base this extends).** Per-column hit detection and Greek accounting across columns 13–21 on the public PHerc.1667 flatboi surface (9,205 × 709): Greek letters per column 122, 164, 169, 200, 160, 175, 191, 174, 89; the slots = letters + dots rule holds across all 9 columns.

**First Letters pipeline (PHerc1447) — completed.** The full workflow (segment, flatten, render, ink detection) was run end to end on PHerc1447. Current honest state: 0 legible letters. The pipeline is the deliverable; no letters are claimed.

## 5. Implementation path and reproduction

1. Download the public PHerc.1667 flatboi TIFXYZ and the flattened OBJ from the Vesuvius Challenge open-data release.
2. Run the column pipeline (plain Python, numpy + scipy) in the documented order: hit generation → column analysis → geometry/correlation tasks → correspondence validation.
3. Every reported number regenerates from the CSV/JSON outputs (hit lists, per-column records, the vertex map).
Code: https://github.com/tyofthestars11-lab/vesuvius-progress-prize (September) and https://github.com/tyofthestars11-lab/vesuvius-october-progress-prize (October). License: MIT.

## 6. Official-format checklist (matched to scrollprize.org/prizes, Progress Prizes)

Core requirements:
- [x] 1. Problem identification and solution — a specific challenge on Vesuvius Challenge scroll data (Section 3), with an implementation path and demonstration (Sections 4–5)
- [x] 2. Documentation — comprehensive, with usage examples (this packet + script headers + run order)
- [x] 3. Technical integration — standard community formats throughout: tifxyz surface data in, CSV/JSON records and an OBJ-vertex map out; modular scripts, each runnable standalone in the documented order

What the judges say they favor:
- [x] Released / open-sourced early — code public on GitHub since September; October repo public since October 3
- [x] Improves results on real data, quantitatively — 26,932 hits fully partitioned with 0 outside; a 1:1 validated map over 4,406,818 vertices; effect sizes reported with their limits (r ≤ 0.357, labeled exploratory)
- [x] Insightful, actionable information — the correspondence blocker is named exactly (unpublished straightening deformation field), with the invalid method (3D nearest-neighbor across spaces) documented so others skip it
- [x] Well documented — honesty notes travel with the numbers: what is structural, what is a proxy, what is partial
- [ ] Actually gets used by the community — signals (questions, comments, use by the Annotation Team) accrue after filing; nothing claimed yet

## 7. Links (for the submission form)

- October repo: https://github.com/tyofthestars11-lab/vesuvius-october-progress-prize
- September repo: https://github.com/tyofthestars11-lab/vesuvius-progress-prize
- Phi ledger (the organizing record for the scroll work): https://tyofthestars11-lab.github.io/phi-ledger-cookie-chain/

---

**Held for your word.** To file: open the Progress Prizes section at https://scrollprize.org/prizes, follow its submission form link, paste from this packet. Deadline October 31, 2026, 11:59pm Pacific — nothing sends before you say so.
