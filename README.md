# DMIT Fontana: What the $100/Year LAX Eyeball Plan Actually Includes, Who It Suits, and How It Stacks Up Against Corona and the Monthly Tiers

Most people searching "DMIT Fontana" already know two things: it's a Los Angeles VPS from DMIT, and it costs $100 a year. What they usually can't pin down is what the name means, whether the stock is real, and whether this specific box beats the cheaper Corona sitting one row up in the same shopping cart.

Here's the short version before the details. Fontana is a limited-quantity promo plan in DMIT's Los Angeles Eyeball series, priced at $100/year for 2 vCPU, 2GB RAM, 40GB SSD and 4TB of monthly traffic on a 4Gbps port. It sells out, it gets restocked, and when it's gone the closest replacement is a monthly LAX.EB plan that costs more over a year.

## What "Fontana" means in DMIT's naming system

DMIT names the tiers inside a product line after California cities. Inside the Los Angeles Eyeball line the ladder runs WEE at the bottom, then CORONA, then FONTANA above it. The full plan name is usually written out as something like `PVM.LAX.EB.FONTANA` or `LAX.EB.FONTANA`, which decodes as:

- **PVM** — the virtual machine product family
- **LAX** — Los Angeles datacenter
- **EB** — Eyeball network profile
- **FONTANA** — the configuration tier

That "EB" is the part that matters most for buying decisions, and it's where a lot of the confusion comes from. DMIT sells three network profiles in Los Angeles: Premium (Pro), which includes China Telecom CN2 GIA; Tier 1 (T1), which is international routing with no China optimization at all; and Eyeball (EB), which sits in between. DMIT's own wording for Eyeball is that it makes a "reasonable effort" to route China-bound traffic over CMIN2 or comparable Chinese carrier networks. That phrasing is deliberate. Eyeball is not a guaranteed premium line the way Pro is, and it's not raw international transit either.

## DMIT Fontana specs and price

The configuration is consistent across DMIT's own listings and the reseller and coupon-tracking sites that mirror them:

| Item | LAX.EB.FONTANA |
| --- | --- |
| CPU | 2 vCPU |
| RAM | 2GB |
| Storage | 40GB SSD |
| Monthly traffic | 4,000GB, counted bidirectionally |
| Port | 4Gbps VirtIO |
| IPv4 | 1 |
| IPv6 | 1 × /64 |
| Price | $100/year |
| Routing | Eyeball (CMIN2 / AS9929 class) |

Two details are easy to miss in that table and they matter more than the CPU count.

The first is **bidirectional counting**. Upload and download both draw from the same 4TB pool. A plan that looks like it hands you 4TB is really closer to 2TB of "normal" usage if you're doing anything that pushes data both ways. Some providers only meter outbound; DMIT meters both on these plans.

The second is **what happens when the 4TB runs out**. You don't get shut off. The port drops to a throttle — low single-digit Mbps on the smaller plans, up to 10Mbps on the larger ones — and you keep going with unlimited traffic. For a personal proxy, a small site, or a sync box, that's a reasonable safety net. For a production service that needs real throughput at the end of the month, it isn't.

Traffic on Fontana was upgraded once already. When the plan launched it shipped with 2,500GB/month. DMIT later raised it to 4,000GB at the same $100/year, and doubled Corona from 1,500GB to 2,000GB while doubling its port speed from 1Gbps to 2Gbps. Whether that pattern repeats is anyone's guess, but it's worth knowing that the current spec is a raise, not the original offer.

## The routing, by carrier

Eyeball is a mixed bag depending on which Chinese ISP you're on, and this is the single biggest reason two people can have completely different experiences on the same plan.

- **China Mobile**: the strong case. CMIN2 on both outbound and return.
- **China Telecom**: CN2 GIA outbound, with CMIN2 or AS9929 handling the return depending on load.
- **China Unicom**: outbound over AS1299/Telia, return over CUG Premium (AS9929).

The return paths for all three carriers land on CMIN2 or 9929-class networks rather than ordinary transit. DMIT publishes a Looking Glass for the Los Angeles Eyeball node if you want to run your own traces instead of trusting a table, and the test IP commonly cited for this series is 154.17.226.2.

If your users are mostly on China Mobile, Eyeball is the profile that makes sense. If they're mostly on China Telecom and you need consistency rather than "reasonable effort," that's what the Pro profile exists for, and it costs more.

## Full LAX.EB lineup and pricing

Below is the Eyeball lineup as listed, split into the discounted stock-limited plans and the regular monthly plans. Prices change, stock moves, and the AMD platform generation (AS3 with EPYC 7003, AN4 with EPYC 9004, AN5 with EPYC 9005) shifts the monthly plans roughly 20% per generation — so treat the monthly figures as the current-generation listing and confirm on the order page before you pay.

### Discounted and stock-limited plans

| Plan | vCPU | RAM | SSD | Traffic/month | Port | Price | Order |
| --- | --- | --- | --- | --- | --- | --- | --- |
| LAX.EB.WEE | 1 | 1GB | 10–20GB | 800–1,000GB | 1Gbps | $39.90/year | [Check current WEE stock](https://www.dmit.io/aff.php?aff=12046&pid=188) |
| LAX.EB.CORONA | 1 | 1GB | 20GB | 2,000GB | 2Gbps | $49.90/year | [Check current Corona stock](https://www.dmit.io/aff.php?aff=12046&pid=218) |
| **LAX.EB.FONTANA** | **2** | **2GB** | **40GB** | **4,000GB** | **4Gbps** | **$100/year** | [Check current Fontana stock](https://www.dmit.io/aff.php?aff=12046&pid=219) |

### Regular monthly Eyeball plans

| Plan | vCPU | RAM | SSD | Traffic/month | Port | Listed price | Order |
| --- | --- | --- | --- | --- | --- | --- | --- |
| LAX.EB.TINY | 1 | 2GB | 20GB | 1,500GB | 2Gbps | ~$12.98/month | [See current Eyeball pricing](https://www.dmit.io/aff.php?aff=12046) |
| LAX.EB.Pocket | 2 | 2GB | 40GB | 3,000GB | 4Gbps | ~$18.90/month | [See current Eyeball pricing](https://www.dmit.io/aff.php?aff=12046) |
| LAX.EB.STARTER | 2 | 2GB | 80GB | 5,000GB | 10Gbps | ~$38.90/month | [See current Eyeball pricing](https://www.dmit.io/aff.php?aff=12046) |
| LAX.EB.MINI | 4 | 4GB | 80GB | 10,000GB | 10Gbps | ~$76.90/month | [See current Eyeball pricing](https://www.dmit.io/aff.php?aff=12046) |
| LAX.EB.MICRO | 4 | 4GB | 160GB | 14,000GB | 10Gbps | ~$99.90/month | [See current Eyeball pricing](https://www.dmit.io/aff.php?aff=12046) |
| LAX.EB.MEDIUM | 6 | 8GB | 160GB | 30,000GB | 10Gbps | ~$219.90/month | [See current Eyeball pricing](https://www.dmit.io/aff.php?aff=12046) |
| LAX.EB.LARGE | 8 | 16GB | 320GB | 50,000GB | 10Gbps | ~$459.90/month | [See current Eyeball pricing](https://www.dmit.io/aff.php?aff=12046) |

The MEDIUM and LARGE plans ship with 2 IPv4 addresses; the smaller ones ship with 1. All of them include an IPv6 /64, KVM virtualization, standard DDoS protection, and the option to add RAM or SSD. Plans with 4GB of RAM and up are the ones DMIT supports for Windows, so a 2GB Fontana is a Linux box.

## Fontana versus Corona versus WEE

The honest comparison: Fontana costs exactly twice what Corona costs, and it gives you twice the cores, twice the RAM, twice the storage, twice the traffic and twice the port speed. If that sentence reads suspiciously neat, it's because DMIT priced it that way on purpose.

So the decision is less about value-for-money between the two and more about what you're running:

- **WEE ($39.90/year)** — lowest ceiling, 1Gbps port, under 1TB of traffic. Fine for a single lightweight proxy or a tiny personal site. It's also the plan that vanishes fastest and comes back with the smallest allocation.
- **Corona ($49.90/year)** — $10 more than WEE for double the traffic and double the port. For most people who just want a personal node, this is the sensible stopping point.
- **Fontana ($100/year)** — the pick when 1GB of RAM keeps running out. Two cores and 2GB handle a small WordPress install, a Docker stack, a database, or a handful of concurrent services without swapping. 4TB of bidirectional traffic on a 4Gbps port is genuinely generous at this price.

Here's the comparison that usually settles it. Fontana is $100/year. Pocket is $18.90/month, which is roughly $227/year for a similar 2-core/2GB/40GB shape — the differences being 3TB instead of 4TB of traffic, no annual discount, and no stock lottery. Fontana's real advantage isn't its raw specs relative to Pocket. It's the annual billing. You're trading availability for price.

That trade is the whole story of this plan. Fontana exists as a limited-quantity offer, not a permanent product. When it's in stock it's the best price-per-GB-of-RAM in the Eyeball line. When it's out, it's simply out, and the regular monthly tiers are what you buy.

## Before you buy: stock, IPs, refunds, payment

A few operational details that aren't obvious from the product page.

**Stock is genuinely limited.** Resellers that track DMIT inventory note order caps on the promo plans, and unpaid orders get cancelled automatically after a few hours. If you're waiting on a restock notification, don't sit on the cart.

**IP replacement is built in.** If your assigned IP gets blocked, DMIT's terms for these plans allow a free replacement roughly every 15 days. This is one of the practical differences between a provider that treats blocked IPs as a support cost and one that treats them as your problem.

**The refund window is short but real.** Reported terms: a full refund within 3 days if you've used under 30GB of traffic, and a prorated refund within the first month with the payment gateway fee deducted. DMIT publishes its refund documentation publicly, so read that page before assuming the terms — it's the authoritative source, not a forum post.

**Payment options cover the usual bases** — Alipay, PayPal, and credit card via Stripe. That Alipay support is a big part of why this provider gets discussed so heavily in Chinese-language hosting communities, and it's worth knowing if that's how you prefer to pay.

**Hardware generation varies.** DMIT has run AS3, AN4 and AN5 hardware in Los Angeles. AN4 stock was withdrawn at one point and AN5 was later re-listed at higher prices. If you specifically care which EPYC generation you land on, the order page is the only reliable place to check, because the platform isn't part of the plan name.

## Where Fontana doesn't fit

Three honest limitations.

It's not a premium China route. If your traffic is China Telecom-heavy and latency consistency is the whole reason you're buying, Eyeball's "reasonable effort" language is a warning label, not a marketing phrase. Pro is the profile designed for that, and it costs more.

Two gigabytes of RAM is a ceiling, not a floor. It's comfortable for a personal stack and tight for anything with a JVM, a busy MySQL instance, or a build pipeline. DMIT lets you add RAM and SSD, but once you're customizing a $100/year plan upward you should be comparing against Pocket and Starter on monthly billing.

And the annual commitment is real. Paying $100 up front for a plan that only exists during restock windows means you don't get to reassess in three months. If you're not confident the workload is staying put for a year, the monthly tiers are the lower-risk entry.

## Questions people actually ask about Fontana

**Is Fontana still available?** It comes and goes. The link above checks the current pid, and if it's out of stock you'll see that immediately rather than after adding it to a cart.

**Is $100/year a promotional price that expires?** The plan itself is the promotion. DMIT hasn't signaled that the $100 figure is time-limited separately from stock availability, but treat any annual price as something to verify at checkout rather than quote from an article.

**Can I run Windows on it?** Not on 2GB. DMIT's Windows support starts at 4GB of RAM, which means MINI and up.

**What happens if I hit 4TB in a month?** The port throttles and traffic becomes unlimited. You keep the server; you lose the speed.

**Does Eyeball guarantee CMIN2?** No, and DMIT doesn't claim it does. The profile description says CMIN2 or similar Chinese carrier routes on a reasonable-effort basis. Mobile users most consistently see CMIN2 in both directions; telecom and unicom involve CN2 GIA, AS9929 and AS1299 depending on direction and load.

## The bottom line

Fontana is the sweet spot of DMIT's Los Angeles Eyeball promo trio. WEE and Corona cover the cheap personal-node use case; Fontana is the one that's actually a small server rather than a proxy with a filesystem, and at $100/year it undercuts the monthly tiers by more than half on a like-for-like basis.

The catch is that the price is tied to scarcity. There's no version of this where you decide today, spend three weeks comparing options, and still find it in stock at $100. If you're in the market for a 2-core/2GB Los Angeles box with China-optimized return routing and you're comfortable paying annually, it's worth checking availability now. If you need guaranteed routing quality or month-to-month flexibility, skip it and look at the monthly Eyeball tiers or the Pro line instead.

👉 [Check DMIT Fontana price and current stock](https://www.dmit.io/aff.php?aff=12046&pid=219)
