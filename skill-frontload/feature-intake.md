# Office Hours — Feature Intake (Builder mode)

Frontload context so `/office-hours` skips the questions it would otherwise ask
one at a time. Two parts: stable context that lives in your product's CLAUDE.md
(set once), and a short per-feature block you paste each session.

---

## Part A — Stable context (paste into your product's `CLAUDE.md`, once)

The skill reads `CLAUDE.md` in Phase 1, so this frontloads everything that's the
same every session — with zero changes to the skill itself.

```markdown
## Product context (for /office-hours and other gstack skills)

- **What it is:** AI-native web app that automates quotation building for a small business.
- **Who uses it:** Back-office employees with domain knowledge of the company's products and customers.
- **Where it runs:** Web app hosted on a custom-built production server.
- **Stack:** Node (frontend), Claude Code (AI backend).
- **Hard constraints:** Processing an email inquiry must take < 1 min; building a quotation must take < 1 min.

### Office-hours defaults
- **Mode:** Builder mode (Phase 2B). I bring features for an existing product —
  collaborative design-partner session ending in a concrete build plan, NOT
  startup demand-validation. Skip the goal question.
- **Web search (Phase 2.75):** Yes, generalized category terms OK.
- **Prior designs (Phase 2.5):** start fresh unless there's a strong match.
```

Kills every session, no copy-paste: goal/mode question, web-search gate,
prior-design gate, and all product/stack/constraints questioning.

---

## Part B — Per-feature paste (the short bit you type each session)

Paste right after invoking `/office-hours`:

```markdown
/office-hours

Feature: <one sentence — what you want to build (left blank; varies per build)>
Who it's for: The quotation-building team. It removes the monotonous work and
  brings them in only for judgement.
Today they: Read the client email and understand context + requirements (including
  technical ones), map requirements to products from the company catalog (stored as
  tables across multiple Excel sheets), copy and rename the quotation-template Excel
  file, copy-paste products from the Excel catalog into the template, add prices
  based on context, then email the finished file to the client. Entirely manual,
  per inquiry.
Smallest shippable: <narrowest slice that delivers value this week (left blank; varies per build)>
Closest existing thing: Comena (YC-backed) automates this for some industries. Ours
  differs — built for the UAE market and for businesses that operate ad hoc, where
  processes change weekly.
10x version: Three skills that mimic the workflow —
  (1) inquiry-parser: .eml email → requirements JSON;
  (2) product-matcher: requirements JSON + catalog Excel → recommended-products JSON
      (max 3 recommendations per requirement);
  (3) excel-quote-builder: recommended-products JSON → quotation Excel following the
      company template.
  Then, an AI brain that reads the company's email inbox, builds context on each
  client, infers product pricing from that client context, auto-fills pricing, and
  sends instant quote replies for inquiries that match a recurring pattern.
Success = <a behavior or number that means it worked (left blank; varies per build)>
Output: concrete build plan — ordered steps + the wedge to ship first
```

Each line maps to a Builder-mode question, so smart-skip suppresses it. Leave an
`[optional]` line blank and the skill asks just that one live.

## What's left after both parts

Down from ~9 question rounds to two — both by design, both ones you want:

1. **Phase 3** — premise confirm ("here's what I'm assuming, agree?")
2. **Phase 4** — pick approach A/B/C → this is your build plan
