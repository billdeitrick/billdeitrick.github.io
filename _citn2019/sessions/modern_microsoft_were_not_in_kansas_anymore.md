---
presenter: Karl Peterson, Vibrant
type: session
title: Modern Microsoft - We're Not in Kansas Anymore
index: 6
---

## Presenter's Notes

https://vibrant.cloud/citn2019
[Slides](https://static1.squarespace.com/static/5bd21cb7755be22a659bd2e2/t/5dacdad625e2af536e043f2b/1571609308035/Modern+Microsoft+-+CITN.pdf)
[Notes](https://static1.squarespace.com/static/5bd21cb7755be22a659bd2e2/t/5dacdb07aa1e3231b4d3cb3f/1571609351636/Modern+Microsoft+Notes+-+CITN.pdf)

## Introduction

* Changes are trending broader; greater fundamental shifts (identity systems, core infrastructure)
* Low awareness/understanding of modern ecosystem (things changing so fast, people don't have time to keep up)
    * Divergence between knowledgebase and products (pace of change!!)
* We exist to equip our organization for success
    * **Help Great People do Greater things**
* This is a reference point for Modern Microsoft -- workplace enablement
* How to digest all of this (so much change, tools have such a broad scope!)

**Results matter more than tools!**

* Modern solutions are results-focused
    * Not tools-focused; we don't serve tools, tools serve us

## Setting the Stage - Where is MS Coming From?

* Microsoft seeing significant failures...
    * failure to build mobile platforms
    * Windows losing market share
    * Exchange -> Google apps
    * "Less Cool"

## The Comeback

* Focus on:
    * Culture, people, results (instead of tools)

## Modern areas of focus

* Trust, collaboration, mobility, inteligence

### Update in 2018

* creativity, teamwork, simplicity, security
* MS basically doesn't care about selling servers and/or Surface Books anymore...they want to sell 👆
* There is tension between these results!
    * Tools that don't actively deliver results will be changed or replaced

## Example Environments

* Classify by complexity: simple / moderate / complex
    * There is time to deliberately migrate over a reasonalb eime period, but we need to be looking more like "Modern Microsoft" in the next 3 years

## Simple Environment

* No need for on-prem servers, except local NAS
* No Windows server, traditional AD
    * Purely modern SaaS solutions!
* Less than 10 non-microsoft SaaS in use
    * Little use for Windows machines other than user-allocated

## Solutions

* M365, Windows devices managed with Microsoft 365 device management
* Using Microsoft Update for patching
* Windows Hello for auth
* Autopilot for provisioning new Windows machines
* Mac/iOS/Android enrolled/managed w/Intune
* SSO for third-party devices...

## Moderate environment

* Differences from simple environment

* No need for on-prem servers, except local bulk storage
* More need for Windows server, other uses for Windows devices 
* Users have M365E3
* M365F1 licenses shared devices (Kiosks, conference rooms, etc.)

## Solutions

* Adding Windows analytics + Azure storage for patch monitoring
* We do have some Active Directory needs (Domain Services)
* Virtual servers in Azure/storage in Azure
* Azure update manager
* Azure managed SQL
* Azure backup for Servers/storage/SQL
* PowerBI reports and alerts on everything!
* Options for on-prem if needed

## Complex Environments

* Still need on-prem servers and Windows Server
* Need traditional AD
* Mix of modern/traditional apps
* Windows machines for more than just direct users
* Regulatory/internal policies compliance and significant security demands
* Users licensed with M365E3 + E5 security, or going straight to M365E5
* Windows devices managed with Intune, Hybrid AD enrolled

## Solutions

* Still have VMs on-prem
* Need specific solutions for connectivity to Azure
* AADConnect w/federation services
* Backup on-prem, duplicated to Azure
* Realtime protection/replication to Azure (or replicate to another datacenter)
* High availability and fast failover!!
* PowerBI again, with local gateway for analytics

## Modern Environments - Results

* Automated and fast workstation deployment
* Best-in-class data security
* Availability baked in
* Sharing built-in
* Passwordless future
* 60 to 70% reduction in management!! 🎉

## Licensing/Cost

* Usage-based
* Things increasingly moving away from VLSC
* Licensing can be purchased yearly or longer, so this helps
* Planning for cost/budgeting is important!
    * These are results you want, these are what you need to pay to get them
    * If we can't afford this, we need to adopt a different plan
* **Justify budgets on value delivered!**

## Change

* ...is inevitable!!
* Avoiding change isn't good...
    * Disruption isn't good, but we can't stay still
* We need to focus on affecting change for the better!
* We need to understand our organizations needs and our solutions to meet them
    * **Provide change that delivers meaningful results!!**

## Constant learning

1. Practical Learning
    * Learn being better at something you already to
    * Learn something directly related to what you already new
1. Exploratory Learning
    * different ways to do what you aready do
    * something brand new
1. Challenging Learning
    * Learn something that will challenge you!
1. What ever you do -- be consistent!
    * Regular improvement will lead to someplace better

## Be ready to let go

* everything has a lifespan
    * recognize when that lifespan passes
    * let it go!!
* We are stewards of change

## Conclusions

* Results of tools
* Simplify environments whenever possible
* Build complexity responsibly
* Budget well, justify on value/results
* Accept change as inevitable, make sure it's for the better
* All good ideas have a live, be attuned to its end

## Q+A

* Self-holding encryption keys
    * Not applicable for almost everything
* Windows Virtual Desktop Service
    * Virtual desktops in the cloud, at scale, and relatively affordable
* SSO for third-party platforms
    * Can enroll third-party platforms in Intune
    * Some asterisks there...
    * Company Portal App provides launching pad for this
