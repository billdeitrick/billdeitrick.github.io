---
layout: citn2019
title: Talk Outline - All-in with Azure AD, Intune, and Office 365
permalink: /citn2019/outline/
---

1. Introduction
    1. About Me
       1. Professional: Information Services Director for CWC, CS degree from Houghton College, been getting paid to do IT in one form or another for the last 9 years or so; experience working in Higher Ed, a bit in Fortune 500, and NPO
       1. Personal
    1. Overview
       1. I’m going to be sharing an IT Director’s perspective on moving from a traditional Microsoft Active Directory environment in a ministry setting to one powered by Azure AD, Intune, and Office 365
          1. We’ll focus mostly on identity management with Azure AD and Windows device management with Intune
          1. Our Intune discussion will be limited to managing Windows, but we’ll talk about how we’re leveraging Azure AD to provide multi-platform authentication
          1. Not going to talk as much about O365, since many of us are already familiar and are likely living there (at least somewhat) already (and there’s lots of other opportunity here to learn about O365) 
       1. Goal is to share our experience, and I’m hopeful that you’ll leave better equipped to apply Azure AD and Intune as appropriate in your environment.
          1. This won’t be an exhaustive treatment of everything Azure AD and Intune; there’s just too much to cover
          1. I’ll try to cover what I think will be most relevant coming from managing Windows devices with traditional AD; I'll hit a lot of topics briefly, and I've tried to provide links, examples, and further comments with the notes as specified on my website
       1. I am not an Azure AD and Intune expert; I’m sharing based on my experience in my environment. I don’t know the best practices to apply these tools in every scenario, or the ins-and-outs of every situation.
          1. So, I’ve asked some of our vendors to join us…they’ll be able to provide insights from their perspectives working across many different clients (and, I’m sure, be quite happy to help you if you’d like some more hands-on assistance getting up and running with these platforms)
          1. I'm also going to try to avoid being "prescriptive" for your environment; I don't feel like I have the experience with these tools in enough environments to make recommendations for yours--I'll leave that to our vendors. I will speak from the perspective of the choices we made and why we made them.
1. 👉Our Environment
   1. Church
      1. PCs, Macs, Chromebooks, and iPads
      1. ~65 employees
      1. PC-dominated, moving to mix of PC, Mac, and Chrome
         1. (We're just starting offer pastors and directors choice of device)
      1. Traditional AD environment (with AADConnect); moving to Azure AD/Intune only
         1. Using Azure AD as auth source for G Suite and Chromebooks (more on this later)
   1. School
      1. PCs, Chromebooks and iPads
      1. ~65 employees, ~400 students
      1. Employees all use PCs, students use Chromebooks (one-to-one for high school) and iPads
      1. Fully transitioned into an Azure AD-only environment
         1. Azure AD and G Suite accounts for all employees and students
         1. Azure AD provides authentication for staff PCs, student ChromeBooks (so students log into Chromebooks using Azure AD credentials)
         1. School used to live in the same AD and Office 365 tenant as the church; this summer we completed moving the school to their own education tenant and moving to Azure AD as central identity source
1. 👉Your Environments
   1. Totally in the MS cloud?
   1. Using AADSync and pushing identities up for O365?
   1. Managing devices with Intune?
   1. Managing non-windows devices with Intune?
   1. Using hybrid joined devices (Intune and On-prem AD)?
1. 👉Why Azure AD and Intune?
   1. This audience is no stranger to the draw of SaaS, PaaS, and all of those cloudy buzzwords
      1. So, of course we're attracted by the usual suspects: reduced maintenance overhead, fewer things we have to fix when they break, less time managing infrastructure and more time delivering ministry value
         1. Ministry value is the key; anything that better delivers ministry value is a win! 🎉
      1. Our specific scenario:
         1. Church and school environments had long shared infrastructure. With licensing changes, and education-focused products from Microsoft, it was time to move the school completely to their own environment with education-SKU products
         1. Originally this move was going to be to two traditional on-prem AD environments with a trust between them
            1. But this felt like overkill. This meant more servers to maintain and license, which felt like moving backwards rather than forwards
         1. Then we considered G Suite and ChromeBooks only for the school (we love the lightweight Chrome experience), but we had major limitations with classroom hardware by going Chrome only, not to mention decades worth of data in Microsoft formats and staff with years of experience using Microsoft tools
            1. So we couldn't get away from PCs...we considered moving identities to G Suite, but we needed PCs and Azure AD doesn't allow identities to be mastered in another platform (and there doesn't seem to be a good solution to this, without introducing other platforms/providers in the mix)
         1. So the conversation came around to Azure AD + Intune, and ultimately moved to a "why not"? After kicking the tires, this seemed like the best solution, giving us the management tools and flexibility we wanted
   1. 👉Best fit for ministry needs within licensing and cost constraints
      1. No need for more servers, best flexibility to provide authentication across variety of platforms
      1. We want to live in a world where we have as small on-prem server footprint as possible (and as much as possible is containerized and lives on hardware someone else owns--but that's a topic for another day); that world includes minimal or no Windows servers on-prem
   1. 👉Better Windows device management: NO MORE DEVICE IMAGING!! 🎉
      1. We'd long used FOG for building images...a labor intensive and time-consuming process
      1. With Windows 10 and Intune, and Auto Pilot, we don't need to build images anymore. 
   1. 👉SSO for SaaS apps
      1. Azure AD makes SSO for SaaS apps really easy...like, really easy. This sort of thing used to require major infrastructure and investment.
      1. We love the seamless experience for our users; this goes beyond apps that we've explicitly provisioned for SSO.
      1. Since we're authenticating G Suite against AAD, our users can sign in with their accounts anywhere the see a "Sign in with Office 365" or "Sign in with Google" button
   1. 👉Device-agnostic, user-driven, available-from-anywhere experience
      1. We want our users to be completely interchangeable with PC, Mac, Chromebook, or a mobile device and be able to sign in with immediate access to all of their data on that platform
      1. We want as much user state to be transferred as possible, so there's relatively little (other than signing in) that a user needs to do to be immediately up and running on a new device
      1. We want the experience across platforms to be as "self-service" as possible--we push apps and settings that are needed by all, users can install what they need themselves (without having local admin unless required by their role)
      1. We wanted to make sure our users have first available-anywhere productivity available. VPN provided this in the past, but there's nothing about the UX I would call "first class". If we don't provide this, our users will go and get it elsewhere (and take our data with them). We have the policy in place, but want it to be an easy one to enforce.
      1. The bottom line: in terms of device management, we want to manage Windows devices more like they're Chromebooks. I think it's clear that, this is ultimately Microsoft's target with Modern managment, and we've found ourselves reaching for Chromebooks as a default less and less becuase of the positive experience with Windows 10 and modern management.
   1. 👉More forward-looking solution
      1. All the momentum is with the cloud products at this point; with constant enhancements and licensing changes, it's clear that Microsoft sees their cloud offerings as the path forward for the majority of organizations (especially ones of our size)
1. 👉M365: Two Minute Overview
   1. Microsoft 365 is basically the license that gets you access to all of the Modern Microsoft Management services. We'll talk about the major components here in turn.
   1. Most of you are already familiar with MS NPO offerings, so I won't spend a lot of time here; check out the talk notes for links that will get you started with NPO
      1. Bottom line is, you can expect to pay about 25% of the commercial price for most licenses as NPO
   1. 👉Office 365 ProPlus
      1. Local office apps
   1. 👉Office 365 - E1, E3, E5
      1. The office 365 cloud services
      1. You get the "Office 365" Azure Active Directory plan with an Office 365 subscription; this is a basic version, but if, in addition to O365 logins you just want single sign on for a few cloud services, this is a super-affordable way to do that (limit of 10 SSO apps)
      1. This might be a bridge to the cloud; if you're living fully in the modern stack, you're really going to want (and what I'm assuming you'll have for purposes of this talk) 👇
   1. 👉Enterprise Mobility + Security (EM+S) - E3, E5
      1. Intune, Azure Active Directory Premium
      1. This gives you device and identity management in the cloud
   1. 👉Windows Enterprise - E3, E5
      1. This is Windows-as-a-Service--gives you access to perpetual updates on "the last version of Windows"; user-based licensing for Windows 10
         1. In contrast to the traditional volume licensing that we're all used to (being device-based), this is user based
         1. All of the bits for Windows 10 Enterprise are included with Windows 10 Pro; the user's Windows 10 license will unlock the enterprise functionality
      1. Primary difference between E3 and E5 is that E5 also includes Windows Defender ATP
   1. 👉Microsoft 365 (M365) - E3, E5
      1. The total package; includes all of the above
      1. Notable things E5 adds to E3: more advanced security, discovery, and auditing tools, plus phone system
   1. 👉Our Licensing Strategy
      1. We've found E3 licenses to be sufficent for our needs.
         1. Not using phone system (under contract for SIP trunks, which gives end-to-end QoS)
         1. We've found we don't need the more advanced security features (at this point), and we're using third-party AV
      1. Users with org-owned Windows devices: M365 E3
         1. Where we need the Windows license, we reach for the whole suite in one shot via the M365 license
         1. Not sure if this is the case for everyone, but we don't have the option to purchase a standalone Windows 10 Enterprise license in our NPO portal; it only shows up with commercial licenses
            1. So, we reach for M365 to get the Windows Enterprise license
         1. This makes our cost $8.00/user/mo with annual payment ($96.00 yearly)
      1. Users with org-owned non-Windows devices: ProPlus, O365 E1, and EM+S
         1. Until recently, MS gave away 50 EM+S E3 seats to NPOs (this was replaced with 10 small business essentials licenses Sept. 1). So, we combine these with a ProPlus license for our users running ChromeOS or MacOS
         1. This makes our cost $3.00/user/mo with annual payment ($36.00 yearly)
      1. Users with no org-owned devices: O365 E1 and EM+S
         1. This makes our cost for basic access (email only and cloud apps/authentication $0)
      1. So, of course, this may not be the strategy that is best for your organization to adopt
         1. Number of staff (and having the donated EM+S seats) makes a big difference for us
         1. The point here is, you can go all-in with the kitchen sink M365 license, or mix and match a bit to save 💰
      1. One note on licensing: you can't license volunteers with donated licenses (unless they're "unpaid full-time equivalent (FTE) staff who have material day-to-day managerial, operational, and fiduciary responsibilities")
         1. At least for us, almost all of our volunteers
         1. There is an E1 license you can purchase for volunteers in the NPO subscription portal; our cost for this is $2.00/user/mo w/ annual payment
         1. Otherwise, Microsoft's recommendation is to invite volunteers as guests
1. Azure Active Directory (AAD)
   1. 👉"Azure AD is not Cloud AD" (©?)
      1. If you've Googled any number of search terms relevant to Azure AD, you've probably been bombarded by these advertisements looking to sell you...yet another cloud-based identity service
         1. And it's true...AAD and traditional AD are very different, built to meet different needs in different technology stacks and, ultimately, different eras
         1. Azure AD isn't just traditional Active Directory in the cloud
      1. 👉Goodbye NTLM, LDAP, Group Policy, and RADIUS; hello web services
         1. OAUTH, SAML, OpenID, etc.; these are the languages Azure AD speaks
         1. Windows 10 uses WS-Fed to join a device to Azure AD and WS-Trust to sign in to an Azure AD-joined device
         1. The traditional AD auth protocols are not part of Azure AD itself. You can get them with another Azure service (called Azure Active Directory Domain Services - ADDS), but in the words of Han Solo, "It's gonna cost you something extra".
         1. At first, I didn't think we could live without LDAP and RADIUS especially; I thought we were going to be jumping directly in with Azure ADDS. 
         1. Two major pain points:
            1. PBX using LDAP for user web portal auth
               1. Web portal user usage is minimal; needed with our system to change speed dials and that sort of thing
                  1. Seldom used, and even more seldom that changes were made; we'll just do this for folks when needed now (we do expect to implement a better solution for this long-term)
            1. WPA2 Enterprise Wi-Fi
               1. NPS/RADIUS auth against AD for employees and AD-joined devices
               1. Printing is really the only thing the "secure" Wi-Fi offered to employee mobile devices that public doesn't; so, we've pushed our employees to open Wi-Fi
                  1. With the proliferation of HTTPS we don't feel that this is nearly as much of a risk as it used to be; the security boundary is moving to the endpoint instead of the network
                  1. We are beginning a Meraki rollout, and Meraki supports web auth against Azure AD and G Suite, so we'll likely head that route in the future for employees (and provided them access to print services over an open network with a web auth portal)
      1. 👉Azure AD manages applications
         1. Azure AD manages "Enterprise Applications"; these are basically SSO-enabled Apps to which you assign users access in AAD
         1. Not really a direct analogue in traditional AD
      1. 👉Flat user structure; no more domains, forests, or OUs
         1. Groups are the only mechanism for, um, "grouping" users, and they do function a bit differently in Azure AD (more on that in a bit)
      1. 👉Can't customize the directory schema
         1. Other than what installing Exchange server I suspect most of folks in this room typically aren't making changes to their directory schema
            1. But, if you were relying on schema extensions you can't do it in Azure AD (and I suspect you'd be hard pressed to find the need to do so)
      1. So thats the 1000 ft. overview of Azure AD from a "vs. AD" perspective; I'll continue to take that perspective and try to hit what we found to be some of the other cognitive shifts
   1. 👉Groups
      1. I mentioned groups function a bit differently in Azure, so let's talk about groups now.
      1. 👉Two types of groups: Security and O365
      1. 👉Three membership types: Assigned, Dynamic User, Dynamic Device
         1. Dynamic User and Dynamic Devices are the interesting ones here
         1. Think similar to Exchange dynamic distribution lists, but for building security or office 365 groups; basically, you build a filter based on directory attributes and the group is populated automatically
         1. Filters use a very Powershell-like syntax
         1. We use dynamic groups in a few different ways...one interesting example is for students--grouping based on elementary, middle, and high school
            1. Last two digits of graduation year are in usernames, so we simply have dynamic groups that look for the usernames containing the appropriate graduation years 
      1. 👉Group-based licensing
         1. Licenses can be assigned to groups instead of individual users; this was released late last year, and we've found this capability to hugely simplify license management! ("You want to turn this on for all of your employees? Ok, one click here please...")
         1. This does, I believe, require an Azure AD premium license
      1. One thing we've found with regards to groups: As a general rule, we try not to use O365 groups as security groups, especially when we're letting users manage membership
         1. This gives users control, without worrying about unexpected side effects like "I don't have access to this third party app anymore" or "I can't access my email anymore"
         1. Instead, we create dedicated security groups to manage access to apps, licenses, traditional SharePoint sites, that sort of thing
            1. This guarantees maximum flexibility for user-managed O365 groups without needing to worry about unexpected consequences
            1. We use a specific syntax for our security groups, so we can easily search for them in the UI (searches start at beginning of group name strings):
            1. 👉Sec-[GROUP TYPE]-[GROUP NAME]
               1. Various group types, such as "Lic" for groups that assign license, "Acc" for groups that give access to resources, that sort of thing
   1. 👉Connecting Devices
      1. In traditional AD this was straightforward; devices were either domain-joined or not
         1. Three types of joins in AAD:
      1. 👉Azure AD Registered
         1. Personal devices, BYOD scenarios
         1. A device becomes AAD registered when you use an app on that device to sign in to your organization account in AAD
      1. 👉Azure AD Joined
         1. Closest analogue to devices joined to traditional AD; organization owned, users sign in using Azure AD accounts
         1. Can't directly Azure AD join non-windows devices (say, like Mac to traditional AD)
         1. This is what we're doing; sort of interesting--devices behave somewhat like they're just "workgroup" members, once a user signs in with an Azure AD account it's basically like a local account was created for them
         1. Folder in C:\Users basically becomes FirstLast, downlevel logon name (DOMAIN\username) format becomes:
         1. 👉Down-Level Logon Name: AzureAD\FirstLast
         1. If you're working with the user account locally in any way, say adding to some local group on the machine like Remote Desktop Users, you'll want to use the AzureAD\FirstName downlevel logon name format
      1. 👉Hybrid Azure AD Joined
         1. Joined both to traditional AD and AAD
         1. We did not explore this option in-depth since our goal is to eliminate on-prem AD 🙂
   1. 👉Enterprise Applications
      1. The primary "killer feature"
      1. 👉Administrative control of SSO with third-party apps
         1. Azure AD was built for providing authentication to third-party apps and platforms
         1. Basically like if ADFS had was rolled directly into (and part of) active directory
         1. Access to applications can be controlled with Azure AD groups, or by assigning access to individual users
         1. 👉Hundreds of applications in the gallery
         1. SaaS vendors and/or Microsoft will typically have documentation
         1. We're moving as much as we can to use Azure AD identities
      1. 👉Azure AD as IDP for G Suite
         1. One of the biggest wins for (on both church and school side) has been setting up our Azure AD tenant as the identity provider for G Suite. This gives us the following on the church side (school/EDU is a bit different):
            1. This is actually fairly straightforward and easy to set up
         1. 👉Google "Cloud Identity Free" licenses
            1. On the church side, we're using a commercial G Suite account (School uses EDU account) with most users licensed using the Cloud Identity Free License
            1. Cloud identity free basically gives you a managed Google account without Google Apps; so, you essentially get all of the Google consumer services minus Gmail, Google Docs, and so on (which you shouldn't need anyway if you're living in O365)
            1. Number of cloud identity free seats you get is related to how many paid licenses you purchase; we have 10 G Suite Business licenses (for certain use cases that significantly benefit from specific G Suite functionality) which gets us ~550 Cloud Identity Free licenses
         1. Web App Login: "Sign in with Google"
            1. Seems like Google as OAUTH IDP is among the most popular; if SSO is supported, you can almost bet Google will be on the list
            1. So, this instantly gets us SSO with web applications all over the Internet
         1. Chrome Sync with Azure AD logins
            1. Gets us complete platform agnosticism in the browser; users can sign into any device or platform and all of their browser preferences, shortcuts, etc. are there and will follow them around
               1. We also force Chrome browser management with a policy in Intune, and then can use G Suite to specify browser settings on supported platforms...this is the 💣
               1. We whitelist allowed Chrome extensions this way, and do things like prevent push notifications (we found users would blindly allow these, and then call us wondering why they were getting random popup advertisements...)
         1. Azure AD logins on ChromeBooks 😎
            1. While we've ended up using ChromeBooks less than we expected (because the Intune experience is so good), we do find they make sense for employees with really basic needs (email, web apps, really basic word processing)
            1. This is notwithstanding one-to-one school scenario where students are using Chromebooks; we've got this in production at this point with ~250 student users since July (and working well so far)
         1. 👉👉Chrome signin with Azure AD
         1. One note: there is not a native way to bind Macs to Azure AD for SSO
            1. Your Mac MDM may be able to help with this...Mosyle offers "Mosyle Auth for Mac Login Window" which advertises Azure AD logins for Mac (this is a paid addon)
            1. We haven't tested this yet (since we don't have any Macs in the school environment, but we plan to do so soon).
   1. 👉Conditional Access
      1. The second "killer feature" for us...
      1. 👉Configure security controls to apply in specific scenarios
         1. Basically, conditionally allow/deny access, require MFA, etc.
      1. 👉Based on a variety of "signals", such as:
         1. Group membership (or even specific user)
         1. IP Geolocation
         1. Device (managed or not)
         1. Application being accessed
         1. Risk detection (depending on license)
         1. Examples we've implemented:
            1. Require MFA for admins
            1. Require approved apps on Android and iOS devices
               1. Sandboxing of org data on mobile devices via Intune Mobile App Management; conditional access polices are ultimately what make this a requirement
               1. More on this when we talk about Intune
         1. Other examples (some we're planning to implement)
            1. IP Geolocation blocking
            1. Block off-campus sign ins for groups that don't sign in from off-campus
            1. Require MFA from all employees
   1. 👉Our Pain Points
      1. 👉Security group nesting is...unpredictable
         1. Some places it works exactly as you'd expect, other places it just doesn't work; group members from nested groups simply aren't there
         1. In traditional AD, we had worked hard to move everything to role-based access; if you were, say, a Receptionist, we assigned you to the "Receptionist" and you magically got everything you needed from there
         1. We found this role-based approach really didn't work in Azure AD, because nesting was so hit or miss
         1. To be consistent, we just stopped using group nesting altogether
      1. 👉Password changes on AAD-joined devices are...jarring
         1. The user is taken to a web page
         1. This makes new employee setup especially awkward, I think; they're not prompted when logging in to set a new password, and the only real indication that some action is needed is all of the cloud-connected apps (OneDrive, etc.) basically just don't work
1. 👉Intune
   1. Intune is not just "GPO in the cloud"; it's Mobile Device Management and Mobile Application Managment
      1. MDM...just like you would use for iOS/iPadOS devices, Android Devices, Macs, etc. Now you use it for Windows
   1. 👉Device Configuration Profiles
         1. Because Intune is MDM, not GPO, you're managing configuration profiles instead of Group Policy Objects (just like in any other MDM)
      1. 👉Assigned to devices or groups of devices (not OUs), not hierarchical like GPO
         1. You select the platform when creating a profile, and then you can select from the appropriate configuration profile types for your platform
            1. Links on website for more on config profiles, including profiles types
            1. We have 8 profiles deployed for our school config that are basically our entire Windows config (not including update rings...we'll get there in a minute)
         1. Built-in configuration profiles do not have the breadth of settings that we're used to coming from GPOs, but, with some recent additions, there's a lot of room to configure settings that aren't specified in a pre-built configuration profile. Let's cover those since they're more interesting than just what the built-in profiles can do
      1. 👉Administrative Templates
         1. Yes...this is a profile which basically gives you the option to set the settings from Windows 10 Administrative Templates ADMX from Intune
            1. Went GA in July, hugely increases the number of settings you can configure using config profiles
            1. Admin Templates screenshot
               1. Very different from what you're used to...one big long list, 109 pages!! 😲
               1. Not exhaustive, but fills in a lot of gaps. First choice is always to use another configuration profile type, then fall back to admin templates profile if needed settings aren't somewhere else.
            1. This is what we use for our OneDrive setup; enables automatic SSO with the Windows logon, turns on files on demand, and does KFM (articles onling showing how to do this other ways...this is crazy easy)
               1. Makes the OneDrive setup completely seemless. Sign into device > OneDrive does its thing (takes a few mins on first logon) > start working
            1. OneDrive config was ultimately the only thing for which we needed to reach to an Administrative Templates profile
      1. 👉Custom Profiles/OMA-URI
         1. This is where things get a little more interesting, and a bit more labor intensive
            1. You can use custom profiles to specify settings that aren't included in one of the standard profiles
         1. 👉Specify custom OMA-URI and values
            1. OMA-URI = Open Mobile Alliance Uniform Resource Identifier; this is basically a path (think URL) specifying a particular setting to be modified
               1. Using the OMA-DM (Open Mobile Alliance Device Managment) standard; this is the industry spec that basically defines how MDM platforms interact with devices
            1. All possible OMA-URI for Windows 10 are defined in the CSP (configuration service provider) reference -- this is great evening reading 😛
               1. From that spec you can get what you need to specify supported settings using custom policies; links on the website
            1. We use this for pushing default apps. Notes on the website.
         1. 👉Ingest Custom ADMX
            1. You can ingest any ADMX template that's not already in admin templates or specified in existing policy; we use this for pushing a few Google Chrome settings (basically to register as managed browser, then G Suite takes over from there)
               1. Essentially you paste in the XML from the ADMX into Intune and then generate OMA-URIs from there and specify your settings (links on the website)
   1. 👉Patching: No WSUS? No problem!
      1. Really two things you want to set up that work in concert to manage patching:
      1. 👉Delivery Optimization
         1. This is a configuration profile; sets up parameters for allowing P2P distribution of update files
         1. Gets local caching benefits, without having to have something like a WSUS server
      1. 👉Softare Update Policy
         1. This is where you specify Windows update settings
            1. No more do you really have control over individual patches (and I don't think you really need to); instead, you have...
         1. 👉Windows 10 Update rings
            1. Update rings are basically groups of devices sharing patching settings
               1. Primary thing you do is specify how soon after updates are realeased they will be installed on groups of your machines
               1. Under the hood you're ultimately controlling Windows Update for Business settings
            1. You specify a deferral period for Feature and Quality updates
            1. We use a Fast Ring for some devices to try to catch updates with issues before they go to everyone, and then a "Standard Ring" which is where most devices live
            1. 👉Patching screenshot; Here you can see our update rings
            1. You can pause updates for certain rings (useful for situations where there's a bad patch in the wild) and also uninstall feature updates and quality updates for certain rings (haven't personally tested this yet) if something blows up
            1. You also specify when to interrupt your users (or not) here, and what the overall update story will be for your usres
            1. Overall, you definitely have less granular control with update rings, but it's much less labor-intensive to manage (and Microsoft's cumulative patching model makes this less useful anyway nowadays)
   1. 👉PowerShell Scripts
         1. You can easily push custom powershell scripts to your Windows devices using Intune. Use this if you can't configure what you need via other means, or you need some more intelligent decision making.
      1. 👉Intune Management Extension deploys scripts and installs Win32 apps
         1. PowerShell scripts and Win32 apps are deployed by a small helper service called "Intune Mangement Extensions"
         1. This is automatically pushed to the device when you push a PowerShell script or a Win32 app (which we'll talk about in a minute)
      1. 👉PowerShell Scripts can be run user or machine-scoped
         1. You assign the script to either a group of users, or a group of machines
            1. You can control whether scripts are run in the user context or as the system user
         1. PowerShell scripts will run until completed (based on exit code), with 3 retries and a timeout of 10 minutes
      1. 👉DO NOT put sensitive data into PowerShell scripts you push with Intune
         1. Script contents are dumped to the Intune Management Extension logs, and area easily accessible even with a standard user account
         1. If drive isn't encrypted, accessible offline!
      1. We use a PowerShell script for deploying Microsoft Teams. To get Teams not to run automatically, large and in charge at startup after an install, there's a command line param that needs to be set on the installer. We couldn't get this to work well with any other app deployment methods in Intune, so we hacked this together with inspiration from somewhere on the Internet. Teams was, among (if not the most) difficult app we packaged. Example on website.
   1. 👉App Deployment
      1. This is one of our favorite Intune capabilities; something we didn't have a great solution for before we rolled out Intune (deploying apps with Group Policy is spectacularly meh)
         1. With the relatively recently added ability to deploy Win32 apps, Intune's app deployment capabilities are really robust.
         1. Apps can be assigned to devices or users
      1. 👉Types of apps that can be deployed on Windows:
         1. 👉Microsoft Store Apps
            1. Really straightforward; purchase paid app licenses in the App store, it syncs with Intune, and you deploy to devices or device groups
         1. 👉Line of Business App (Well-behaved MSI)
            1. Well-behaved MSIs are really easy to deploy...upload the MSI, specify any command line args, and you're basically done. Intune Management Extension will download the MSI and take care of the rest
         1. 👉Windows app (Win32)
            1. If you've done any amount of Windows app deployment, you know that the majority of apps are not "well behaved MSIs"
            1. This option gives you a lot more flexibility in deployment; can deploy MSI or EXE
            1. Here's the basic process:
               1. Put all of the resources needed to silently deploy the app into a folder (executable, scripts you write to help with install/uninstall, etc)
               1. Use a Microsoft-provided utility to bundle the resources into a .intunewin archive
               1. Upload the .intunewin archive
               1. Specify an entrypoint to install the app; this could be a script you've written to help with installation, the exe installer itself, etc.
               1. Specify requirements needed to install the app: > than a certain Windows version, certain amount of Ram or disk space, etc.
               1. Specify detection rules to determine if the app is installed (check if a particular MSI GUID is present, particular file/folder is present, etc)
            1. Since you can specify your own scripts as an entrypoint, you can get really creative if need be. For example, we have a test generating app for the school that insists on saving data in %programfiles% by default
               1. We hacked together a script that symlinks the directories this app uses to OneDrive during the install process, so all of the data is transparently written to OneDrive
               1. The app is happy; it things its just program files, and we're happy because it ends up in OneDrive--gotta maintain that user/device agnosticism
      1. 👉Company Portal
         1. The company portal app is an important part of app deployment; allows for self-service app installation
            1. You make apps "Required" or "Available"; required apps are automatically pushed to the device, available apps can be installed by users in the Company Portal
            1. This is a great self-service option for "optional" applications; users can install them on-demand, just like the app store on their mobile device (doesn't matter if it's a Win32 app, Windows Store app, etc)
            1. Company Portal app image
   1. 👉Pain Points
      1. 👉App install error codes for Win32, MSI are often...unhelpful
         1. Means you usually have to resort to more hands-on troubleshooting methods on your test machine. See website for notes on this.
      1. 👉Built-in cloud-based printer deployment solution is...nonexistent
         1. We resorted to a third-party product called Printix for managing and deploying printers (doesn't require print server).
         1. We came from PaperCut; Printix doesn't have reporting (which we didn't really need), but we do miss some of the features and overall visibility from PaperCut
         1. Printix gets you Windows, Mac, iOS, and Android printing
         1. 30% non-profit discount
         1. Printix could be a session in and of itself...talk to me afterwards or in the hallway and I'll be happy to share more about Printix
      1. 👉Wi-Fi policies will report an error if pushed to a device without a Wi-fi adapter, which we find...annoying
         1. Otherwise, we'd have one set of policies we'd be pushing for all device form factors
         1. As a result of this, we have to push separate policies for desktops and laptops
      1. 👉Reporting intervals are...really slow 🐢
         1. It tends to take a long time for the pretty donut graphs in Intune to reflect reality
1. 👉Getting Devices "Business Ready"
   1. I struggled with what exactly to title this slide, because "Enroll", "Register", "Join", all mean something a bit different in Modern Management parlance; I'm taking the 1000 ft. view here
      1. "Business Ready" is what Microsoft calls a device that is ready for a user to use
         1. So, the question is, how do we take a device from boxed to busy?
         1. In other words..."how to I get my devices into Azure AD and Intune to manage them?"
   1. This is a fairly nuanced topic, mostly because there are different options depending on your exact scenario and needs. This could be another whole session in and of itself.
      1. I'll mosty focus on what we've done (again, focusing on being cloud-only since that's our goal)
   1. 👉Azure AD/Intune Integration
      1. As you would expect, Azure AD and Intune are well integrated. You specify Intune as your MDM in Azure, and when you join a device in Azure AD it can be automatically enrolled in Intune and will pull down policies
         1. Recall Azure AD Registered = BYOD, Joined = organization owned
   1. 👉Primary choice: User or IT-driven?
      1. Microsoft parlance: self-enrollment or administrator-based enrollment in Intune
      1. You can set things up so you hand users an unopened box, they unpack the device,connect to Wi-Fi, sign in with their creds, and everything is automatically deployed
         1. Downside of this is that it will take some time on the user's end for the device to be ready, upside is that this works great if you don't have IT at a remote site and want to ship devices directly, or need a really light touch from IT
      1. Or, you can make everything more IT-driven; IT does device prep, hands device to user that is ready to go
         1. Downside is that IT time and touch is required, upside is that you can hand the user a device that is all-but ready to use
         1. This is our choice; we want to hand users a device that is as ready to do ministry as possible
      1. We'll talk about Intune enrollment methods now, because ultimately the more nuanced topic here (than just joining devices to Azure AD)
      1. 👉Self-enrollment methods:
         1. I'm not hitting everything here, because there's a lot...pulling out what I think will be most relevant for most of us
         1. 👉BYOD
         1. Azure AD Join
         1. Autopilot
            1. Most interested in White Glove deployment, but needs TPM 2.0
      1. 👉Administrator-based enrollment methods
         1. 👉Hybrid Azure AD Join
         1. Bulk enroll
   1. 👉Our Process: Bulk enrollment, Fresh Start resets
      1. I call this the "Gray Glove" deployment
      1. Downside: we don't get user/device association in Azure AD/Intune
1. 👉Random Tasty Tidbits 🍨
   1. Things I wanted to share, but didn't fit anywhere else!
   1. 👉BitLocker: Key escrow to Azure AD, Intune policy for automatic encryption 🔐
      1. Super easy to set up...really no good reason not to be deploying drive encryption
   1. 👉Azure AD Sign-in logs 👍
      1. Quickly see sign-ins for a user or all users...SO MUCH EASIER than on-prem
   1. 👉Azure Cloud Shell 😎
      1. Basically containerized PowerShell instance in the browser (running on Linux)...nice because you're probably already signed in with your MS account
      1. Does cost a bit for Azure storage account (and might cost a bit for the computer)...we get a bill that's pennies per month for this.
   1. 👉Intune: Compliance policies 🔑
      1. Specify standards your device must meet in order to satisfy your security policy (BitLocker enabled, Win version > X, etc.)
      1. Can be used in Conditional Access rules in Azure AD to make authentication decisions!
   1. 👉Mobile App Management 📱
      1. Basically allows you to create a sandboxed environment on employee personal devices with organization data
         1. You can wipe just org data when employee leaves
         1. You can require specific security controls for your data on the employee's device
         1. Big win: you don't need to manage the entire device; you're only managing the apps connecting to your data
         1. This works in conjunction with AAD conditional access rules to 
1. Conclusion: What's the right path?
   1. Goals we set out to meet:
1. Notes and Contact
   1. Check out the Microsoft Learn link 
1. Q+A!

## Content ToDo
* TODO: Enrollment and AutoPilot
* TODO: Conclusion

## To Test
* TODO: Windows activation with Provisioning Packages
* TODO: https://churchitnetworkcom.sharepoint.com/:f:/s/Leadership/EtSkZW5WC6JJjkypLMxeOWsBAF__zdAmm8cCKyAJV9J83A?e=DTSvfy 

## Commands:
<!--docker run --rm -t --net=host -v ${pwd}:/slides astefanutti/decktape --slides 1-3,10,17,22,27,32,37,41,44,50,53,57,63,68,74,80,82,83 http://10.0.75.1:4000/citn2019/slides slides.pdf-->
<!--jekyll serve --host 0.0.0.0-->u
