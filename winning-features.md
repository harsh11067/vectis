# Wallet with Opinions — Winning Features & Moat

> Companion to `plan.md`. The thesis: **win on depth + three research-backed pillars that are all the same primitive viewed three ways — not on feature count.**

## The principle (read first)

Feature count is inversely correlated with winning past a point: each feature is another thing that breaks on camera and another sentence diluting the story judges remember. So prefer **re-framings of the core delegation+caveat engine** (zero new failure surface) over **bolt-ons** (new subsystems, new ways to fail on mainnet).

Your delegation engine already *is* a policy engine, an audit log, and a revocation system. Surfacing those is nearly free and each gives a distinct research-backed talking point + demo beat.

## The three pillars (Tier 0 + two Tier-1) — this is the product

| Pillar | One-line claim | Same primitive as | Research (verified) |
|---|---|---|---|
| **1. Attenuated redelegation** | Authority only ever shrinks downstream; a child can't exceed its parent, enforced on-chain. | the core | South & Pentland, *Authenticated Delegation & Authorized AI Agents*, arXiv:2501.09674 |
| **2. On-chain policy + immutable audit log** | An unsafe agent action reverts on-chain *and* is recorded with its reason; the log is tamper-evident. | caveats = policy + the action log | *SoK: Security & Privacy of AI Agents for Blockchain*, arXiv:2509.07131; *New Vectors of AI Harm*, arXiv:2507.08249 |
| **3. Instant cascade revocation (kill-switch)** | User revokes the root; the entire subtree dies at once. | disabling a delegation breaks every chain under it | *New Vectors of AI Harm*, arXiv:2507.08249 (kill switches); revocability intrinsic to 2501.09674 |

All three are the delegation engine viewed three ways → maximum narrative + citations, minimum new failure surface. **Ship these three flawlessly before anything else.**

## Tiered menu

### Tier 0 — core (non-negotiable)
- **Multi-hop attenuated redelegation**, depth ≥ 2 (User→Governor→Researcher→Summarizer), each hop's caveats enforced on-chain. Verify: `verification-checklist.md` V2, V4, V8.

### Tier 1 — the differentiators (build both)
- **On-chain policy + audit log + "block the unsafe action"** demo beat. A deliberately malicious action reverts on-chain and lands in a tamper-evident log with the blocking caveat named.
- **Cascade revocation / kill-switch.** Revoke root → a child redemption that worked a minute ago now reverts.

### Tier 2 — stretch (only if Day 8 core is green on mainnet)
- **Proof-of-Delivery on x402** — settle only if the deliverable matches the request (A402, arXiv:2603.01179). Adds a *new* subsystem → new failure surface; that's why it's stretch.
- **Venice multi-modal** — Researcher reads a proposal's linked image/PDF. Lowest leverage: it's a capability, not a research gap. Only if it changes a decision in the demo.

### Tier 3 — do NOT build (name as "future work" for research credibility)
- **ZK intent proofs** (TIVA, arXiv:2511.15712) — ZK in 14 days kills the timeline.
- **Voting-bloc coordination** — the original mis-scope; not redelegation.
- **Multi-chain** — pure scope tax, no prize.

## Honest odds

The A2A track is winnable because real multi-hop redelegation is rare; the field is thin. The single determinant is **a working end-to-end redelegation on Base mainnet in the video** — not the UI, not feature count. Realistic ceiling for a clean build: place in A2A, plus contention for the Venice and 1Shot add-ons. There is no "100%"; there is "ship the invariant on mainnet and you're a real contender."

## Citations (verified this session — confirm they still resolve before submitting)

- South, Pentland, et al. (2025). *Authenticated Delegation and Authorized AI Agents.* arXiv:2501.09674.
- *SoK: Security and Privacy of AI Agents for Blockchain* (2025). arXiv:2509.07131.
- *Giving AI Agents Access to Cryptocurrency and Smart Contracts Creates New Vectors of AI Harm* (2025). arXiv:2507.08249.
- Li et al. (2026). *A402: Binding Payments to Service Execution.* arXiv:2603.01179.
- TIVA (2025). arXiv:2511.15712 — future work only.
- Qin & Duan (2026). *"What I Sign Is Not What I See."* arXiv:2601.16751 — ClearSign.

> Replace any "ICCA 2025" reference: I could not find a paper indexed under that name. 2509.07131 + 2507.08249 make the identical point (a blockchain can enforce policy on an AI's actions and create an immutable audit log) and they resolve.
