# Phishing Email Analysis & Threat Investigation

## Task

**Analyze a Phishing Email Sample**

---

# Objective

The objective of this task is to analyze a suspicious email sample, identify phishing indicators, understand social engineering techniques, and document the findings through a structured email security investigation.

This assessment focuses on identifying Business Email Compromise (BEC) techniques, email authentication checks, sender analysis, and threat indicators.

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
| WHOIS (who.is) | Domain registration analysis |
| IPinfo.io | IP reputation and geolocation analysis |
| Email Header Analysis | Email authentication verification |

---

# Email Sample Information

| Field | Details |
|---|---|
| Email Subject | Invoice SI-4471 & Updated Bank Details for Future Payments |
| Date | 07 July 2026, 3:28 PM IST |
| Sender | r********.k********@apex-steeltraders.co |
| Return-Path | r********.k********@apex-steeltraders.co |
| Reply-To | a******.p********@apexsteel-billing.com |
| Classification | Malicious |
| Attack Category | Business Email Compromise (BEC) |
| Attachment | invoice-si****-apex-steel.pdf |

---

# Investigation Methodology

The email sample was analyzed using a manual investigation approach.

The following steps were performed:

1. Examined sender information.
2. Compared sender and Reply-To domains.
3. Reviewed email authentication results.
4. Analyzed email body content.
5. Identified social engineering techniques.
6. Performed domain investigation using WHOIS.
7. Reviewed sending IP information.
8. Documented phishing indicators and risks.

---

# Email Overview

The email impersonated a legitimate business vendor and attempted to redirect an invoice payment to a new bank account.

The message requested urgent payment processing and included an invoice attachment.

This behavior matches a **Business Email Compromise (BEC)** attack pattern where attackers manipulate employees into transferring money to fraudulent accounts.

---

# Sender Analysis

## Sender Information

```

Sender:
r********.k********@apex-steeltraders.co

```

The sender address was designed to appear as a legitimate business communication.

However, additional investigation identified suspicious characteristics.

---

# Reply-To Analysis

## Reply-To Address

```

a******.p********@apexsteel-billing.com

```

## Finding

The sender domain and Reply-To domain were different.

| Parameter | Domain |
|---|---|
| Sender Domain | apex-steeltraders.co |
| Reply-To Domain | apexsteel-billing.com |

## Security Impact

This technique is commonly used in phishing campaigns.

The attacker allows the email to appear legitimate while redirecting replies to an attacker-controlled mailbox.

**Risk Level: Critical**

---

# Email Authentication Analysis

## SPF

```

Result: PASS

```

The email passed SPF verification for the sender domain.

---

## DKIM

```

Result: PASS

```

The email contained a valid DKIM signature.

---

## DMARC

```

Result: PASS

```

The email passed DMARC validation.

---

## Analysis

Email authentication passing does not always indicate that an email is safe.

SPF, DKIM, and DMARC verify email authorization but cannot detect:

- Vendor impersonation
- Social engineering
- Fraudulent payment requests

---

# Email Body Analysis

## Observed Characteristics

The email contained:

- Invoice payment request
- Bank account update request
- Urgent payment timeline
- Financial pressure tactics
- Request for confirmation after payment

---

# Social Engineering Indicators

| Indicator | Observation | Risk |
|---|---|---|
| Urgency | Requested priority payment | High |
| Financial Request | Invoice payment involved | Critical |
| Account Change Request | New payment details provided | Critical |
| Vendor Impersonation | Pretended to be supplier | High |
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
Funds Redirected To Attacker

```

---

# Attachment Analysis

## Identified Attachment

```

File:
invoice-si****-apex-steel.pdf

```

## Analysis Status

The attachment was identified during email investigation.

However, malware analysis and static file analysis were not performed as part of this assessment.

Recommended future analysis:

- Calculate file hash
- Check PDF metadata
- Extract embedded URLs
- Perform sandbox analysis

---

# OSINT Verification

## WHOIS Investigation

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

- Reply-To domain differed from sender domain.
- Domain ownership information should be verified during incident response.

---

# IP Analysis

Tool Used:

```

IPinfo.io

```

Sending IP:

```

103.22.xxx.xxx

```

Observation:

The sending infrastructure information was reviewed as part of the investigation.

IP location alone is not considered a standalone phishing indicator and must be analyzed with other evidence.

---

# Indicators of Compromise (IOC)

| Type | Indicator |
|---|---|
| Sender Domain | apex-steeltraders.co |
| Reply-To Domain | apexsteel-billing.com |
| Suspicious Domain | apexsteel-billing.com |
| Attachment | invoice-si****-apex-steel.pdf |
| Attack Type | BEC / Invoice Fraud |

---

# Phishing Indicators Identified

| Finding | Status | Severity |
|---|---|---|
| Reply-To Domain Mismatch | Detected | Critical |
| Vendor Impersonation | Detected | High |
| Payment Redirection Request | Detected | Critical |
| Social Engineering Language | Detected | High |
| Suspicious Attachment | Requires Further Analysis | Medium |

---

# Risk Assessment

| Category | Rating |
|---|---|
| Attack Type | Business Email Compromise |
| Financial Risk | Critical |
| User Manipulation Risk | High |
| Overall Severity | Critical |

---

# MITRE ATT&CK Mapping

## T1566 - Phishing

Attackers use phishing emails to manipulate users into performing unauthorized actions.

---

## T1566.001 - Spearphishing Attachment

The attacker used an invoice document attachment as part of the phishing attempt.

---

# Recommended Actions

- Verify bank account changes through a trusted communication channel.
- Avoid processing payment changes based only on email requests.
- Block suspicious domains identified during investigation.
- Conduct phishing awareness training for employees.
- Implement multi-person approval for high-value payments.
- Enable email security monitoring.
- Report suspicious emails to the security team.

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
- Understood Reply-To spoofing techniques.
- Learned that SPF, DKIM, and DMARC alone cannot guarantee email legitimacy.
- Practiced OSINT-based email investigation.
- Improved phishing detection skills.

---

# Conclusion

The analyzed email was identified as a **Business Email Compromise (BEC) phishing attempt** designed to redirect invoice payments to an unauthorized account.

The primary indicators included Reply-To domain mismatch, vendor impersonation, payment urgency, and financial manipulation techniques.

This investigation demonstrates the importance of email verification, security awareness, and proper payment validation procedures in preventing phishing-based financial fraud.

---

# References

- MITRE ATT&CK Framework
- OWASP Phishing Awareness Guidelines
- WHOIS Domain Lookup
- IPinfo.io
```
