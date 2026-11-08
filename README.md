# Linux dedicated server: what it really costs at SpinServers, when bare metal beats a VPS, and which of the 11 builds to pick (all configs side by side)

SpinServers' cheapest Linux dedicated server is **$55 a month** in San Jose: a dual Xeon E5-2630 v2 with 64 GB of DDR3, one 240 GB SSD and 30 TB of monthly transfer on 2 × 10 Gbps ports. For most people running one busy application, the **$79 build** is the better spend, because it swaps all those old cores for an E3-1280 v5 at 3.7 GHz and a 1 TB NVMe drive. Both are month-to-month, and neither is refundable, so read the billing section before you pay.

Below are all 11 configurations currently listed across Dallas and San Jose, what each spec actually buys you for a Linux workload, where the money goes compared with a VPS or a cloud instance, and the questions worth sending to support before you commit.

> **Quick pick:** one Linux app server, moderate traffic, no virtualization → Intel Xeon E3-1280 v5, 32 GB RAM, 1 TB NVMe, from $79/month. Running VMs, heavy containers or a database with a large working set → SJC-204, 32 cores / 64 threads, 512 GB RAM, 2 × 3.84 TB SSD with a battery-backed RAID controller, $250/month, which works out to about $0.49 per GB of RAM. 👉 [See the current SpinServers dedicated server listings](https://bit.ly/Spinservers)

## The full lineup: four builds in Dallas, seven in San Jose

Both locations run enterprise hardware with ECC memory and a 30 TB monthly transfer allowance. Dallas carries the high-core-count dual Xeon Scalable machines; San Jose carries the cheap 64 GB and 512 GB boxes plus the same $79 E3 entry build.

**Dallas, Texas**

| Build | CPU (total cores / threads) | RAM / storage | Port & transfer | From (USD/mo) | Order |
| --- | --- | --- | --- | --- | --- |
| Intel Xeon E3-1280 v5 | 4 / 8, 3.7 GHz | 32 GB DDR4 ECC / 1 TB M.2 NVMe | 10 Gbps, 30 TB | $79 | [View build](https://bit.ly/Spinservers) |
| Dual Intel Xeon E5-2630L v3 | 16 / 32, 2.9 GHz | 128 GB DDR4 ECC / 1 TB NVMe | 10 Gbps, 30 TB | Quoted per build | [View build](https://bit.ly/Spinservers) |
| Dual Intel Xeon Gold 6148 | 40 / 80, 3.7 GHz turbo | 256 GB DDR4 / 2 × 1.92 TB SSD | 2 × 10 Gbps LACP, 30 TB | Quoted per build | [View build](https://bit.ly/Spinservers) |
| Dual Intel Xeon Platinum 8173M | 56 / 112, 3.5 GHz turbo | 512 GB DDR4 / 4 × 1.92 TB SSD | 2 × 10 Gbps LACP, 30 TB | Quoted per build | [View build](https://bit.ly/Spinservers) |

The $79 figure is the listed Dallas starting point and belongs to the E3-1280 v5 build. The three larger dual-Xeon configurations are priced individually on their own listing entries rather than in a single flat table, so pull the quote for the exact build you want instead of assuming a linear step up.

**San Jose, California**

| Build | CPU (total cores / threads) | RAM | Storage | From (USD/mo) | Order |
| --- | --- | --- | --- | --- | --- |
| SJC-207 | Dual E5-2630 v2, 12 / 24, 2.6 GHz | 64 GB DDR3 ECC | 1 × 240 GB SSD | $55 | [View build](https://bit.ly/Spinservers) |
| SJC-205 | E3-1280 v5, 4 / 8, 3.7 GHz | 32 GB DDR4 ECC | 1 × 1 TB NVMe | $79 | [View build](https://bit.ly/Spinservers) |
| SJC-202 | Dual E5-2630L v3, 16 / 32, 1.8 GHz | 64 GB DDR4 ECC | 1 × 1.6 TB SSD | $115 | [View build](https://bit.ly/Spinservers) |
| SJC-206 | Dual E5-2630L v3, 16 / 32, 1.8 GHz | 64 GB DDR4 ECC | 1 × 1.6 TB NVMe | $155 | [View build](https://bit.ly/Spinservers) |
| SJC-201 | Dual E5-2630L v3, 16 / 32, 1.8 GHz | 256 GB DDR4 ECC | 2 × 1.6 TB SSD, hardware RAID | $225 | [View build](https://bit.ly/Spinservers) |
| SJC-203 | Dual E5-2650L v3, 24 / 48, 1.8 GHz | 64 GB DDR4 ECC | 1 × 1.6 TB SSD | $225 | [View build](https://bit.ly/Spinservers) |
| SJC-204 | Dual E5-2683 v4, 32 / 64, 2.1 GHz | 512 GB DDR4 ECC | 2 × 3.84 TB SSD, battery-backed RAID | $250 | [View build](https://bit.ly/Spinservers) |

All seven San Jose builds are listed as instant provisioning and come with a 30 TB monthly transfer allowance on 2 × 10 Gbps ports.

## What these specs actually buy you

**The prices are low because the silicon is old.** Every San Jose build except SJC-204's Broadwell-era E5-2683 v4 uses Xeon E5 v2 or v3 parts, and the $55 machine runs DDR3. Those chips give you a lot of cores and cheap memory, but the base clocks sit between 1.8 and 2.6 GHz, and single-thread performance is well behind a current Xeon or EPYC. For a PHP site, a queue worker fleet or a container host that is throughput-bound, that trade is fine. For anything latency-sensitive per request (game servers, real-time APIs, compile-heavy CI), the E3-1280 v5 at 3.7 GHz will feel faster than a 16-core E5-2630L v3 at 1.8 GHz despite having a quarter of the threads.

**Memory is where the value concentrates.** Divide the monthly price by RAM and the ordering changes completely:

- SJC-204: $250 for 512 GB, roughly **$0.49 per GB**
- SJC-207: $55 for 64 GB, roughly $0.86 per GB
- SJC-201: $225 for 256 GB, roughly $0.88 per GB
- SJC-202: $115 for 64 GB, roughly $1.80 per GB
- SJC-203: $225 for 64 GB, roughly $3.52 per GB

SJC-203 and SJC-201 cost the same $225. One gives you 24 cores and 64 GB on a single SSD; the other gives 16 cores, 256 GB and a hardware RAID pair. If you are building a virtualization host or a database with a large page cache, SJC-201 is the obvious pick. If your workload is core-bound and small in memory, SJC-203 is.

**Redundancy is the exception, not the rule.** Only SJC-201 and SJC-204 include a hardware RAID controller with multiple drives. The $55 to $225 single-disk builds have no mirror, so a drive failure means a rebuild from your own backups. Budget for a backup target outside the box, and ask support what drive replacement looks like in practice before you put anything production-critical on a single-SSD plan.

**30 TB on a 10 Gbps port is not unmetered bandwidth.** Spread 30 TB evenly across a month and you average roughly 93 Mbit/s sustained. The 10 Gbps port is there for bursts, image pushes and short traffic spikes, not for running a sustained multi-gigabit stream. Ask what happens past 30 TB and what an overage costs, because that number decides whether a media-heavy workload belongs here at all. 👉 [Check the port, transfer and overage details on the listings](https://bit.ly/Spinservers)

## Linux dedicated server vs VPS vs cloud instance

The difference that matters is what happens when your neighbour gets busy.

| Dimension | Dedicated server | VPS | Cloud instance |
| --- | --- | --- | --- |
| Performance isolation | Full, no noisy neighbours | Shared hypervisor | Shared, variable |
| Resource guarantee | 100% of CPU, RAM, disk | Partial, burst | Soft limits, throttling possible |
| Cost model | Fixed monthly | Fixed monthly | Usage-based |
| Scaling | Vertical, hardware swap | Vertical within the host | Horizontal, near-instant |
| DDoS protection | Usually included at L3/L4 | Provider-dependent | Often an add-on |
| Provisioning | Provider-dependent | Minutes | Seconds to minutes |

A dedicated box earns its price in three situations: you need guaranteed CPU and RAM without a hypervisor in the way, you need full root control down to kernel parameters and SELinux/AppArmor policy, or you need single-tenant hardware for GDPR, HIPAA or PCI-DSS reasons. A $55 SpinServers machine with 64 GB of RAM is also simply cheaper than most cloud instances with comparable memory, which is why memory-heavy but compute-light workloads end up on old dual Xeons.

A VPS wins when you need a clean Linux box for a site that gets a few hundred visitors a day, when you want snapshots and one-click resizes, or when your budget is under about $30 a month. Cloud wins when traffic is spiky and you would rather pay for 40 minutes of 64 cores than for a month of 16. If you cannot name the CPU model you need, you probably do not need bare metal yet.

## Which Linux distribution to install

SpinServers does not lock you into a proprietary image, so the choice is yours to make on support lifecycle.

| Distribution | Support window | Pick it when |
| --- | --- | --- |
| Ubuntu Server LTS | 5 years standard, extendable to 10 | Web apps, containers, the widest documentation |
| Debian stable | ~5 years per release | You want a minimal, quiet server that rarely changes |
| RHEL | 10 years | Compliance, certification, vendor-supported stacks |
| AlmaLinux / Rocky Linux | Follows RHEL | RHEL compatibility without the subscription |
| SUSE Linux Enterprise Server | 10–13 years | SAP, high-availability clusters |
| CentOS Stream | ~5 years | Dev/test and previewing what lands in RHEL next |

For most of the builds above, Ubuntu LTS is the default answer, with Debian if you want fewer moving parts. On the 512 GB SJC-204 running KVM or Proxmox, check that your chosen host distribution has driver support for the RAID controller before you install, and confirm with support which stock images are available for automatic provisioning versus manual install.

Every mainstream Linux distribution here is free of licence cost, which is part of why a dedicated box is predictable: a fixed monthly rate with no per-core Windows licensing to absorb, and no usage meter running in the background.

## Network, SLA and DDoS: what the plan cards don't tell you

The listings give you cores, RAM, disk, port speed and transfer. They do not give you the routing or the paperwork, and those are what you are actually relying on at 3 a.m.

Ask support for four things in writing:

1. **Whether the provider runs its own autonomous system** and peers at internet exchanges. Own AS plus Tier 1 upstreams plus IX peering is what gives you a second path when a transit link drops, and it shows up directly in latency to your users.
2. **An SLA figure with teeth.** 99.9% monthly uptime is the normal floor for dedicated hosting. What matters more is the hardware replacement commitment: how many hours until a failed RAM stick or drive is swapped, and whether that is in the contract or just in a sales reply.
3. **Whether DDoS mitigation is included by default** at layer 3/4, or sold as an add-on. Baseline always-on filtering is a different product from scrubbing on request. No provider can honestly promise 100% DDoS protection, and the ones that admit it are easier to trust on everything else.
4. **Overage, extra IPv4 addresses, setup fees and the exact renewal rate.** A monthly list price is not a contract rate. Ask whether the price you see is locked for any period.

## Refunds and billing: assume no refund on month-to-month

SpinServers' own refund policy is blunt. Month-to-month services are **not refundable**, with the exception of SLA credits on a cancelled service. The company says it may issue a refund at its discretion if you are unhappy, but states plainly that it is under no obligation to do so, and that any reversal can take up to 48 hours to complete.

That changes how you should buy. Order the smallest build that could plausibly do the job for one month, benchmark your actual workload on it, and only then commit to a bigger machine. A $55 or $79 month is a cheap evaluation; a $250 machine you cannot return is not. If you sign up on a quarterly or annual term instead of monthly, get the cancellation window in writing before you pay, since the notice requirement sits in the billing terms rather than on the plan card. 👉 [Read SpinServers' plans and terms before you order](https://bit.ly/Spinservers)

## How SpinServers compares with IONOS, Netrouting and Atlantic.Net

All three of these publish specifications worth knowing about. The details below are the providers' own descriptions, not independent benchmark results.

| Provider | What they publish | Where it fits |
| --- | --- | --- |
| IONOS (UK) | Linux or Windows dedicated servers, 1 Gbit/s standard with unmetered traffic, on-demand rental with no minimum term, servers available minutes after purchase, KVM VNC console, included wildcard SSL. States that 100% DDoS protection is not currently possible, and that Hyper-V cannot be used on their dedicated plans for licensing reasons. | Buyers who want a short commitment and a big support organisation |
| Netrouting | Xeon and EPYC bare metal, up to 2 TB RAM and 24 drives with hardware RAID, Linux provisioned in under 60 minutes, 99.9% SLA, 24/7 NOC with a one-hour ticket target, unmetered 10 Gbps, own AS 6206, 10 locations | Workloads where unmetered bandwidth and many locations matter |
| Atlantic.Net | Full root access, a choice of distributions, dedicated IPs, hardware RAID options, SSD or NVMe storage, 24/7 US support, optional managed services covering patching, backup and monitoring | Teams without a full-time sysadmin who want management on top |

IONOS is the short-commitment, high-bandwidth option; Netrouting competes on network capacity and locations; Atlantic.Net sells management. SpinServers competes almost purely on price per core and price per gigabyte of RAM, which is why its catalogue is dominated by older Xeons.

## Who should not rent one of these

If your site gets a few thousand visits a month, a $10 VPS will serve it fine and you will never notice the noisy neighbours. If your traffic doubles unpredictably every few weeks, cloud auto-scaling handles that better than swapping hardware. If you need a managed server with someone else patching the kernel, a managed provider is the right purchase even at two or three times the price. And if your application depends on high single-core clock speed across many cores, none of the E5 v2/v3 builds here will satisfy you, regardless of how many threads the listing shows.

For everyone else, the decision comes down to four rules:

- **One Linux application server, normal traffic** → E3-1280 v5 at $79/month. High clock speed, NVMe, instant provisioning, lowest regret.
- **Virtualization host, many small VMs, or a large database cache** → SJC-204 at $250/month. 512 GB and 32 cores for less than most cloud quotes for the memory alone.
- **Cheapest possible box for backups, a test lab or a low-traffic mirror** → SJC-207 at $55/month, accepting DDR3 and no disk redundancy.
- **Core-heavy batch processing on a budget** → SJC-203 or the Dallas dual Xeon Gold 6148, depending on whether you need 24 cores at $225 or 40 cores at a higher quote.

Before you pay, confirm two things: the exact CPU model and generation on the build you are ordering, and the renewal price plus overage rate in writing. Those two answers separate a good deal from an unpleasant second invoice. 👉 [Start with the SpinServers configuration that matches your workload](https://bit.ly/Spinservers)
