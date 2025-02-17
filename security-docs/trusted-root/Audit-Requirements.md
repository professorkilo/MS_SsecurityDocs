---
title: Audit Requirements - Microsoft Trusted Root Certificate Program
description: This document provides details about the audit requirements that all Certificate Authorities are required to adhere to  in order to provide annual audits that meet our standards. 
ms.date: 07/08/2024
ms.service: security
author: kasirota
ms.author: kasirota
ms.topic: conceptual
---
# Audit Requirements - Microsoft Trusted Root Certificate Program

This page sets out the requirements for Certification Authorities (CAs) who participate in the Microsoft Trusted Root Certificate Program (\"Program\") along with the requirements to use each of the extended key usage properties (EKUs) that Microsoft currently supports as part of the Microsoft Trusted Root Certificate Program.

Find the requirements for Commercial CAs and Government CAs along with information about what constitutes a Government CA and how the requirements are changing for Government CAs in the [definitions section](#definitions).

> [!TIP]
> Bookmark this page: [https://aka.ms/auditreqs](https://aka.ms/auditreqs)

## General Requirements

Microsoft requires that every CA submit evidence of a Qualifying Audit on an annual basis for the CA and any nonlimited root within its Public Key Infrastructure (PKI) chain. A Qualifying Audit must meet the following five main requirements:

- The auditor must be qualified.
- The audit must be performed using the proper scope.
- The audit must be performed using the proper standard.
- The audit must be performed and the attestation letter must be issued within the proper time period.
- The auditor must complete and submit a Qualifying Attestation.

It's the responsibility of the CA to provide Microsoft with a Qualifying Attestation to the results of the audit and conformance to the Audit Requirements in a timely manner.

### A. The Auditor's Qualifications

Microsoft considers an auditor to be a Qualified Auditor if they're an independent individual or company that is certified to perform certification authority audits by one of these three authorities: (1) WebTrust, (2) an ETSI Equivalent National Authority (published at [https://aka.ms/ena](https://aka.ms/ena)) or, (3) in the case of a Government CA, the government itself. (For more information on Government CAs, see [Government CA Requirements](#government-ca-requirements).)

If a CA chooses to obtain a WebTrust audit, Microsoft requires the CA to retain a WebTrust licensed auditor to perform the audit. The full list of WebTrust-licensed auditors is available at [https://aka.ms/webtrustauditors](https://aka.ms/webtrustauditors). If a CA chooses to obtain an ETSI-based audit, Microsoft requires the CA to retain an authorized entity by an Equivalent National Authority (or \"ENAs\"). A catalog of acceptable ENAs is based on the list at [https://aka.ms/ena](https://aka.ms/ena). If a CA is operated in a country that doesn't have an ETSI Equivalent National Authority, Microsoft accepts an audit performed by an auditor that is qualified under an Equivalent National Authority in the auditor\'s home country.

### B. The Scope of the Audit

The scope of the audit must include all roots, nonlimited subroots, and cross-signed nonenrolled roots, under the root, except for subroots that are limited to a verified domain. The audit must also document the full PKI hierarchy. The final audit statements must be in a publicly accessible location and must contain the start and end dates of the audit period. In the case of a WebTrust audit, WebTrust seals must also be in a publicly accessible location.

### C. Point-in-Time Readiness Assessments

Microsoft requires an audit prior to commencing commercial operations. For commercial CAs that haven't been operational as an issuer of certificates for 90 days or more, Microsoft accepts a point-in-time readiness audit conducted by a Qualified Auditor. If the CA uses a point-in-time readiness audit, Microsoft requires a follow-up audit
within 90 days after the CA issues its first certificate. A commercial CA already in our program applying for a new root to be included is exempt from the point-in-time and period-in-time audit requirement for the new roots. Rather, they should be up to date on audits for their existing roots in the program.

### D. The Time Period Between the Assessment and the Auditor's Attestation

Microsoft requires that the CA obtain a conforming audit annually. To ensure that Microsoft has information that accurately reflects the current business practices of the CA, the attestation letter arising from the audit must be dated and received by Microsoft not more than three months from the ending date specified in the attestation letter.

### E. Audit Attestation

Microsoft requires that each auditor complete and submit to Microsoft a Qualifying Attestation. A Qualifying Attestation requires that the auditor completes a Qualifying Attestation Letter.

Microsoft uses a tool to automatically parse audit letters to validate the accuracy of the Qualifying Attestation Letter. This tool is found in the Common Certification Authority Database (CCADB). Work with your auditor to make sure the Qualifying Attestation Letter fulfills the following requirements. If the audit letter fails in any of these categories, a mail is sent back to the CA asking them to update their audit letter.

#### ALL CAS 

- Audit letter must be written in English
- Audit letter must be in a "Text Searchable" PDF format.
- Audit letter must have the auditor's name in the audit letter as recorded in CCADB. 
- Audit letter must list either SHA1 thumbprint or SHA256 thumbprint of audited roots.
- Audit letter must list the date the audit letter was written.
- Audit letter must state the start and end dates of the period that was audited. Note this time period isn't the period the auditor was on-site.
- The audit letter must include the full name of the CA as recorded in CCADB.
- Audit letter must list the audit standards that were used during the audit. Reference WebTrust/ETSI guidelines or [https://aka.ms/auditreqs](https://aka.ms/auditreqs) and list the full name and version of the audit standards referenced.

#### CAs submitting Webtrust audits

Audits conducted by certified WebTrust auditors must have their audit letters uploaded to [https://cert.webtrust.org](https://cert.webtrust.org/). 
    
#### CAs submitting ETSI audits

- Audits conducted by certified ETSI auditors should have their audit letters uploaded to their auditor's website. If the auditor doesn't post on their website, the CA must provide the name and email of the auditor when submitting the audit letter. A Microsoft representative reaches out to the auditor to verify the authenticity of the letter. 
- CAs may submit audits with either the EN 319 411-2 or 411-2 policy. 

### F. Audit Submission

To submit annual audits, refer to the CCADB instructions on how to create an audit case found here: <https://ccadb.org/cas/updates>.

If the CA is applying into the Root Store and isn't in the CCADB, they should email their audit attestation to msroot\@microsoft.com.

## Conventional CA Audit Standards

The Program accepts two types of audit standards: WebTrust and ETSI. For each of the EKUs on the left, Microsoft requires an audit that conforms to the standard marked.

> [!NOTE]
> As of February 2024, CA providers must ensure their S/MIME enabled root CAs and all subordinate CAs capable of issuing S/MIME certificates have been and will continue to be audited against the most recent version of, at minimum, one of the below sets of criteria. 
> 
> - WebTrust Principles and Criteria for Certification Authorities – S/MIME
> - ETSI TS 119 411-6 LCP, NCP, or NCP+

### A. WebTrust Audits

Microsoft will now be requiring the WebTrust Trust Services Principles and Criteria for Certification Authorities -- Code Signing for any audit statements with periods commencing on or after January 1, 2018. This will be required for any CA that has the code signing EKU enabled for their roots. If a CA has the code signing EKU enabled on a root but isn't actively issuing code signing certificates, they can reach out the msroot\@microsoft.com to have the EKU status set to "NotBefore." 

| Criteria | WebTrust for CA v2.1 | SSL Baseline with Network Security v2.3 | Extended Validation SSL v1.6.2 | Extended Validation Code Signing v1.4.1 | Publicly Trusted Code Signing Certificates v1.0.1 | WebTrust Principles and Criteria for Certification Authorities – S/MIME |
| --- | --- | --- | --- | --- | --- | --- |
| Server Authentication (Non-EV) | X | X |  |  |  |
| Server Authentication (non-EV) and Client Authentication only | X | X |  |  |  |
| Server Authentication (EV) | X | X | X |  |  |
| Server Authentication (EV) and Client Authentication only | X | X | X |  |  |
| EV Code Signing | X |  |  | X |  |
| Non-EV Code Signing and Time stamping | X |  |  |  | X |
| Secured Email (S/MIME) | X |  |  |  |  | X |
| Client Authentication (without Server Authentication) | X |  |  |  |  |
| Document Signing | X |  |  |  |  |

### B. ETSI-Based Audits

Note 1: If a CA uses an ETSI-based audit, it must perform a **full** audit annually, and Microsoft won't accept surveillance audits. 
Note 2: All ETSI audits statements must be audited against the CA/Browser Forum requirements and compliance with these requirements must be stated in the audit letter. The ACAB'c [https://acab-c.com](https://acab-c.com) has provided guidance that meets the Microsoft requirements. 

| Criteria | EN 319 411-1: DVCP, OVCP or PTC-BR policies | EN 319 411-1: EVCP policy | EN 319 411-2: QCP-w/QEVCP-w policy (based on EN 319 411-1, EVCP) | EN 319 411-1: LCP, NCP, NCP+ policies | EN 319 411-2: QCP-n, QCP-n-qscd, QCP-l, QCP-l-qscd policies (based on EN 319 411-1, NCP/NCP+) | ETSI EN 319 411-1, LCP, NCP, or NCP+ policies as amended by ETSI TS 119 411-6 or ETSI EN 319 411-2, QCP-n, QCP-I, QCP-n-qscd or QCP-I-qscd policies as amended by ETSI TS 411-6 |
| --- | --- | --- | --- | --- | --- |--- |
| Server Authentication (Non-EV) | X |  |  |  |  |  |
| Server Authentication (non-EV) and Client Authentication only | X |  |  |  |  |  |
| Server Authentication (EV) |  | X |  |  |  | 
| Server Authentication (EV) and Client Authentication only |  | X | X |  |  |  |
| EV Code Signing |  |  | X | X |  |  |
| Non-EV Code Signing and Time stamping |  |  |  | X | X |  |
| Secured Email (S/MIME) |  |  |  | X | X | X|
| Client Authentication (without Server Authentication) |  |  |  | X | X |  |
| Document Signing |  |  |  | X | X | |

## Government CA Requirements

Government CAs might choose to either obtain the previously described WebTrust or ETSI-based audit(s) required of Commercial CAs, or to use an Equivalent Audit. If a Government CA chooses to obtain a WebTrust or ETSI-based audit, Microsoft will treat the Government CA as a Commercial CA. The Government CA can then operate without limiting the certificates it issues.

### A. Equivalent Audit Restrictions

If the Government CA chooses not to use a WebTrust or ETSI audit, it may obtain an Equivalent Audit. In an Equivalent Audit (\"EA\"), the Government CA selects a third-party to perform an audit. The audit has two purposes: (1) to demonstrate that the Government CA complies with local laws and regulations related to certificate authority operation, and (2) to demonstrate that the audit substantially complies with the relevant WebTrust or ETSI standard.

If a Government CA chooses to obtain an EA, Microsoft limits the scope of certificates that the Government CA might issue. Government CAs that issue server authentication certificates must limit the root to government-controlled domains. Governments must limit the issuance of any other certificates to ISO3166 country codes that the country has sovereign control over.

Government CAs must also accept and adopt the appropriate, CAB forum baseline requirements for CAs based on the type of certificates the root issues. However, the Program Requirements and Audit Requirements supersede those requirements in any aspect in which they are in conflict.

All Government CAs entering the Program are subject to the above EA requirements. All Government CAs that are part of the Program before June 1, 2015 will be subject to the previously described EA requirements immediately upon expiration of their then-current audit.

### B. Content of the Equivalent Audit Report

Microsoft requires all Government CAs that submit an EA to provide an attestation letter from the auditor that:

- Attests that the audit is issued by an independent agency, which is authorized by the Government CAs government to conduct the audit.
- Lists the Government CA's government's criteria for auditor qualification, and certifies that the auditor meets this criteria.
- Lists the particular statutes, rules, and/or regulations that the auditor assessed the Government CAs operations against.
- Certifies the Government CA's compliance with the requirements outlined in the named governing statutes, rules, and/or regulations.
- Provides information that describes how the statute's requirements are equivalent to the appropriate WebTrust or ETSI audits.
- Lists Certificate Authorities and third parties authorized by the Government CA to issue certificates on the Government CA's behalf within a certificate chain.
- Documents the full PKI hierarchy.
- Provides the start and end date of the audit period.

## Definitions

#### Government CA

A "Government CA" is an entity that signs the Government Program Agreement.

#### Commercial CA

A "Commercial CA" is an entity that signs the Commercial Program Agreement.

#### Certification Authority

"Certification Authority" or "CA" means an entity that issues digital certificates in accordance with Local Laws and Regulations.

#### Local Laws and Regulations

"Local Laws and Regulations" means the laws and regulations applicable to a CA under which the CA is authorized to issue digital certificates, which set forth the applicable policies, rules, and standards for issuing, maintaining, or revoking certificates, including audit frequency and procedure.

