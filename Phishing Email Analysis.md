# Phishing Email Analysis & Threat Investigation

## Task

**Analyze a Phishing Email Sample**

---

# Objective

The objective of this task is to analyze a suspicious email sample, identify phishing indicators, understand social engineering techniques, and document the findings through a structured email security investigation.

This analysis helps in understanding phishing attacks, Business Email Compromise (BEC) techniques, and methods used by attackers to manipulate victims into performing unauthorized actions.

---

# Lab Environment

| Component | Details |
|---|---|
| Operating System | Kali Linux |
| Analysis Method | Manual Email Analysis |
| Sample Source | Cybersecurity Training Platform |
| Investigation Type | Phishing Email Investigation |
| Report Type | GitHub Portfolio |

---

# Tools Used

| Tool | Purpose |
|---|---|
| WHOIS (who.is) | Domain registration investigation |
| IPinfo.io | IP geolocation analysis |
| Email Header Analysis | Sender and authentication verification |

---

# Email Sample Information

| Field | Details |
|---|---|
| Email Subject | Invoice SI-4471 & Updated Bank Details for Future Payments |
| Date | 07 July 2026, 3:28 PM IST |
| Sender Name | Ramesh Kulkarni |
| Sender Email | ramesh.kulkarni@apex-steeltraders.co |
| Return-Path | ramesh.kulkarni@apex-steeltraders.co |
| Reply-To | accounts.payments@apexsteel-billing.com |
| Classification | Malicious |
| Attack Category | Business Email Compromise (BEC) |
| Attachment | invoice-si4471-apex-steel.pdf |

---

# Investigation Methodology

The email sample was analyzed manually using the following approach:

1. Examined sender information.
2. Compared sender domain and reply-to domain.
3. Reviewed email authentication results.
4. Analyzed email body for social engineering indicators.
5. Investigated suspicious domains using WHOIS.
6. Checked sending IP information.
7. Evaluated attachment risk.
8. Documented indicators of compromise.

---

# Email Overview

The email impersonates a legitimate vendor, **Apex Steel Traders**, and attempts to convince the recipient to transfer an invoice payment of:

```

Amount: ₹4,85,600

```

The attacker requested the recipient to update payment details and transfer funds to a new bank account mentioned in the attached invoice.

This behavior matches a common **Business Email Compromise (BEC)** attack pattern.

---

# Sender Analysis

## Sender Information

```

From:
[ramesh.kulkarni@apex-steeltraders.co](mailto:ramesh.kulkarni@apex-steeltraders.co)

```

The sender address appears legitimate because it uses a domain similar to the expected vendor domain.

However, further analysis identified a suspicious mismatch.

---

# Reply-To Analysis

## Reply-To Address

```

[accounts.payments@apexsteel-billing.com](mailto:accounts.payments@apexsteel-billing.com)

```

## Finding

The sender domain and reply-to domain are different.

| Parameter | Domain |
|---|---|
| From Domain | apex-steeltraders.co |
| Reply-To Domain | apexsteel-billing.com |

## Risk

This technique is commonly used in phishing and BEC attacks.

Victims may believe they are communicating with the legitimate vendor while responses are redirected to the attacker-controlled mailbox.

---

# Email Authentication Analysis

## SPF

```

Result: PASS

```

The email passed SPF validation for the sender domain.

## DKIM

```

Result: PASS

```

The email contains a valid DKIM signature.

## DMARC

```

Result: PASS

```

The email passed DMARC verification.

## Analysis

Although SPF, DKIM, and DMARC passed, the email can still be malicious.

Authentication mechanisms verify email authorization, but they do not confirm whether the sender is trustworthy or whether the message content is legitimate.

---

# Email Body Analysis

## Observed Content

The email states:

- Invoice payment request
- Updated bank account information
- Immediate payment requirement
- Financial urgency
- Request for confirmation after transfer

---

# Social Engineering Indicators

| Indicator | Observation | Risk |
|---|---|---|
| Urgency | Payment required on priority | High |
| Financial Request | ₹4,85,600 invoice payment | Critical |
| Account Change Request | New bank details provided | Critical |
| Authority Impersonation | Pretends to be vendor accounts department | High |
| Business Context | Uses invoice-related communication | High |
| Deadline Pressure | Quarter closing reference | Medium |

---

# Business Email Compromise (BEC) Analysis

## Attack Type

```

Vendor Impersonation / Invoice Fraud

```

## Attack Flow

```

Attacker
|
|
Impersonates Vendor
|
|
Sends Fake Invoice Update Email
|
|
Victim Changes Payment Details
|
|
Money Transferred To Attacker Account

```

---

# Attachment Analysis

## Attachment Identified

```

File Name:
invoice-si4471-apex-steel.pdf

```

## Analysis Status

Attachment was identified during the investigation.

However, static file analysis or malware analysis was not performed as part of this assessment.

Recommended future analysis:

- File hash calculation
- PDF metadata inspection
- URL extraction
- Malware sandbox analysis

---

# OSINT Verification

## WHOIS Analysis

Tool Used:

```

who.is

```

Finding:

```

Domain:
apexsteel-billing.com

```

Observation:

- Reply-To domain differs from the original sender domain.
- Domain registration information requires further verification.

---

# IP Geolocation Analysis

Tool Used:

```

ipinfo.io

```

Sending IP:

```

103.22.8.190

```

Observation:

The sending infrastructure information was reviewed during investigation.

IP location alone is not considered a standalone indicator of malicious activity; it must be evaluated with other evidence.

---

# Indicators of Compromise (IOC)

| Type | Indicator |
|---|---|
| Sender Email | ramesh.kulkarni@apex-steeltraders.co |
| Reply-To Email | accounts.payments@apexsteel-billing.com |
| Suspicious Domain | apexsteel-billing.com |
| Attachment | invoice-si4471-apex-steel.pdf |
| Payment Amount | ₹4,85,600 |

---

# Phishing Indicators Identified

| Finding | Status | Severity |
|---|---|---|
| Reply-To Domain Mismatch | Detected | Critical |
| Fake Vendor Communication | Detected | High |
| Bank Detail Change Request | Detected | Critical |
| Payment Urgency | Detected | High |
| Invoice-Based Social Engineering | Detected | High |
| Suspicious Attachment | Requires Analysis | Medium |

---

# Risk Assessment

| Category | Rating |
|---|---|
| Attack Type | Business Email Compromise |
| Financial Risk | Critical |
| Data Exposure Risk | Medium |
| User Manipulation Risk | High |
| Overall Severity | Critical |

---

# MITRE ATT&CK Mapping

## Technique: Phishing

**T1566 - Phishing**

Attackers use phishing emails to manipulate users into performing unauthorized actions.

---

## Technique: Spearphishing Link / Attachment

**T1566.001 - Spearphishing Attachment**

The attacker used an invoice PDF attachment as part of the social engineering attempt.

---

# Recommended Actions

- Verify bank account changes through an independent communication channel.
- Do not trust payment updates received only through email.
- Block suspicious domains identified during analysis.
- Train finance teams against invoice fraud attacks.
- Enable email security monitoring.
- Implement multi-person approval for high-value payments.
- Report suspected phishing attempts to the security team.

---

# Evidence

## Screenshot 1

Email Header Analysis

```

(Add Screenshot Here)

```

---

## Screenshot 2

WHOIS Domain Investigation

```

(Add Screenshot Here)

```

---

## Screenshot 3

IP Information Analysis

```

(Add Screenshot Here)

```

---

# Key Learnings

- Learned how to identify Business Email Compromise attacks.
- Understood the importance of Reply-To verification.
- Learned that SPF, DKIM, and DMARC alone cannot confirm email legitimacy.
- Practiced OSINT-based email investigation.
- Improved phishing detection and threat analysis skills.

---

# Conclusion

The analyzed email was identified as a **Business Email Compromise (BEC) attack** attempting to redirect a legitimate invoice payment to an unauthorized bank account.

The main indicators were the Reply-To domain mismatch, payment redirection request, urgency tactics, and vendor impersonation techniques.

This investigation demonstrates the importance of email verification, user awareness, and security controls in preventing phishing-based financial fraud.

---

# References

- Nmap Official Documentation  
- OWASP Phishing Awareness Guidelines  
- MITRE ATT&CK Framework  
- WHOIS Domain Lookup  
- IPinfo.io
```
