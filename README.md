# Evoxt New York VPS: Which Plan Do You Actually Need, What Latency Should You Expect, and Is the $2.99 Plan Enough? (Full 11-Plan Table)

Evoxt's New York location peers at NYIX and with multiple Tier 1 ISPs, and the lineup runs from a 512 MB box at $3.49/month to a 16-core, 32 GB machine at $95.99/month. Most people looking at this node should buy **VM-1 at $5.99/month**: 1 vCPU, 2 GB RAM, 20 GB storage, 300 GB monthly transfer.

What follows is the measured latency from a New York test VM, the full plan table, and the three step-ups in the lineup that are easy to overpay for.

> **Quick pick**
> - **Most readers: VM-1, $5.99/mo.** One WordPress site, a small API, a handful of Docker containers, or a WireGuard tunnel for a team.
> - **Proxy or tunnel only: VM-0.5, $3.49/mo.** 512 MB and 5 GB is enough for WireGuard and not much else.
> - **You know you need 4 GB: VM-2, $11.99/mo.** Same two cores as VM-1.5, double the RAM.
>
> 👉 [See the current New York plan list and checkout prices](https://bit.ly/EvoXt)

## All 11 plans, side by side

| Plan | vCPU / RAM / Storage | Monthly transfer | Price (USD/mo) | Best for | Order |
| --- | --- | --- | --- | --- | --- |
| VM-0.5 | 1 / 512 MB / 5 GB | 150 GB | $3.49 | Proxy, tunnel, DNS node | [Deploy VM-0.5](https://bit.ly/EvoXt) |
| VM-0.75 | 1 / 1 GB / 10 GB | 250 GB | $4.99 | Tiny Docker host, monitoring | [Deploy VM-0.75](https://bit.ly/EvoXt) |
| VM-1 | 1 / 2 GB / 20 GB | 300 GB | $5.99 | One WordPress site, small API | [Deploy VM-1](https://bit.ly/EvoXt) |
| VM-1.5 | 2 / 2 GB / 20 GB | 300 GB | $6.95 | Web process plus a worker | [Deploy VM-1.5](https://bit.ly/EvoXt) |
| VM-2 | 2 / 4 GB / 30 GB | 600 GB | $11.99 | App and database on one box | [Deploy VM-2](https://bit.ly/EvoXt) |
| VM-3 | 4 / 4 GB / 30 GB | 700 GB | $14.99 | Parallel jobs, several containers | [Deploy VM-3](https://bit.ly/EvoXt) |
| VM-4 | 4 / 8 GB / 60 GB | 1000 GB | $23.99 | Heavier app plus cache | [Deploy VM-4](https://bit.ly/EvoXt) |
| VM-6 | 8 / 8 GB / 60 GB | 1250 GB | $29.99 | Build agents, batch processing | [Deploy VM-6](https://bit.ly/EvoXt) |
| VM-8 | 8 / 16 GB / 80 GB | 2000 GB | $47.99 | Multi-tenant or mid-size DB | [Deploy VM-8](https://bit.ly/EvoXt) |
| VM-12 | 16 / 16 GB / 80 GB | 2500 GB | $60.95 | Heavy concurrent workloads | [Deploy VM-12](https://bit.ly/EvoXt) |
| VM-16 | 16 / 32 GB / 100 GB | 4000 GB | $95.99 | Production database, teams | [Deploy VM-16](https://bit.ly/EvoXt) |

Prices are monthly USD as listed on Evoxt's pricing page. Longer billing cycles exist (the pricing page mentions terms up to 3 years), but it doesn't publish the discounted rates, so you only see them in the cart.

One thing to clear up before you go further. Evoxt's homepage still advertises a "$2.99 plan" and promises that if you order it, you pay $2.99 with no bandwidth or CPU burst fees. The pricing page lists the smallest plan, VM-0.5, at $3.49. I can't reconcile the two from the pages themselves, and the cart is the only place that settles it. If the entry price is the whole reason you're reading, check it there first.

## What the New York location actually gets you

Evoxt connects this location to NYIX and peers with multiple Tier 1 providers, which is the same peering arrangement the company advertises for London (LINX), Paris (France-IX) and Amsterdam (AMS-IX). That matters more than a benchmark score for one reason: traffic to US East Coast networks and to Europe takes shorter paths.

The IP ranges check out as real data center space. A lookup of 23.27.125.0 returns New York City, ISP Evoxt, AS149440 Evoxt Sdn. Bhd., usage type Data Center/Transit, proxy type DCH, fraud score 3, and no anonymous proxy flag. A second address, 23.27.202.143, resolves to New York City on the same ASN with AS type Hosting and VPN not detected. Whether that matters depends on what you're doing: mail, ad verification, account logins and anything that gets scored on IP reputation behave better from a clean hosting range than from a flagged proxy pool.

A 2024 third-party test on a 2-core/4 GB New York VM gives the clearest picture of who this location is fast for:

| Target | Latency | Speedtest up / down |
| --- | --- | --- |
| Montreal, CA | 12.79 ms | 860.55 / 908.66 Mbps |
| Dallas, US | 36.09 ms | 1447.82 / 2722.87 Mbps |
| Los Angeles, US | 64.08 ms | 1251.86 / 2568.53 Mbps |
| Paris, FR | 82.87 ms | 839.40 / 6157.96 Mbps |
| Hong Kong, CN | 209.65 ms | 4.70 / 0.31 Mbps |
| Chongqing, CN | 277.08 ms | 19.55 / 1.55 Mbps |

The same test ran iperf3 from the VM: 7.61 Gbit/s receiving from a New York endpoint at 1.67 ms, 2.41 Gbit/s send to London at 74.9 ms, 2.55 Gbit/s send to Paris at 77.1 ms. One Dallas iperf3 run came back at 179 Mbit/s send with 158 ms, which looks like a bad run rather than a routing problem, since Speedtest to Dallas measured 36 ms.

Read the Asian rows twice. 209 ms to Hong Kong with 0.31 Mbps down is not a tuning issue, and 277 ms to Chongqing with 1.55 Mbps down won't carry a website for users in China. If that's your audience, Evoxt's Hong Kong location is the one built for it (the company advertises CN2 routing there), with Tokyo, Osaka and Seoul as the other regional options. Buying New York to serve Asia is the single most common mistake with this node.

## The benchmark numbers, and what they don't tell you

The same 2024 test, on a 2-core/4 GB Debian 11 KVM instance, produced these figures:

- Geekbench 6: **1167 single-core, 1966 multi-core**
- fio 4k mixed: 430.05 MB/s read, 431.19 MB/s write
- fio 512k: 888.98 MB/s read, 936.21 MB/s write
- fio 1m: 989.06 MB/s read, 1.05 GB/s write
- Basic I/O across three runs: 267, 827, 806 MB/s, averaging 633.3 MB/s
- Speedtest from the VM itself: 0.56 ms, 1253.16 Mbps up, 5443.05 Mbps down

These are third-party measurements of one instance in 2024, not Evoxt's official figures, and a different plan will score differently. The 4k numbers are the ones to watch: 430 MB/s at 4k is a fast drive, and it's the figure that affects database queries and small-file reads. The 1m write above 1 GB/s looks good on paper and rarely shows up in real workloads.

The CPU line in that test read **QEMU Virtual CPU version 2.5+ at 4199.984 MHz**. Two useful facts fall out of it. First, the clock speed is real, but it isn't the 6.0 GHz that Evoxt's marketing leads with; the pricing page says "up to 6.0 GHz," and this instance ran at about 4.2 GHz. Second, the CPU model is masked, so you can't confirm which generation of hardware you landed on before you buy. Evoxt markets 3.5 GHz and above as its floor, and that's the number to plan against.

## Which plan to pick, step by step

Evoxt's ladder has two kinds of steps: ones that buy memory and disk, and ones that only buy cores. Sorting them saves real money.

**VM-0.5 to VM-0.75 (+$1.50).** RAM goes from 512 MB to 1 GB, disk from 5 to 10 GB, transfer from 150 to 250 GB. 512 MB is below what a control panel or a normal Docker host wants, so this is the step from "toy" to "usable."

**VM-0.75 to VM-1 (+$1.00).** Another gigabyte of RAM, another 10 GB of disk, 50 GB more transfer. This is the best dollar-for-dollar move in the whole table, and it's why VM-1 is the default recommendation.

**VM-1 to VM-1.5 (+$0.96).** You get a second core. RAM, disk and transfer stay exactly where they were. A single WordPress site or one small API won't use that core, so the extra 96 cents buys nothing. Buy VM-1.5 when two processes have to run at the same time, such as a web server next to a queue worker.

**VM-1.5 to VM-2 (+$5.04).** RAM doubles to 4 GB, disk to 30 GB, transfer to 600 GB, and the core count stays at two. This is the step for the point where MySQL and PHP together stop fitting in 2 GB, not before.

**VM-2 to VM-3 (+$3.00).** Two more cores, no more RAM, no more disk. Only parallel work justifies it: compiling, batch jobs, several containers that each need CPU time.

**VM-3 to VM-4 (+$9.00).** RAM to 8 GB, disk to 60 GB. **VM-4 to VM-6 (+$6.00)** adds four more cores with the same 8 GB and 60 GB, so it repeats the VM-3 trap. VM-8, VM-12 and VM-16 jump to 16 GB, 16 GB with 16 cores, and 32 GB.

A single site running on VM-6 pays for seven cores it will never schedule, because PHP and WordPress are single-threaded per request. Evoxt sells clock speed, and clock speed stops helping once you have as many cores as concurrent requests.

There's also an upgrade path that doesn't require picking a new plan. Evoxt's pricing page says you can add individual resources (CPU, RAM, transfer) to an existing VM without changing plans. Starting at VM-1 and adding RAM later is usually cheaper than jumping to VM-2 on day one, as long as the add-on price in the console works out in your favor. Check that number before you commit.

## Where the New York node falls short

**Asia routing.** Covered above: 209 ms to Hong Kong, 277 ms to Chongqing, with download speeds under 2 Mbps in that test. Use the Hong Kong, Tokyo, Osaka or Seoul locations for that traffic.

**IPv6 is ambiguous.** Evoxt's site says every VM includes an IPv6 address. A 2023 test on a New York VM reported IPv6 offline. That test is old, and an instance can ship without the address configured rather than the product lacking it. If you need IPv6, log into the control panel after deployment and confirm it's there before you build anything on it.

**The bandwidth cap is listed but not explained.** The smallest plan gets 150 GB per month, VM-1 gets 300 GB, VM-2 gets 600 GB. Evoxt's homepage says it doesn't charge extra bandwidth fees, which is about surcharges, not about what happens at the cap. If you expect to run near the limit, ask support how it's enforced.

**Support is ticket-based.** A third-party review reports ticket responses stretching to 4–8 hours during busy periods, with Discord and Telegram moving faster. Treat that as one reviewer's experience, not a published SLA.

**No trial, and no refund window on the pricing page.** I found no free trial advertised and no refund period stated on the public pricing page. If a refund matters to your decision, read the terms of service and ask support before you pay, not after.

## FAQ

**New York or Los Angeles?**
New York for users on the US East Coast and in Europe. From the New York test VM, Paris was 82.87 ms and London 74.9 ms over iperf3. Los Angeles for West Coast and Asia-Pacific traffic. Evoxt connects Los Angeles to Equinix LA and Tier 1 providers.

**Can the $2.99 (VM-0.5) plan run WordPress?**
Not comfortably. 512 MB of RAM is where a PHP stack starts swapping, and the 5 GB disk leaves little room for uploads and backups. VM-1 at 2 GB is the realistic floor for a WordPress site.

**Is there a coupon code?**
Third-party pages list `EVOXT595` for 40% recurring off, but Evoxt hasn't confirmed it, and Evoxt's affiliate terms prohibit affiliates from posting coupon codes on coupon sites, which is why you won't find an official one. Treat any code you see as unofficial, try it in the checkout field, and budget for the list price.

**Does Windows cost extra?**
One third-party write-up says Windows and Linux are the same price with licensing included. Evoxt's own pricing page doesn't list a Windows surcharge, but it also doesn't promise one won't appear. Check the OS dropdown in the cart before you pay.

**Can I upgrade later without migrating?**
Yes. Evoxt's pricing page states you can add CPU, RAM and transfer to an existing VM without changing plans.

## The final decision rules

- Proxy, tunnel or DNS node only → **VM-0.5 at $3.49**, or VM-0.75 if you want 1 GB of headroom.
- One WordPress site, a small API, or a WireGuard tunnel for a team → **VM-1 at $5.99**.
- You already know 2 GB isn't enough → **VM-2 at $11.99**.
- Multi-threaded batch work, builds, several containers → **VM-3 at $14.99** and up.
- Serving users in Asia → skip this location entirely and pick Hong Kong, Tokyo, Osaka or Seoul.

Two things to confirm in the cart before you pay: the monthly transfer allowance for the plan you chose, and the current refund terms. Neither is fully spelled out on the public pricing page, and both are cheaper to check now than later.

👉 [Start with VM-1 in New York and confirm the price at checkout](https://bit.ly/EvoXt)
