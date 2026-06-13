# Wallet with Opinions — Frontend Brief (objectives-driven, color-agnostic)

> This is a brief, not a mockup. It defines **what the UI must achieve and prove**, not how it must look. Hand it to Claude Design (or a designer) and let them own color, type, and spacing within these constraints. Build a **web dapp**, not an extension. Note: this hackathon has **no UI/UX prize** — the UI exists to make the demo *legible*, nothing more.

## 0. The one job

Let a judge watching a muted 3-minute video understand, without reading code, that:
1. the agent acted **on-chain** (real, verifiable transactions), and
2. every sub-agent had **provably less authority** than its parent (the A2A redelegation proof), and
3. the agent **reasoned in the open** before high-stakes actions (Venice / ClearSign).

If those three read instantly, the UI succeeded. Everything else is decoration.

## 1. Hard objectives (must-haves)

| # | Objective | UI must communicate | Why it matters |
|---|---|---|---|
| O1 | **Show the redelegation tree** | A live tree: User → Governor → sub-agents, each node showing its budget + capabilities, with the *capabilities it lacks* visibly absent/greyed vs its parent. Each edge links to the real redelegation tx. | This is the A2A prize proof. It must be the visual centerpiece. |
| O2 | **Prove on-chain, not app-side** | Every action and every delegation links out to the Base block explorer (real tx hash). | Judges discount anything that could be faked. The link is the trust. |
| O3 | **Show reasoning before acting (ClearSign)** | Before high-stakes/novel actions: Venice reasoning trace + plain-English summary + cost + remaining budget + [Authorize]/[Cancel]. | The Venice showcase; also the "user takes part" moment. |
| O4 | **Show the money flow** | x402 micro-payments in the feed (who paid whom, how much) and that **gas was sponsored** (gasless via 1Shot). | x402 + 1Shot track evidence. |
| O5 | **Distinguish enforced vs advisory** | At onboarding, show which rules became **on-chain caveats** (hard) vs **reasoning guidance** (soft). | Pre-empts "what's actually enforced?" — the credibility question. |
| O6 | **Real-time** | The feed and tree update live (SSE/WebSocket), within ~1s of an event. No refresh-to-see. | A live demo dies on stale UI. |

## 2. State language (the only "design" rule that affects scoring)

Define one consistent visual vocabulary so the demo is readable even muted. Map *meaning* to a treatment; pick the actual colors later:
- **Enforced on-chain** vs **advisory/prompt-only** — two clearly different treatments.
- **Settled** vs **pending/verifying** vs **blocked/withheld** — three clearly different treatments.
- **Has capability** vs **lacks capability** (for the tree nodes) — present vs visibly removed.
Whatever palette is chosen, these distinctions must survive grayscale.

## 3. Screens (keep it to one that carries the demo)

1. **Onboarding** (used once): connect MetaMask → type rules in plain English → show the **enforced vs advisory** split → sign the 7702 upgrade + root delegation. Keep it under 30s of demo time.
2. **Command Center** (the demo screen): the four regions below.
3. *(future, not for the demo)* Rules editor.

### Command Center regions (function, not layout)
- **Delegation Tree** (centerpiece, O1): nodes = agents with budget + capability chips; edges link to redelegation txs; children visibly narrower than parents.
- **Activity Feed** (O2, O4, O6): live stream of redelegation / x402 payment / decision / execution events, each with a tx link and the right state treatment.
- **ClearSign** (O3): reasoning trace (streamed), plain-English summary, cost, budget left, Authorize/Cancel.
- **Memory Log** (O2): past actions with cost + tx hash.

## 4. Anti-goals (do NOT build these — they signal low substance)

- ❌ Vanity finance chrome: fake "total portfolio value," trend graphs, efficiency gauges, "confidence 95%" dials. (These are the Image 1 / Image 3 trap.)
- ❌ A marketing landing page as the demo. Judges want the working product, not a hero banner.
- ❌ Generic "AI dashboard" widgets that don't map to a real on-chain event.
- ❌ Ten screens / heavy settings. One screen, deep.
- ❌ Any number on screen that isn't backed by a real value (a tx, a budget caveat, a real cost).

## 5. Demo legibility checklist (for the video)

- [ ] The subset relationship is obvious at a glance (a judge can point and say "that one can't spend").
- [ ] Every settled item is one click from a real Base explorer tx.
- [ ] ClearSign reasoning is large and streams (readable when paused).
- [ ] Gasless + x402 cost are explicitly labeled.
- [ ] All key states readable in grayscale / with sound off (subtitle key lines).
- [ ] Updates appear live during the demo, no manual refresh.

## 6. Future-feature extension points (leave room; don't build now)

Design the layout so these can be added later without a rebuild:
- **Rules editor** — edit/add opinions post-setup (a panel or modal slot).
- **More sub-agent roles** — Risk-Scorer, Negotiator (tree should accept N node types).
- **Proof-of-Delivery on x402** — a verdict badge slot on purchase events (borrowed from Aegis).
- **On-chain memory / attestations** — Memory Log entries could gain an "attested" badge.
- **Multi-chain** — the network badge should be a selector, not a label.
- **Notifications / mobile view** — the feed should degrade to a single-column mobile layout.

## 7. Brief to paste into Claude Design

> Design a single-screen "Command Center" web dashboard for an onchain AI-agent app. It must make three things instantly legible, even muted: (1) a **live delegation tree** (User → Governor → Researcher → Summarizer) where each child node visibly has fewer capabilities and less budget than its parent, and every edge links to a blockchain transaction; (2) a **real-time activity feed** of agent actions, each linking to a real transaction and clearly marked settled / pending / blocked; (3) a **ClearSign panel** showing the agent's reasoning in plain English with Authorize/Cancel buttons. Include a memory log of past actions with transaction hashes. Use a consistent visual state-language that survives grayscale: enforced-onchain vs advisory, and settled vs pending vs blocked, and capability-present vs capability-absent. Trustworthy, serious, finance-grade tone — avoid generic AI-dashboard chrome, vanity metrics, fake charts, and confidence dials. One deep screen, not many. Color and typography are open; the distinctions above are not.

*(Stack for the eventual build: Next.js + Tailwind + wagmi/viem + MetaMask connect; live updates via SSE/WebSocket from the agent process; no browser storage APIs.)*
