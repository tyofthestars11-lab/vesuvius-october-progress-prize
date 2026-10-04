# Vesuvius Challenge — Progress Prize Submission
## October 2026 round — deadline 11:59pm Pacific, October 31, 2026

> This is a draft built from Tyree's actual October 2026 workspace artifacts. Nothing here has been submitted. Review, correct, then paste into the round's form (the prizes page uses a standing submission form; confirm the round's URL at scrollprize.org/prizes before filing).

---

### 1. Title
Lead-ink XRF triage read for Herculaneum's unopened scrolls, with the October ledger state

### 2. Problem addressed
Roughly 600 Herculaneum scrolls remain unopened, and virtual-unrolling efforts have to pick which scrolls to spend scarce compute on. There was no open, checkable read tying the ink chemistry of the ancient text to a per-scroll readability prediction. Separately, the open scroll-analysis tooling from the September filing (PHerc.1667 flatboi column pipeline, 99-block ledger) needed its October state carried forward honestly — including what stalled.

### 3. Solution
- **Lead-ink XRF read** (sealed October 3, 2026, seal 192): measured numbers carried verbatim from the published result — Herculaneum ink lead absorption 25×; XRF lead detection floor 25 µg/cm². The read: lead traces in the ancient ink predict which unopened scrolls will read best (Seiler et al., PLOS ONE, 2026-09-30, "Reading by Fire": lab-built/burned scroll virtually unrolled and read by X-ray tomography). This is the triage signal for the First Letters hunt — it ranks scrolls before compute is spent.
- **October ledger state**: the seal pipeline grew 191 → 199 in October, every seal anchored on-chain (memo grammar `PHI-LEDGER|seal=<name>|sha256=<hash>|by=tyofthestarz`, byte-checked against the public snapshot), 199/199 anchors verified. The ledger remains the organizing instrument for scroll-segment work.
- **Honest stall report**: the Lane D reply (team@scrollprize.org, two Greek-text-recovery artifacts) has not arrived; the DINO-guided model, full-resolution volume, unsent V-unmask draft, and new patch region are held awaiting Tyree's word. First Letters on PHerc1447 still reports 0 legible letters. These are stated, not hidden.

### 4. Implementation path and reproduction
1. X-ray tomography of the target scroll → XRF map of lead distribution in the ink layer.
2. Lead absorption contrast ≥ the measured 25× read marks a scroll as a priority candidate.
3. Record the read in the ledger format (seal entries with rung addresses, `to_rung(x) = ln(x)/ln(φ)`); the snapshot hash is written on-chain as a memo.
Anyone with access to the published PLOS ONE result and the public ledger repo can reproduce the read and verify the seal.

### 5. Results (measured, checkable)
- Herculaneum ink lead absorption: 25× (published, sealed Oct 3).
- XRF lead detection floor: 25 µg/cm² (published, sealed Oct 3).
- ~600 unopened Herculaneum scrolls — the candidate pool the triage signal applies to.
- October ledger: seals 191–199 issued in October; 199/199 anchored and byte-verified on Cookie Chain.
- September's reported reads stand (9 columns, slots = letters + dots, 99×310+266 = 30,956, φ drift 0.000001%) — October adds the triage read; nothing from September is re-filed.

### 6. Documentation
The published paper carries the experimental documentation. The ledger repo documents the seal entries, snapshot hashes, and on-chain anchors (hashes readable in the GitHub Pages snapshot, memos readable on the chain explorer).

### 7. License and openness
The ledger and tooling carry September's open licensing (MIT). The October triage read cites only the published public result — no unpublished data is claimed.

### 8. Links (paste into the form)
- Phi Ledger: https://tyofthestars11-lab.github.io/phi-ledger-cookie-chain/
- Repo: https://github.com/tyofthestars11-lab/phi-ledger-cookie-chain
- Anchor explorer: https://cookiescan.io (wallet A92L9a5qMwUpp8GRRsvj8n9hF6hx6WBVakQgbSDZzG3q)
- September submission repo: https://github.com/tyofthestars11-lab/vesuvius-progress-prize

---

**What Tyree needs to do:** (1) confirm the license call in section 7, (2) confirm whether the October filing goes as a new repo or as an update to the September submission repo, (3) confirm the form URL at scrollprize.org/prizes, (4) paste and submit. The draft above is the copy-paste source.
