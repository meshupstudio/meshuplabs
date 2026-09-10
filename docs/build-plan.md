# The store is the asset

**Build plan — Revision 3 — September 2026**
Status: proposed, awaiting sign-off. No code written yet.

Revision 3. The plan's shape is unchanged; what changes is the exit story, the
scope limits, and how the offer is tiered. Supersedes
[`tech-stack-recommendations.md`](./tech-stack-recommendations.md), which remains
the record of why option C was chosen for our own site.

## The brief this answers

| | |
|---|---|
| Our site | Next.js + Payload + Ecwid |
| Client stores | Duda white label + Ecwid |
| The constant | One Ecwid store, any front end |
| Our site build | 3–4 weeks |
| Client promise | Store live in 2 weeks |

## What the Ecwid detail actually buys us

Duda doesn't have its own store — it bundles Ecwid, and around 83% of all Ecwid
sites run on Duda. So when we sell a Duda store we are selling an Ecwid store with
a Duda front end on it.

The part previously missed: Ecwid is a widget, not a walled platform. It embeds in
anything, and there is an **official Ecwid plugin for Next.js** — a storefront
component and buy-buttons, maintained by Ecwid. The same store, with the same
products, orders, customers and settings, can appear on a Duda site or on a bespoke
React site we build.

That's not a small detail. It means the valuable half of a client's store — the
catalogue and the trading history, not the page design — is *never* locked to Duda.
And it means the two systems in the last revision, which were said to share
nothing, actually share the one layer worth sharing.

## The offer this makes possible

A genuine ladder rather than a single product with a ceiling. Same commerce engine
on every rung, so moving up is a redesign, not a migration — and nobody loses an
order history to climb it.

| | Rung 1 · DIY | Rung 2 · Hybrid | Rung 3 · Custom |
|---|---|---|---|
| | **Self-serve store** | **Managed store** | **Bespoke storefront** |
| What it is | Our Duda starter, our branding on the editor, client runs it day to day. The two-week promise and the volume business. | Same platform, but we do merchandising, content and SEO on a retainer. For clients who bought simplicity and then found they had no time. | We design and build a custom front end and embed their existing store in it. Every product, order and customer carries over untouched. |
| Front end | Duda | Duda | Next.js |
| Who runs it | Client, we set up + SEO | Us | Us, designed and built bespoke |

**Unchanged on every rung: one Ecwid store — products, orders, customers, payment
and tax settings.**

> **Why this matters commercially.** The usual problem with a productized entry
> offer is that our best clients outgrow it and leave. Here they climb instead, and
> the thing that normally makes leaving painful — moving the catalogue and order
> history — is exactly the thing we don't have to move. Rung 3 is also where our
> Next.js template and studio skills stop being decoration on the website and start
> being the premium product.

## Correcting the previous correction

Revision 2 said not to promise clients any portability, because Duda's export is a
static snapshot. That was right about the *site* and wrong about the *store*. The
accurate version is more nuanced, and better for us.

**The honest, sellable position:**

**Their store is genuinely theirs and genuinely portable.** Products, orders,
customers, tax and payment configuration live in Ecwid and can be lifted onto any
other website — including one we build them later, or one somebody else builds.
**The Duda page design is not portable**, and exports only as a static snapshot.
Say both halves plainly.

That's a stronger sales position than the vague "you own everything" most resellers
imply and can't back up. It's also true, which means it survives the conversation
where a client actually leaves.

> **One piece of fine print to check before relying on it.** Duda supports
> transferring a site to a different account, but where a store is attached the
> store plan is cancelled in the process and some connections drop, even though
> tax, shipping and payment settings are retained. Run that transfer once on a
> throwaway site during the trial so we know the exact steps before doing it live
> for a departing client.

## Whose Ecwid account is it?

The most consequential operational decision here, and easy to get wrong by default.
Ecwid supports staff accounts with their own logins and restricted permissions,
separate from the owner's billing and profile access — so both arrangements are
workable, and they say very different things.

**Client owns the Ecwid account, we hold staff access.** *Recommended.* The
ownership promise above becomes literally true, the client's payment settlement is
unambiguously theirs, and rung 3 is a clean upgrade rather than a handover. We keep
the work; we just don't keep the hostage.

**We own the account, client gets staff access.** Stickier and simpler to
administer at volume, and it's what the platform's design nudges us toward. But it
quietly contradicts the ownership story, and it makes every departure a
negotiation. Choose it deliberately if we choose it at all.

## What actually stays out of scope

The previous list was too long. Ecwid carries far more than credited — digital
goods, services, subscriptions and recurring billing, multi-channel selling into
social and marketplaces, real-time shipping rates, automated tax. Most of what a
small store needs is present. The genuine limits are narrower and more specific.

### Refer these elsewhere

- **True international multi-currency.** Ecwid converts prices for *display* but
  settles every order in the store's base currency, and doesn't show local currency
  at the final checkout step. A business genuinely selling into several currencies
  wants Shopify. This is the one hard limit worth memorising.
- **Very large catalogues** are a price question, not a capability one — the tiers
  ladder up to tens of thousands of products. Quote the tier, don't refuse the work.
- **Deep bespoke checkout logic** — unusual B2B pricing rules, complex
  quote-to-order flows. Possible via the API, but it stops being a two-week job.

### Say yes to these

- **Subscriptions, memberships, monthly boxes.** Native, not a bolt-on.
- **Digital downloads and service bookings** alongside physical goods.
- **Selling on Instagram, Facebook, Google Shopping and marketplaces** from the
  same catalogue — a strong upsell, and genuinely hard to do well without a
  platform.
- **Automated tax and live carrier shipping rates** at the appropriate tier.

> **Two questions on the sales call, not three.** How many products, and do you
> sell in more than one currency. The first picks the tier and our price; the
> second is the only one that can disqualify a prospect outright.

## Revised recommendation: put Ecwid on our own site too

Revision 2 said to use Stripe Checkout for our handful of packages, because a
custom cart was overkill. Stripe is still the simpler pure-commerce answer — but it
teaches us nothing and demonstrates nothing.

**Build meshuplabs.com as Next.js + Payload with an embedded Ecwid store instead.**
We sell packages and retainers through it, we learn the plugin on our own time
rather than a client's, and our own site becomes a live, inspectable example of
exactly what rung 3 looks like. When a prospect asks what a custom build gets them
over the self-serve tier, we answer by pointing at the page they're already on.

Cost is one entry-tier Ecwid plan and perhaps two days over the Stripe route. A
cheap reference implementation of our most profitable product.

## What doesn't change

The rest of the plan holds, and shouldn't be reopened — none of it is affected by
what's under Duda's bonnet.

- **Our site is still option C**, still 3–4 weeks, still Next.js and Payload from
  our existing template.
- **The two-week client delivery holds** as written, with the SEO redirect map on
  days 11–12 still the one genuinely unrecoverable step.
- **The white-label economics are unchanged** — a fixed monthly base that's
  punishing at one client and sensible at fifteen, so still don't subscribe until
  three or four are committed.
- **The "for now" habits still apply**: bill through our own Stripe, keep
  onboarding platform-agnostic, avoid custom widget work.

One habit from that list can be retired. Revision 2 suggested exporting every
client's product data monthly as our portable asset — that was insurance against a
lock-in that turns out not to exist at the store layer. Keep backups because
backups are sensible, not because we're planning an escape.

## Sources

Checked September 2026. Plan tiers and pricing move — confirm current figures with
Duda and Ecwid before setting package prices.

- [Ecwid Help Centre — Selling on Next.js websites](https://support.ecwid.com/hc/en-us/articles/4405894647186-Selling-on-Next-js-websites-with-Ecwid)
- [@ecwid/nextjs-ecwid-plugin](https://www.npmjs.com/package/@ecwid/nextjs-ecwid-plugin)
- [Ecwid Help Centre — Displaying prices in different currencies](https://support.ecwid.com/hc/en-us/articles/360000857760-Displaying-prices-in-different-currencies)
- [Ecwid Help Centre — Staff accounts](https://support.ecwid.com/hc/en-us/articles/115005355089-Adding-and-managing-staff-accounts)
- [Duda Support — Transfer a site to a different account](https://support.duda.co/hc/en-us/articles/26519246911639-Transfer-a-Site-to-a-Different-Account)
- [Duda Support — URL redirects](https://support.duda.co/hc/en-us/articles/26519925447703-URL-Redirects)
- [Duda — Plans & pricing](https://www.duda.co/pricing)

---

Ecwid is Ecwid by Lightspeed. Duda bundles it as the native store; this plan
assumes that continues.
