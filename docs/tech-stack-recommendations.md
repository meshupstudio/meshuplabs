# How to build the MeshUp Labs site

**Technical direction — September 2026**
Status: proposed, awaiting sign-off. No code written yet.

## The brief this answers

| | |
|---|---|
| What we're building | Studio & portfolio site |
| Who's building it | One experienced developer |
| Optimising for | Fast launch, room to grow |
| Window | ~3 months, modest budget |

## Read this part first

A portfolio site is not a hard thing to build. Any of the four options below will
be standing up and working well inside three months, and two of them inside the
first month. The schedule risk isn't the code — it's the case studies, the
photography and the writing. Those take longer than people expect and can't be
rushed at the end.

That reframes the decision. We aren't choosing what's fast enough. We're choosing
**who gets to publish**, and **what the site is allowed to become in year two**.

"Room to grow" for a studio site nearly always means one of three specific
things, and they point at different answers:

1. More case studies, and more people writing them.
2. Interactive Labs pieces that need to run real code in the browser.
3. Logged-in areas — a client review portal, a shop for templates, a members' section.

> **The trap to avoid.** The expensive mistake isn't picking a stack that's too
> small. It's picking one that's too big, spending six weeks on machinery for
> features nobody has committed to, and launching with three case studies because
> the writing never got done.

## Option A — The printed magazine

*Every page is finished and printed before anyone asks for it. Handing one to a
reader is instant, because nothing is being made while they stand there waiting.*

| Layer | Choice |
|---|---|
| Front end | Astro |
| Back end | None — pages are built ahead of time |
| Database | None — case studies live as text files beside the design |
| Hosting | Cloudflare Pages or Netlify, free tier |

**Why it fits.** Fastest-loading option by a wide margin, and a studio site gets
judged on how it feels in the first second. Costs essentially nothing to run. One
developer can hold the entire thing in their head — no second system to keep in
sync, no account to renew, nothing to patch.

**What we give up.** Every content change is a developer change. Adding a case
study means editing files and republishing, so nobody else in the studio can
publish without going through one person. Client logins or a shop later means
bolting on a second system rather than extending this one.

**Build: 2–4 weeks · Run cost: $0–5/month**

## Option B — The restaurant kitchen

*The recipes are written down once, somewhere any member of staff can read and
change them. Plates go out made to order — but the popular dishes are kept ready,
so almost everyone is served immediately.*

| Layer | Choice |
|---|---|
| Front end | Next.js |
| Back end | Built into the same application |
| Content | Sanity — a hosted editor the studio writes in |
| Hosting | Vercel |

**Why it fits.** Anyone in the studio can write and publish a case study in a
proper editor, without touching the developer or waiting for a deploy. The most
widely used foundation of its kind, so a future hire or contractor already knows
it on day one. Grows into a real application — logins, a shop, a client area —
without starting over.

**What we give up.** Three things to keep in sync instead of one: the site, the
content editor, the host. Free tiers are genuinely fine for launch, but expect
roughly $20/month per person once a shared team account is wanted. Pages are a
shade slower than option A unless set up carefully — real but manageable.

**Build: 4–7 weeks · Run cost: $0–20/month**

## Option C — The house plumbed for a second storey

*Run the wiring and pipework for an upstairs during the original build. It costs
more now, and you live in the same size house for a while — but adding the second
floor later is a weekend's work rather than a demolition.*

| Layer | Choice |
|---|---|
| Front end | Next.js |
| Back end | Payload, running inside the same application |
| Database | PostgreSQL, ours to export |
| Hosting | Railway, Render or Fly — single bill |

**Why it fits.** Content, accounts and files all live in one system we own, in one
database we can export and take anywhere. If Labs becomes a members' area, or
clients need logins to review work, or we sell templates, the foundations are
already poured. One supplier, one bill, no vendor able to change the terms
underneath us.

**What we give up.** Slowest route to launch, and we pay for capability not needed
on day one. We also become responsible for the database — backups, upgrades, the
occasional problem at an unsociable hour — which options A and B hand to somebody
else.

**Build: 6–10 weeks · Run cost: $10–30/month**

## Option D — The serviced apartment

*You move in this week. Everything works, it's furnished, and someone else fixes
the boiler. You also can't knock through a wall, and the rent never stops.*

| Layer | Choice |
|---|---|
| Front end | Provided by the platform |
| Back end | Provided by the platform |
| Database | Built-in, not directly accessible |
| Hosting | Framer or Webflow — all one product |

**Why it fits.** By far the fastest way to be live, and the site is built by
dragging things around rather than writing code — which suits a visually-led
studio and puts the design directly in a designer's hands. Effectively no
maintenance, ever.

**What we give up.** The one option a good developer can't rescue later. Custom
interactive work — exactly what "Labs" implies — hits a hard ceiling, because we
can't run our own code. Moving elsewhere means rebuilding from scratch. The
monthly fee is permanent and rises with traffic.

**Build: 1–3 weeks · Run cost: $20–60/month**

## Side by side

Costs are first-year, at the traffic a studio site actually gets. Lock-in means
how hard it would be to walk away in two years and take the work with us.

| Option | Live in | Cost/month | Who can publish | Room to grow | Lock-in |
|---|---|---|---|---|---|
| **A** — Printed magazine | 2–4 weeks | $0–5 | Developer only | Limited | None |
| **B** — Restaurant kitchen | 4–7 weeks | $0–20 | Anyone in the studio | Strong | Low |
| **C** — Plumbed house | 6–10 weeks | $10–30 | Anyone in the studio | Strongest | None |
| **D** — Serviced apartment | 1–3 weeks | $20–60 | Anyone in the studio | Capped | High |

## Recommendation: build option B

We asked for a fast launch *and* room to grow. **B is the only option that scores
well on both at once**, and it's the one to sign off on for MeshUp Labs.

- **A** launches sooner but permanently routes every published word through one
  developer — the wrong bottleneck for a studio that lives on publishing work.
- **D** launches sooner still, then quietly forecloses the interactive Labs pieces
  that are the most distinctive thing we could put on the site.
- **C** is a genuinely good build, but it asks us to buy a client portal we haven't
  committed to yet — and we can add exactly that later, on the same foundation,
  once it's real.

B costs roughly six of the twelve weeks. The rest goes to photography, case-study
writing, and two or three real Labs demos. That's what actually wins work.

**Switch to A if** the studio is genuinely happy for the developer to be the only
person who publishes, for at least the first year. Take A, save three weeks, spend
them on the work itself.

**Switch to C if** a client portal or members' area is already a committed, dated
plan with someone's name against it — not a maybe. Speculation doesn't justify it;
a scheduled commitment does.

## What the first three weeks look like

Assuming option B. The point of this order is that the slowest thing — writing and
shooting the work — starts on day one, in parallel with the build, rather than
being discovered late.

| When | What |
|---|---|
| Week 1 | **Decide the content shape.** Agree what a case study actually contains — how many images, whether there's a client quote, what the credits list looks like. This one decision drives most of the build, and changing it later is expensive. |
| Week 1 | **Start the writing and photography.** Immediately, in parallel. Pick the six projects that go in at launch and get them commissioned or drafted. This is the long pole. |
| Week 2 | **Stand up the skeleton and put it online.** An ugly but real site at a real address, with one genuine case study in it. Deploying on day ten rather than day sixty is what stops nasty surprises at the end. |
| Week 3 | **Hand the editor to someone who isn't the developer.** Watch them publish a case study unaided. If they can't, fix that now — it's the entire reason for choosing B over A. |
| Weeks 4+ | **Design properly, then build the Labs pieces.** With real content in place, the design has something true to respond to, and the interactive work gets built against a site that already works. |

---

Build estimates assume one experienced developer working steadily, not full-time
crunch.
