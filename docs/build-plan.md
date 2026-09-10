# MeshUp Labs, and the system it runs on

**Build plan — Option C confirmed — September 2026**
Status: proposed, awaiting sign-off. No code written yet.

Supersedes [`tech-stack-recommendations.md`](./tech-stack-recommendations.md). That
document stands as the record of why option C was chosen; this one is the plan for
building it.

## The brief this answers

| | |
|---|---|
| Stack | Next.js + Payload + PostgreSQL (option C) |
| Template | Next.js / React — drops straight in |
| Own site | Marketing **and** a store |
| Client model | Client self-serves on our system, we set up |
| Client promise | Store live in 2 weeks |

## What changed

Last time we were planning a portfolio site. What's now described is a different
business: MeshUp Labs sells fast, simple, SEO-strong online stores, sets them up,
and hands day-to-day running to the client while staying on support. The portfolio
is the shop window for that.

This makes option C the right call for a better reason than before. A portfolio
doesn't need a database we own; a service where *clients live on our system*
absolutely does.

It also means we're building **two things**, and only one is a website:

1. **meshuplabs.com** — marketing plus a real store, since we sell packages and
   templates directly.
2. **The delivery system** — whatever a client store actually runs on. This is the
   business. Get it wrong and the two-week promise is a lie we keep manually.

## The assumption worth examining

"Clients self-serve on our system" has two very different technical meanings, and
the more expensive one is the default assumption.

### Model 1 — Each client gets their own copy *(recommended first)*

One template repository. Every client store is its own deployment from it, with
its own database and its own Stripe account. "Our system" means our template, our
hosting, our support — not one shared machine.

*Like a builder with a house design they've built forty times. Same plans, same
crew, same two-week schedule — but each house stands on its own plot and nobody
shares a boiler.*

| | |
|---|---|
| Ready to sell | Immediately |
| Cost per client | ~$15–25/mo |
| If one breaks | One client affected |
| Payments | Client's own Stripe |
| Starts hurting at | ~15–20 clients |

### Model 2 — One system, every client inside it *(later, once earned)*

A true platform. One application, one database, every client a tenant within it,
each with their own domain and branding. One update reaches everyone at once.

*Like an apartment block instead of forty houses. Far more efficient per resident —
and a burst pipe is everybody's problem at once.*

| | |
|---|---|
| Ready to sell | 3–5 months |
| Cost per client | Falls sharply |
| If one breaks | Every client affected |
| Payments | Stripe Connect — we route other people's money |
| Starts hurting at | Day one, if built too early |

> **Why this is the whole decision.** The shared-platform version means money from
> our clients' customers flows through infrastructure we operate. That pulls in
> payment routing, payout compliance, and a class of failure where one bad deploy
> takes down forty shops on a Friday. It's a fine destination. It is a terrible
> starting point, and nothing about the two-week promise requires it.

## Recommendation: ship per-client copies now, earn the shared platform later

One template repository, one deployment per client. We can sell the two-week
promise from the very first client, because onboarding becomes a checklist rather
than a project — and the template already exists, so no build stands between us and
client number one.

This isn't a throwaway. The shared-platform version is the same codebase and the
same content structure, reorganised. Everything built now carries forward; we're
deferring the hard part, not repeating it.

**Move to the shared platform when** keeping client sites updated costs more than
about a day a month, or we pass roughly fifteen live clients — whichever comes
first. Both are countable. Before then, building it is speculation paid for in
months.

## The stack, layer by layer

One set of choices covers both our own site and every client store — which is the
point. Our site is instance zero of the same template, so it proves the product
works before we sell it.

| Layer | Choice | Why |
|---|---|---|
| Front end | Next.js, from our template | Pages assembled on the server and sent complete — what makes them fast and readable by search engines. The template already covers this layer. |
| Admin & content | Payload | The editor clients log into. Runs inside the same application rather than as a separate service, so there's one thing to deploy and one to back up. |
| Database | PostgreSQL | Products, orders, pages, customers. Ours, exportable, portable between hosts. |
| Payments | Stripe, in the client's own account | Their money goes straight to them; we never hold it. Keeps us out of payment compliance entirely and is the biggest single reason to start with separate copies. |
| Images | Cloudflare R2 or Bunny | Product photography is the heaviest thing on a store and the usual reason they load slowly. Not optional when selling speed. |
| Hosting | Railway or Render | App and database on one bill per client, provisioned from a template in minutes. Straightforward to hand over if a client leaves. |
| Watching it | Sentry, Better Stack, nightly backups | This is what the support retainer actually pays for. We cannot support what we cannot see, and finding out from the client is finding out too late. |

## Turning four marketing claims into four engineering commitments

E-commerce, simplicity, SEO and support aren't just headings on the homepage. Each
is a promise someone can hold us to, and each has a cost paid in the build.

**E-commerce** — products, cart, checkout, tax, shipping, refunds, abandoned
baskets. The last four are where "simple store" projects overrun.
- Build all of it once, into the template
- Never rebuild per client — configure it
- Decide now what we *don't* support: subscriptions, multi-currency, marketplaces

**Simplicity** — a promise about the admin screen, not the shop front. If clients
self-serve, the editor *is* the product they're buying.
- Hide every field a client doesn't need
- One obvious way to add a product
- Test it on a real client before launch, not after

**SEO** — the most measurable claim we make, and the easiest to be caught out on.
- Product structured data, sitemaps, clean URLs
- Redirects from the old site — the single biggest risk
- Send a real speed and ranking report monthly

**Support** — the recurring revenue, and the thing that quietly eats the week if
the line isn't drawn early.
- Write down what's included and what's billable
- Record the handover training once, reuse it
- Restore a backup as a drill before needing it for real

> **The strongest thing we can do for this positioning.** Make meshuplabs.com
> itself the proof. If we sell speed and SEO, our own site's load time and search
> performance are the advertisement — publish the numbers on the site. A slow site
> selling SEO loses the argument before the call starts.

## The two weeks we're selling

The promise only holds if onboarding is a checklist someone could follow without
us. It's realistic precisely because none of it is building software — the software
already exists.

| When | What |
|---|---|
| Before | **Intake, and no start without it.** Products and prices, brand assets, domain access, current site address, who's handling photography. A client who hasn't sent this hasn't started their two weeks — say so in writing at the sale. |
| Days 1–2 | **Instance up, staging live.** New deployment from the template, database provisioned, temporary address the client can look at from day two. Seeing something real this early is what makes the rest of the fortnight calm. |
| Days 3–5 | **Brand and pages.** Logo, colours, typography, and the written pages — about, delivery, returns, contact. Configuration, not development. |
| Days 6–8 | **Products in, photography placed.** Bulk import from a spreadsheet, images processed, tax and shipping rules set. Build the importer once during our own site's build and this stays a two-day job forever. |
| Days 9–10 | **Payments connected and genuinely tested.** Their Stripe account, test mode first: buy something, refund it, check the confirmation emails arrive and read properly. |
| Days 11–12 | **SEO migration — the risky day.** Map every old URL to its new home before cutover. Skipped, this loses a client their existing search traffic overnight and turns a happy launch into a refund conversation. Everything else on this list is recoverable. This isn't. |
| Day 13 | **Handover training, recorded.** Walk them through adding a product, editing a page, finding an order. The recording becomes their reference and our support deflection. |
| Day 14 | **Domain cutover and monitoring on.** Live, watched, backed up. Then a scheduled check-in at day 30, which is where support retainers are actually sold. |

## Building our own site first

Instance zero. Shop window, store for our packages, and proving ground for
everything above — if the importer or the admin is awkward here, we find out on our
own time rather than a client's.

With the template in hand, budget **4–6 weeks**, not the 6–10 quoted before: the
template removes most of the front-end work, and skipping the shared-platform
architecture removes the rest.

| Week | Focus |
|---|---|
| 1 | **Template in, content structure defined.** What a product is, what a case study is, what a package is. Getting this right once is what makes every later client a configuration job. |
| 2 | **Commerce working end to end.** Cart, checkout, tax, shipping, order emails — on our own store, with our own packages. The part we never want to write twice. |
| 3 | **Admin trimmed, importer built.** The two things that make the two-week promise repeatable. Treat them as product features, not internal tooling. |
| 4 | **SEO, speed and the proof.** Structured data, sitemaps, image handling, and the measured numbers we publish as our sales argument. |
| 5–6 | **Launch, then clone it once.** Spin up a throwaway second instance from the template and time it. If it isn't fast and boring, the two-week promise isn't ready to sell. |

## Decide these before any code is written

Four commercial questions with direct technical consequences. Answering them late
means rework; answering them now costs an afternoon.

**If a client leaves, do they take the site with them?**
*Say yes.* With separate copies we can genuinely hand over code and database, and
it's a strong differentiator against platforms that lock people in — "you own it"
sells. Note it's a promise the shared-platform model makes much harder to keep, so
decide it knowing that.

**Whose Stripe account takes the money?**
*Theirs, always.* We never touch client funds, which keeps us out of payment
regulation and removes an entire category of liability. Revisit only on the shared
platform.

**Who owns the domain name?**
*The client, in their own account.* Holding client domains feels like a retention
lever and is really a hostage situation waiting to sour a relationship. Ask for
access, not ownership.

**What is explicitly not included?**
Write the list before the first sale: subscriptions, multi-currency, marketplaces,
bespoke integrations. An undefined "simple store" is how a two-week build becomes
six.

## On "modern"

Worth being specific, because modern is where a lot of budget goes to die. For a
business selling simplicity and speed, restraint *is* the modern look: generous
space, confident typography, real product photography, motion used once or twice
for emphasis rather than everywhere.

Every heavy effect added to our own site is an argument against the thing we're
selling. The site should feel fast, uncluttered and obviously well-made — because
that is a live demonstration of what a client is buying, and a claim a prospect can
verify in the first three seconds.

---

Timings assume one experienced developer and a template that needs no conversion.
Per-client hosting costs exclude the client's own Stripe fees.
