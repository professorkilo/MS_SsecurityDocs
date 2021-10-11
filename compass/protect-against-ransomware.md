---
title: "Rapidly protect against ransomware and extortion"
keywords: ransomware, human-operated ransomware, human operated ransomware, HumOR, extortion attack, ransomware attack, encryption, cryptovirology, extortionware, malicious encryption
ms.author: josephd
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection: 
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-ransomware
- m365solution-overview
ms.custom: 
description: Rapidly protect your organization against ransomware and extortion.

---

# Rapidly protect against ransomware and extortion

>[!Note]
>This guidance will be updated as new information becomes available.
>

Mitigating ransomware and extortion attacks is an urgent priority for organizations because of the high impact of these attacks and high likelihood an organization will experience one. 

Ransomware is a type of extortion attack that encrypts files and folders, preventing access to important data. Criminals use ransomware to extort money from victims by demanding money, usually in form of cryptocurrencies, in exchange for a decryption key. Criminals also often use ransomware to extort money from victims in exchange for not releasing sensitive data to the dark web or the public internet.

While early ransomware mostly used malware that spread with phishing or between devices, human-operated ransomware has emerged where a gang of active attackers, driven by human intelligence, target an organization rather than a single device or set of devices and leverage the attackers’ knowledge of common system and security misconfigurations and vulnerabilities to infiltrate the organization, navigate the enterprise network, and adapt to the environment and its weaknesses as they go.

These attacks can be catastrophic to business operations and are difficult to clean up, requiring complete adversary eviction to protect against future attacks. Unlike early forms of ransomware that only required malware remediation, human-operated ransomware can continue to threaten your business operations after the initial encounter.

## Sophistication of ransomware and extortion attacks

Technical hallmarks of these human-operated ransomware attacks typically include credential theft and lateral movement and can result in deployment of ransomware payloads to many high-value resources in order to encourage payment of the ransom. The attacker model is often effective and highly tuned, including targeting destruction or encryption of backups, network and enterprise documentation, and other artifacts that would let the organization rebuild without paying the ransom.

The attacks also have sophisticated business models, with attackers setting their ransom prices based on internal financial documentation from the company, cyber-insurance coverage levels, and typical regulatory compliance fines the company would have to pay. 

## Organization of the guidance in this solution

This guidance provides concrete instructions on how to best prepare your organization from many forms of ransomware and extortion.

To help you understand how to protect your organization from ransomware, this guidance is organized into prioritized phases. Each phase corresponds to a separate article. The priority order is designed to ensure you reduce risk as fast as possible with each phase, building on an assumption of extreme urgency that will override normal security and IT priorities to avoid or mitigate these devastating attacks.

![The three phases to protecting against ransomware](media/protect-against-ransomware/protect-against-ransomware-phases.png)

**It is vital to note** that this guidance is structured as prioritized phases that you should follow in the prescribed order. To best adapt this guidance to your situation:

1. **Stick with the recommended priorities** 

    Use the phases as a starting plan for what to do first, next, and later so you get the most impactful elements first. These recommendations have been prioritized using the [Zero Trust](https://www.microsoft.com/security/business/zero-trust) principle of assume breach, which focuses on minimizing business risk by assuming the attackers can successfully gain access to your environment through one or more methods.

2. **Be proactive and flexible (but don’t skip important tasks)**

    Scan through the implementation checklists for all sections of all three phases to see if there are any areas and tasks that you can quickly complete earlier (e.g., already have access to a cloud service that hasn’t been utilized but could be quickly and easily configured). As you look over the whole plan, be very careful that *these later areas and tasks don’t delay completion* of critically important areas like backups and privileged access!

3.	**Do some items in parallel** 

    Trying to do everything at once can be overwhelming, but some items can naturally be done in parallel. Staff on different teams can be working on tasks at the same time (e.g., backup team, endpoint team, identity team), while also driving for completion of the phases in priority order.

The items in the implementation checklists are in the recommended order of prioritization, not a technical dependency order. Use the checklists to confirm and modify your existing configuration as needed and in a way that works within your organization. For example, in the most important backup element, you backup some systems, but they may not be offline/immutable, or you may not test the full enterprise restore procedures, or you may not have backups of critical business systems or critical IT systems like Active Directory Domain Services (AD DS) domain controllers. 

>[!Note]
>See the [3 steps to prevent and recover from ransomware (September 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/) Microsoft security blog post for an additional summary of this process.
>

### Phase 1. Prepare your recovery plan

This phase is designed to [minimize the monetary incentive from ransomware attackers](protect-against-ransomware-phase1.md) by making it:

- Much harder to access and disrupt systems or encrypt or damage key organization data.
- Easier for your organization to recover from an attack without paying the ransom.

>[!Note]
>While restoring many or all enterprise systems is a difficult endeavor, the alternative of paying an attacker for a recovery key and then using tools written by the attackers to recover systems and data is a much worse option.
>

### Phase 2. Limit the scope of damage

Make the attackers work a lot harder to [gain access to multiple business critical systems via privileged access roles](protect-against-ransomware-phase2.md). Limiting the attacker’s ability to get privileged access makes it much harder to profit off of an attack on your organization, making it more likely they will give up and go elsewhere.

### Phase 3. Make it hard to get in

This last set of tasks is important to raise friction for entry but will take time to complete as part of a larger security journey. The goal of this phase is for attackers to have to work a lot harder to [obtain access to your on-premises or cloud infrastructures](protect-against-ransomware-phase3.md) at the various common points of entry for attacks. There are a lot of these tasks, so it’s important to prioritize your work here based on how fast you can accomplish these with your current resources. 

While many of these will be familiar and/or easy to quickly accomplish, it’s critically important that ***your work on phase 3 should not slow down your progress on phases 1 and 2!***

## At a glance

You can also see an overview of the phases and their implementation checklists as levels of protection against ransomware attackers with the [Protect your organization from ransomware
poster](https://download.microsoft.com/download/5/e/3/5e37cbff-9a7a-45b2-8b95-6d3cc5426301/protect-your-organization-from-ransomware.pdf).

[![The "Protect your organization from ransomware" poster](media/human-operated-ransomware/ransomware-poster-thumbnail.png#lightbox)](https://download.microsoft.com/download/5/e/3/5e37cbff-9a7a-45b2-8b95-6d3cc5426301/protect-your-organization-from-ransomware.pdf)

## Next step

[![Phase 1. Prepare your recovery plan](media/protect-against-ransomware/protect-against-ransomware-phase1.png)](protect-against-ransomware-phase1.md)

Start with [Phase 1](protect-against-ransomware-phase1.md) to prepare your organization to recover from an attack without having to pay the ransom.

## Additional ransomware resources

Key information from Microsoft:

- [The growing threat of ransomware](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog post on July 20, 2021
- [Human-operated ransomware](human-operated-ransomware.md)
- [The latest Microsoft Security Intelligence Report](https://www.microsoft.com/securityinsights/) (see pages 22-24)
- **Ransomware: A pervasive and ongoing threat** report in the **Threat analytics** node of the Microsoft 365 Defender portal (see these [licensing requirements](/microsoft-365/security/defender/prerequisites#licensing-requirements))

Microsoft 365:

- [Deploy ransomware protection for your Microsoft 365 tenant](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Recover from a ransomware attack](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Malware and ransomware protection](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Protect your Windows 10 PC from ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Handling ransomware in SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)

Microsoft 365 Defender:

- [Find ransomware with advanced hunting](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Azure Defenses for Ransomware Attack](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Backup and restore plan to protect against ransomware](backup-plan-to-protect-against-ransomware.md)
- [Help protect from ransomware with Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26 minute video)
- [Recovering from systemic identity compromise](/azure/security/fundamentals/recover-from-identity-compromise)
- [Advanced multistage attack detection in Azure Sentinel](/azure/sentinel/fusion#ransomware)
- [Fusion Detection for Ransomware in Azure Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Cloud App Security:

-  [Create anomaly detection policies in Cloud App Security](/cloud-app-security/anomaly-detection-policy)

Microsoft Security team blog posts:

- [3 steps to prevent and recover from ransomware (September 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [Becoming resilient by understanding cybersecurity risks: Part 4—navigating current threats (May 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  See the **Ransomware** section.

- [Human-operated ransomware attacks: A preventable disaster (March 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Includes attack chain analyses of actual attacks.

- [Ransomware response—to pay or not to pay? (December 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro responds to ransomware attack with transparency (December 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)