# Our stack, their platform

**Build plan — Revision 2 — September 2026**
Status: proposed, awaiting sign-off. No code written yet.

Revision 2 replaces the per-client-instance plan. The multi-tenant platform
question is closed and does not need revisiting. Supersedes
[`tech-stack-recommendations.md`](./tech-stack-recommendations.md), which remains
the record of why option C was chosen for our own site.

## The brief this answers

| | |
|---|---|
| Our site | Next.js + Payload + PostgreSQL (option C) |
| Client stores | Duda white label |
| Template | Next.js — our site only |
| Our site build | 3–4 weeks |
| Client promise | Store live in 2 weeks |

## What this settles

Splitting the two systems is the right call, and it removes the largest open risk
in the previous plan. We are not building a platform. We are reselling one, and
building a good site to sell it from.

Everything raised last revision about multi-tenancy, routing other people's money,
and one bad deploy taking down forty shops on a Friday is now somebody else's
problem, and they employ people to have it. That was a three-to-five month build
now avoided entirely.

It also shrinks our own site. The last plan had meshuplabs.com doing double duty as
the proving ground for client delivery. It isn't that any more — it's just our site
— so it gets simpler and faster, and we should resist keeping the ambition that
came with the old role.

### meshuplabs.com — we build and own it

Marketing site, case studies, and a small store selling build packages and support
retainers. Our capability demonstration — proof we're a studio, not only a reseller.

| Layer | Choice |
|---|---|
| Front end | Next.js, from our template |
| Content | Payload |
| Database | PostgreSQL |
| Payments | Stripe Checkout + Billing |
| Hosting | Railway or Render |
| Build | 3–4 weeks |

### Client stores — we configure and support them

Duda white label. Our branding on the editor clients log into, their store running
on Duda's infrastructure, our team doing setup, migration and SEO.

| Layer | Choice |
|---|---|
| Platform | Duda White Label |
| Store | Duda eCommerce add-on, per site |
| Payments | Client's own processor |
| SEO tools | Built in — genuinely good |
| Hosting | Duda's, included |
| Delivery | 2 weeks, config not code |

## A correction from the last revision

The previous plan said to promise clients they own their site and can take it with
them. On the per-client-Next.js model that was true and a genuine differentiator.
**On Duda it isn't, and making that promise would put us in a corner.**

Duda's site export produces a zip of published HTML, CSS, images and scripts — a
static snapshot, not editable source. For a brochure site that's a partial escape
hatch. For a *store* it isn't one at all: the cart, checkout, product data and any
widgets don't come with it. Duda's own client-management design is explicit that
clients get review-and-request-edits access while the agency retains the account.

So do not sell portability of the site. Sell portability of the things that
genuinely are theirs, name them plainly, and let that honesty be the differentiator
— most resellers won't say any of this out loud.

> **What we can honestly promise.** Their domain, registered in their own account.
> Their payment processor account, holding their own money. Their product data,
> exported to a spreadsheet on a schedule and handed over on request. Their content
> and imagery. That's a real ownership story. The site build itself stays with the
> platform — say so at the sale, not at the exit.

## What Duda gives us, and what we're accepting

Checked against current sources rather than recalled. The headline is better than
expected on the thing we're most exposed on, and the constraint is somewhere we may
not have been looking.

### What it gives us

- **The SEO claim is defensible.** Built-in 301 redirect manager, JSON-LD
  structured data, automatic canonical tags, strong Core Web Vitals record. This
  was the biggest worry about our positioning and it's largely answered.
- **Migration redirects are a managed feature**, not hand-rolled per client —
  directly de-risking the step most likely to lose a client their rankings.
- **More commerce than assumed.** Physical goods, digital downloads, services, and
  genuine subscription and recurring billing — so a client selling memberships or
  monthly boxes isn't automatically out of scope.
- **Real white-labeling**, so "clients self-serve on our system" is true in the way
  that matters: the editor they log into is branded ours.
- **Zero infrastructure work.** No deployments, databases, backups, monitoring or
  2am pager. The support retainer becomes almost pure margin on our time.

### What we're accepting

- **A fixed monthly floor before the first client.** White-label pricing starts
  around $149/month including roughly four sites — a real bet if signed before
  anything is sold.
- **Commerce is a per-site add-on on top of that**, tiered by product count,
  roughly $7–52 per site per month. Package pricing has to clear it on every client.
- **A product-count ceiling per tier** — entry tier around 100 products. Fine for
  most small stores, an instant disqualifier for a catalogue business. Ask product
  count on the sales call.
- **Multi-currency is a weak spot** relative to Shopify. A prospect selling
  internationally in several currencies is a referral, not a sale.
- **Platform dependency.** Duda's pricing, roadmap and terms are outside our
  control and set the ceiling on what we can promise. We are a reseller now, with a
  reseller's margin risk.

> **Verify the numbers before committing.** Published sources disagree on exact
> tier limits — one puts the middle tier at 1,000 products, another at 2,500 — and
> pricing moves. Get current figures from Duda directly for the two that decide our
> margin: *what an extra site costs beyond the four included*, and the
> transaction-fee position on each commerce tier. Those two numbers set our floor
> price per client.

## When the white-label tier starts paying

The base fee is fixed, so it's brutal at one client and forgettable at fifteen.

| Live clients | Base share each | + Commerce | Cost per client | Verdict |
|---|---|---|---|---|
| 1 | ~$149 | ~$7–20 | ~$156–169 | Paying for a platform to serve one person |
| 4 | ~$37 | ~$7–20 | ~$44–57 | Break-even; included sites used up |
| 10 | ~$15 | ~$7–20 | ~$22–35 + extra-site fee | Works, if the extra-site fee is modest |
| 20 | ~$7 | ~$7–20 | ~$14–27 + extra-site fee | The model the pricing is designed for |

**So don't buy it yet.** Line up three or four committed clients first, or run the
first one or two on a lower tier to prove the delivery process, then upgrade when
white-label branding is what's actually blocking a sale. Subscribing on day one
buys a monthly bill and a self-imposed deadline. Figures exclude the extra-site fee
beyond the included four — the number worth getting from Duda before modelling this
properly.

## Recommendation: keep option C for our site, but build a much smaller version

Our site is no longer the proving ground for client delivery, so it doesn't need
the machinery the last plan gave it. No product importer. No trimmed client admin.
No per-client anything. It's a marketing site with a handful of things to sell.

Specifically: **don't build a cart and checkout.** We're selling perhaps five
packages and a recurring retainer, not running a catalogue. Stripe Checkout handles
one-off purchases and Stripe Billing handles retainers — both hosted, both
compliant, both roughly a day's work against a week or more for the real thing.
Payload runs content, Stripe runs the money, and we keep every reason option C was
chosen: our template, our database, our control over the SEO we're selling, and no
per-site platform fee on our own front door.

## Building our own site

Three to four weeks. Run the Duda trial in parallel from week one — the tracks
don't block each other, and the trial is what tells us whether the two-week promise
is real before we print it.

| Week | Focus |
|---|---|
| 1 | **Template in, content structure defined.** Services, packages, case studies, retainer tiers. Also: start a Duda trial and begin building the reusable client starter site in it. |
| 2 | **Content written, packages wired to Stripe.** Checkout for one-off builds, Billing for retainers. Test a purchase and a cancellation properly — including the emails. |
| 3 | **SEO, speed, and the proof.** Structured data, sitemaps, image handling — then measure our own site and publish the numbers. If we sell SEO, our own scores are the advertisement. |
| 4 | **Launch, and run the Duda dry run.** Build one complete practice store end to end and time it. If it doesn't come in comfortably under two weeks with slack, fix the process before selling the promise. |

## The two weeks, on Duda

Same shape as before, but almost none of it is now engineering — which is why two
weeks is a promise we can keep repeatedly rather than heroically.

| When | What |
|---|---|
| Before | **Intake, and no start without it.** Products and prices, brand assets, domain access, current site address, photography owner. Ask the product count here — it picks the commerce tier and can disqualify the sale. |
| Days 1–2 | **Site created from our Duda starter, preview shared.** Minutes, not days, once the starter exists. Client sees something real on day two. |
| Days 3–5 | **Brand and written pages.** Logo, colours, type, and the about / delivery / returns / contact copy. |
| Days 6–8 | **Products in, store configured.** Import, images, tax and shipping. Confirm the commerce tier matches the real catalogue size before going further. |
| Days 9–10 | **Payments connected to their account, tested.** Buy something, refund it, read the confirmation emails. Their processor, their money — we never hold it. |
| Days 11–12 | **SEO migration — still the risky day.** Duda's redirect manager makes this manageable but doesn't write the map. Every old URL to its new home, entered and checked before cutover. Skipped, this loses a client their search traffic overnight. |
| Day 13 | **Training on our branded editor, recorded.** Adding a product, editing a page, finding an order. The recording is their reference and our support deflection — and this session is where the DIY half of "DIY hybrid" is actually delivered. |
| Day 14 | **Domain cutover, live, day-30 check-in booked.** That check-in is where retainers get sold, so calendar it before hanging up. |

## Designing for the words "for now"

Duda *for now* is the right instinct and worth acting on. None of the following
costs anything today; all of it makes leaving cheaper later, and each is a habit
rather than a project.

- **Bill clients ourselves, through our own Stripe.** Not through the platform's
  billing. We keep the customer relationship, and Duda stays a cost line we can
  swap out rather than the counterparty on our revenue.
- **Export every client's product data on a schedule.** A monthly spreadsheet per
  client, kept by us. It's the one genuinely portable asset in a store, it's what
  makes our ownership promise true, and it costs minutes.
- **Keep custom platform widgets to a minimum.** Custom widget work is the least
  portable thing we can build and the first thing we'd rewrite. Prefer
  configuration over code, and note it when we can't.
- **Keep intake and onboarding platform-agnostic.** Write the checklist in terms of
  outcomes — "redirect map built", "payments tested" — not platform menus. Then the
  process survives a platform change and only the steps beneath it get rewritten.

## Still to decide before the first sale

**What's explicitly out of scope?**
Now set by Duda's real ceiling, not our preference: large catalogues,
multi-currency international selling, complex tax, heavy third-party integrations.
Write the list before the first sales call — it turns an awkward mid-build
discovery into a clean referral.

**What does the retainer actually include?**
With no infrastructure to maintain, we're selling time and attention: content
changes, SEO reporting, being reachable. Put a number on the hours and say what's
billable beyond them.

**What happens if a client leaves?**
Decide now, in writing, while it's hypothetical. They get their domain, their
payment account and their data export — and they know that from the first
conversation, not the last one.

**When do we subscribe to white label?**
At three or four committed clients, not before. Until then the branding isn't what's
losing us the sale, and the bill is real from month one.

## Sources

Platform details checked in September 2026 rather than recalled. Pricing and tier
limits change — confirm current figures with Duda before modelling margins.

- [Duda — Plans & Pricing](https://www.duda.co/pricing)
- [Duda Support — URL Redirects](https://support.duda.co/hc/en-us/articles/26519925447703-URL-Redirects)
- [Duda Support — Site Export](https://support.duda.co/hc/en-us/articles/26519246857495-Site-Export)
- [Duda — SEO features](https://www.duda.co/seo)
- [Duda — eCommerce](https://www.duda.co/ecommerce)
- [Duda — Client Management](https://www.duda.co/client-management)
- [Website Planet — Duda vs Shopify](https://www.websiteplanet.com/blog/duda-vs-shopify/)

---

Cost figures are indicative and exclude the extra-site fee beyond the four included
in the white-label plan.
