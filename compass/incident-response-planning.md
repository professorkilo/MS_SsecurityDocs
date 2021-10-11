---
title: Incident response planning | Microsoft Docs
description: Understand how to plan for incident response in your security operations center.
keywords: incidents, alerts, investigate, analyze, response, correlation, attack, incident response, cyber-attack, respond, plan, incident response plan, IRP, IR plan
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
localization_priority: Normal
ms.topic: article
ms.prod: m365-security
---

# Incident response planning

Use this table as a checklist to prepare your Security Operations Center (SOC) to respond to cybersecurity incidents.

| Done| Activity | Description | Benefit |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | Table top exercises | Conduct periodic table top exercises of foreseeable business-impacting cyber incidents that force your organization's management to contemplate difficult risk-based decisions. | Firmly establishes and illustrates cybersecurity as a business issue. Develops muscle memory and surfaces difficult decisions and decisions rights issues across the organization. |
| <input type="checkbox" /> | Determine pre-attack decisions and decision-makers | As a compliment to table top exercises, determine risk-based decisions, criteria for making decisions, and who must make and execute those decisions. For example: <br><br><input type="checkbox" /> Who/when/if to seek assistance from law enforcement? <br><br><input type="checkbox" /> Who/when/if to enlist incident responders? <br><br><input type="checkbox" /> Who/when/if to pay ransom? <br><br><input type="checkbox" /> Who/when/if to notify external auditors? <br><br><input type="checkbox" /> Who/when/if to notify privacy regulatory authorities? <br><br><input type="checkbox" /> Who/when/if to notify securities regulators? <br><br><input type="checkbox" /> Who/when/if to notify board of directors or audit committee? <br><br><input type="checkbox" /> Who has authority to shut down mission-critical workloads? | Defines the initial response parameters and contacts to involve that streamline the response to an incident. | 
| <input type="checkbox" /> | Maintaining privilege | Generally, advice can be privileged, but facts are discoverable. Train key incident leaders in communicating advice, facts and opinions under privilege so that privilege is preserved and risk is reduced.| Maintaining privilege can be a messy process when considering the multitude of communications channels, including e-mail, collaboration platforms, chats, documents, artifacts. For example, you can use [Microsoft Teams Rooms](/microsoftteams/rooms/). A consistent approach across incident personnel and supporting external organizations can help reduce any potential legal exposure.| 
| <input type="checkbox" /> | Insider trading considerations | Contemplate notifications to management that should be taken to reduce securities violations risk. | Boards and external auditors tend to appreciate that you have mitigations that will reduce the risk of questionable securities trades during periods of turbulence.| 
| <input type="checkbox" /> | Incident roles and responsibilities playbook | Establish basic roles and responsibilities that allow various processes to maintain focus and forward progress. <br><br> When your response team is remote, it can require additional considerations for timezones and proper handoff to investigators. <BR><br> You might have to communicate across other teams that might be involved, such as vendor teams. | **Technical Incident Leader** – Always in the incident, synthesizing inputs and findings and planning next actions. <br><br> **Communications Liaison** – Removes the burden of communicating to management from the Technical Incident Leader so they can remain involved in the incident without loss of focus. <br><br> This should include managing executive messaging and interactions and other third parties such as regulators. <br><br> **Incident Recorder** – Removes the burden of recording findings, decisions, and actions from an incident responder and produces an accurate accounting of the incident from beginning to end. <br><br> **Forward Planner** – Working with mission-critical business process owners, formulates business continuity activities and preparations that contemplate information system impairment that lasts for 24, 48, 72, 96 hours, or more. <br><br> **Public Relations** – In the event of an incident that is likely to garner public attention, and in conjunction with Forward Planner, contemplates and drafts public communication approaches that address likely outcomes. |
| <input type="checkbox" /> | Privacy incident response playbook | In order to satisfy increasingly-strict privacy regulations, develop a jointly-owned playbook between the SecOps and the privacy office that allows rapid evaluation of potential privacy issues that have a reasonable probability of arising out of security incidents. | Evaluating security incidents for their potential to impact privacy is difficult due to the fact that most security incidents arise in a highly-technical SOC that must quickly get surfaced to a privacy office where regulatory risk is determined, often with a 72-hour notification expectation. | 
| <input type="checkbox" /> | Penetration testing | Conduct point-in-time simulated attacks against business-critical systems, critical infrastructure, and backups to identify weaknesses in security posture. This is generally conducted by a team of external experts focused on bypassing preventative controls and surfacing key vulnerabilities. | In light of recent human-operated ransomware incidents, penetration testing should be conducted against an increased scope of infrastructure, particularly the ability to attack and control backups of mission-critical systems and data. | 
| <input type="checkbox" /> | Red Team / Blue Team / Purple Team / Green Team | Conduct continuous or periodic simulated attacks against business-critical systems, critical infrastructure, backups to identify weaknesses in security posture. This is generally conducted by internal attack teams (Red teams) who are focused on testing the effectiveness of detective controls and teams (Blue teams). <br><br> For example, you can use [Attack simulation training](/microsoft-365/security/office-365-security/attack-simulation-training-insights) for Microsoft 365 Defender for Office 365 and [Attack tutorials & simulations](/microsoft-365/security/defender-endpoint/attack-simulations) for Microsoft 365 Defender for Endpoint.  | Red, Blue, and Purple team attack simulations, when done well, serve a multitude of purposes: <ul><li> Allows engineers from across the IT organization to simulate attacks on their own infrastructure disciplines. </li><li> Surfaces gaps in visibility and detection. </li><li> Raises the security engineering skills across the board. </li><li> Serves as a more continuous and expansive process.</li></ul> <br><br> The Green Team implements changes in IT or security configuration. | 
| <input type="checkbox" /> | Business continuity planning | For mission-critical business processes, design and test continuity processes that allow the minimum viable business to function during times of information systems impairment. <br><br> For example, use [an Azure backup and restore plan](/security/compass/backup-plan-to-protect-against-ransomware.md) to protect your critical business systems during an attack to ensure a rapid recovery of your business operations. | <ul><li>Highlights the fact that there is no continuity workaround for the impairment or absence of IT systems. </li><li> Can emphasize the need and funding for sophisticated digital resilience over simpler backup and recovery.</li></ul> | 
| <input type="checkbox" /> | Disaster recovery | For information systems that support mission-critical business processes, you should design and test hot/cold and hot/warm backup and recovery scenarios, including staging times. | Organizations that conduct bare metal builds often find activities that are impossible to replicate or do not fit into the service level objectives. <br><br> Mission-critical systems running on un-supported hardware many times cannot be restored to modern hardware. <br><br> Restore of backups is often not tested and experiences issues. Backups may be further offline such that staging times have not been factored into recovery objectives. | 
| <input type="checkbox" /> | Out-of-band communications | Prepare for how you would communicate in the event of e-mail and collaboration service impairment, ransom of documentation repositories, and unavailability of personnel phone numbers. | Although this is a difficult exercise, determine how off-line and immutable copies of resources that store phone numbers, topologies, build documents, and IT restoration procedures may be stored on off-line devices and locations and distributed at scale. |
| <input type="checkbox" /> | Hardening, hygiene, and lifecycle management | In line with Center for Internet Security (CIS) Top 20 security controls, harden your infrastructure and perform thorough hygiene activities. | In response to recent human-operated ransomware incidents, Microsoft has [issued specific guidance](human-operated-ransomware.md#protect-your-organization-against-ransomware-and-extortion) for hardening and protecting every stage of the cyber attack kill chain whether with Microsoft capabilities or those of other providers. Of particular note are: <ul><li> The creation and maintenance of immutable backup copies in the event of ransomed systems. You might also consider how to keep immutable log files that complicates the adversary’s ability to cover their tracks. </li><li> Risks related to unsupported hardware for disaster recovery. </li></ul> | 
| <input type="checkbox" /> | Incident response planning | At the outset of the incident, decide on: <ul><li> Important organizational parameters. </li><li> Assignment of people to roles and responsibilities. </li><li> The sense-of-urgency (such as 24x7 and business hours). </li><li> Staff for sustainability for the duration. </li></ul> | There is a tendency to throw all available resources at an incident in the beginning and hope for a quick resolution. Once you recognize or anticipate that an incident will go for an extended period of time, take on a different posture that with your staff and suppliers that allows them to settle in for a longer haul. |
| <input type="checkbox" /> | Incident responders | Establish clear expectations with one another. A popular format of reporting ongoing activities includes: <ul><li> What have we done (and what were the results)? </li><li> What are we doing (and what results will be produced and when)? </li><li> What do we plan to do next (and when is it realistic to expect results)? </li></ul>| Incident responders come with different techniques and approaches, including dead box analysis, big data analysis, and the ability to produce incremental results. Starting with clear expectations will facilitate clear communications. | 

## Incident response resources

- [Overview](incident-response-overview.md) for Microsoft security products and resources for new-to-role and experienced analysts
- [Process](incident-response-process.md) for incident response process recommendations and best practices
- [Playbooks](incident-response-playbooks.md) for detailed guidance on responding to common attack methods
- [Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview) incident response
- [Azure Sentinel](/azure/sentinel/investigate-cases) incident response

## Key Microsoft security resources 

| Resource | Description |
|:-------|:-----|
| [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra) | A set of visual architecture diagrams that show Microsoft’s cybersecurity capabilities and their integration with Microsoft cloud platforms such as Microsoft 365 and Microsoft Azure and third-party cloud platforms and apps. |
| [Minutes matter infographic](https://github.com/MarkSimos/MicrosoftSecurity/raw/master/Microsoft_CDOC_and_DCU_Poster.pdf) download | An overview of how Microsoft's SecOps team does incident response to mitigate ongoing attacks.  |
| [Azure Cloud Adoption Framework security operations](/azure/cloud-adoption-framework/secure/security-operations) | Strategic guidance for leaders establishing or modernizing a security operation function. |
| [Microsoft security best practices for security operations](/security/compass/security-operations) | How to best use your SecOps center to move faster than the attackers targeting your organization. |
| [Microsoft cloud security for IT architects model](https://aka.ms/cloudarchsecurity) | Security across Microsoft cloud services and platforms for identity and device access, threat protection, and information protection. |
| [Microsoft security documentation](/security/) | Additional security guidance from Microsoft. |
|||
