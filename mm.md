<p align="center">
  <img src="https://img.shields.io/badge/Classification-Public%20OSINT-blue?style=for-the-badge" alt="Classification">
  <img src="https://img.shields.io/badge/Date-29%20July%202026-lightgrey?style=for-the-badge" alt="Date">
  <img src="https://img.shields.io/badge/Author-Kumar%20Palanivelu-darkgreen?style=for-the-badge" alt="Author">
</p>

# 🛡️ Case Study: Kudankulam Nuclear Power Plant Supply Chain Data Breach (July 2026)

> **Disclaimer**  
> This report is an independent educational analysis prepared for portfolio and learning purposes. It is based solely on publicly available news reports, official statements, and open‑source intelligence. No classified, proprietary, or leaked materials have been accessed or included.

---

## 📌 Executive Summary

On **15 July 2026**, international media reported that the extortion group **World Leaks** had published nearly **19,000 files (14.3 GB)** related to India’s Kudankulam Nuclear Power Plant (KKNPP) on the dark web. The data — labelled under the search term “KKNP” — included plant blueprints, ventilation layouts, control‑room floor plans, supplier details, meeting records, and insurance policies.

> ⚠️ **Important:** Reuters reviewed the documents but **could not independently verify their authenticity.** Further, the leaked files do not appear to relate to the nuclear reactor’s core systems (supplied by Russia’s Rosatom), but rather to common service infrastructure.

The files originated not from the nuclear operator itself, but from a server managed by third‑party contractor **Reliance Infrastructure Limited** and hosted by data centre provider **Yotta Data Services**. The Nuclear Power Corporation of India Limited (NPCIL) confirmed the breach involved only “common service balance of plant systems” and stressed these have “no connection with nuclear safety and security,” according to acting CMD Rajesh V. The plant’s operational and safety systems, which are air‑gapped, were never compromised. The breach therefore represents a **supply chain and data confidentiality failure**, not an attack on reactor control. India’s Computer Emergency Response Team (CERT‑In) is investigating.

This case study examines the incident timeline, root causes, impact, and lessons for critical infrastructure security.

---

## 🏭 Background

### Kudankulam Nuclear Power Plant
KKNPP, located in Tamil Nadu, is India’s largest nuclear power station. It uses Russian‑designed VVER‑1000 pressurised water reactors and is being expanded to six units totalling 6,000 MW. The plant is central to India’s civil nuclear energy programme.

In **2018**, Reliance Infrastructure Limited won a contract to design and build the Balance of Plant (common utility infrastructure) for the upcoming Unit 3 and Unit 4, each of 1,000 MW capacity. The contractor handled engineering drawings, procurement, and project management — all of which generated the data later found online.

### The 2019 Precedent
This was not the first cyber‑related alarm at KKNPP. In September 2019, the **Dtrack** malware (attributed to the North Korean Lazarus Group) was found on the plant’s administrative network. A spear‑phishing campaign had targeted senior nuclear scientists. The operational technology network was unaffected then as well, but the incident exposed gaps in perimeter defences and incident disclosure. The 2026 breach repeats the pattern: the plant’s own systems remain untouched, but sensitive information escapes through the supply chain.

---

## 📅 Incident Timeline

| Date | Event | Source |
|------|-------|--------|
| **29 May 2026** | Yotta Data Services detects suspicious ransomware activity on a server assigned to Reliance Infrastructure. The threat is contained, but data had already been exfiltrated. | The Hindu |
| **11 June 2026** | A dataset labelled “KKNP” (nearly 19,000 files, 14.3 GB) appears on the World Leaks dark web repository. | Reuters / India Today |
| **15 July 2026** | Reuters publishes an exclusive report confirming the existence of nuclear‑related files online. Reliance Infrastructure’s stock falls sharply. NPCIL acting CMD Rajesh V tells NDTV that the data pertains only to common service balance of plant systems and has “no connection with nuclear safety and security.” | Reuters, India Today, NDTV |
| **15–16 July 2026** | NPCIL issues a formal statement reiterating that no nuclear safety or security systems were compromised. | NPCIL / The Hindu |
| **As of 29 July 2026** | Forensic audits by CERT‑In and the Department of Atomic Energy continue. The exact intrusion vector has not been publicly confirmed. | — |

---

## 🔍 Technical Analysis

### Threat Actor: World Leaks
World Leaks operates an **extortion‑as‑a‑service** model, focusing on data exfiltration and public shaming rather than encryption. The group had previously hit **Nike** (January 2026) and **Tata Electronics** (June 2026), where it demanded $1.5 million for files containing Apple and Tesla component designs. After the ransom was ignored, data was dumped online — the same modus operandi used against Reliance.

### Attack Vector
- **Entry point:** An internet‑facing enterprise file server belonging to Reliance Infrastructure, hosted at **Yotta Data Services**.
- **Exfiltration:** Before being stopped on 29 May, the attackers scraped a large cache of project documents dated from **2016 to mid‑2025**.
- **No OT compromise:** The plant’s industrial control systems and reactor safety networks are physically air‑gapped. The breach stayed entirely within the contractor’s cloud environment.

---

<!-- Attack‑Path Diagram Placeholder -->
![Supply Chain Attack Path](assets/attack-path-diagram.png)
*Supply chain attack path — Reliance → Yotta Server → World Leaks → Dark Web. The OT air‑gap remained intact.*

---

### Data Exposed
| Category | Details |
|----------|---------|
| Engineering blueprints | Structural, piping, ventilation, cooling circuit drawings for Units 3 & 4 |
| Control room layouts | Floor plans and cabling pathways for common control rooms |
| Supplier & vendor lists | Procurement records, approved manufacturers, contact details |
| Meeting & inspection records | Internal minutes, progress reports, technical correspondence with Rosatom |
| Insurance policies | Terrorism insurance policy documents |

These categories were confirmed by multiple media outlets. However, Reuters could not independently verify the authenticity of individual documents, and the exposed files relate only to common service infrastructure, not the nuclear island.

---

## 📊 Impact Assessment

| Security Objective | Impact | Rationale |
|--------------------|--------|-----------|
| **Confidentiality** | 🔴 High | Extensive technical documentation, supplier identities, and internal communications were publicly exposed. |
| **Integrity** | 🟡 Low | No evidence of tampering with plant systems; only unauthorised copying of files. |
| **Availability** | 🟢 None | Plant generation was never disrupted. |

### National Security & Reputational Risk
- The leak provides adversaries with detailed engineering intelligence that could aid physical or cyber‑enabled sabotage planning.
- It reveals the identities of sub‑contractors, making them targets for further compromise.
- The **seven‑week gap** between detection (29 May) and public disclosure (15 July) drew sharp criticism of India’s breach notification practices.
- Although NPCIL emphasised the data had “no connection with nuclear safety and security,” the aggregation of blueprints, supplier lists, and meeting minutes creates a significant intelligence risk.

---

## 🧠 Root Cause & Contributing Factors

1. **Third‑party supply chain risk** – Sensitive plant data was entrusted to a contractor and stored on a commercial cloud server without adequate protection.
2. **Insufficient data segregation** – Engineering documents that could inform an attack were accumulated in a single repository, accessible via the internet.
3. **Weak cloud security posture** – The breach likely exploited a misconfiguration, unpatched vulnerability, or compromised credentials — a forensic finding yet to be officially released.
4. **Opaque disclosure culture** – As noted by The Hindu, Indian organisations often delay breach announcements, hampering timely containment and collective defence.

---

## 📖 Lessons Learned

- 🛡️ **Air‑gapping the plant isn’t enough.** While OT systems remain safe, the intelligence value of aggregated engineering data is immense. Supply chain data must be protected with the same rigour as control systems.
- ☁️ **Contractor data environments must be isolated and monitored.** Commercial clouds holding critical infrastructure data need continuous security validation, just like the plant’s own networks.
- 📢 **Transparency matters.** Delayed disclosure prevents other potential targets from hardening their defences and undermines public confidence.
- 🔁 **Repeat targeting is a signal.** Two incidents in seven years indicate that KKNPP and its contractors are persistently targeted; proactive threat hunting is essential.

---

## 🛠️ Recommendations

### For Critical Infrastructure Operators
- Encrypt **all** technical deliverables before they leave plant premises or are uploaded to contractor systems.
- Mandate that contractors use isolated, multi‑factor‑authenticated data enclaves, not generic public cloud storage.
- Impose **contractual breach‑notification SLAs** (e.g., within 6 hours of detection) to eliminate voluntary disclosure delays.
- Conduct continuous third‑party attack surface monitoring, not just annual audits.

### For Contractors & Vendors
- Align security controls with the asset owner’s standards (e.g., NIST CSF, ISO 27001).
- Segment project data per client; enforce least‑privilege access and multi‑factor authentication everywhere.
- Perform regular penetration testing of all internet‑facing cloud infrastructure.

### For Regulators
- Develop binding **supply chain cybersecurity standards** for the nuclear sector, akin to NERC CIP in North America.
- Strengthen CERT‑In’s mandate to compel timely breach disclosure from critical infrastructure entities.

---

## 🗺️ MITRE ATT&CK Mapping (High‑Level)

| Tactic | Technique | Relevance |
|--------|-----------|-----------|
| Initial Access | T1190 (Exploit Public‑Facing Application) / T1078 (Valid Accounts) | Likely used to breach the Yotta server. |
| Collection | T1005 (Data from Local System) | Bulk harvesting of project files. |
| Exfiltration | T1041 (Exfiltration Over C2 Channel) | Data transferred to World Leaks infrastructure before public dump. |
| Impact | T1486 (Data Encrypted for Impact) | Ransomware activity was detected but stopped; data already stolen. |

---

## 🏁 Conclusion

The 2026 Kudankulam data leak is a textbook case of **supply chain risk materialising at a critical infrastructure site**. While the plant’s air‑gapped control networks held firm and the exposed data did not touch nuclear safety systems, the contractor’s cloud server became a digital back door for a financially motivated criminal group. This incident reinforces a fundamental security principle: an organisation’s security posture is only as strong as its weakest third‑party link.

### 💭 Personal Reflection
As a cybersecurity learner, this case taught me that technical defences like air gaps must be paired with rigorous data governance and supplier oversight. The real challenge isn’t just keeping attackers out of the reactor — it’s ensuring that an engineering drawing sitting on a contractor’s server doesn’t end up on the dark web. This investigation deepened my understanding of how operational, legal, and communication failures can combine to turn a single server compromise into a national security concern.

---

> 🖼️ **News Screenshots (add to assets/ folder)**
> - Reuters article headline: `assets/reuters-headline.png`  
> - The Hindu editorial: `assets/thehindu-report.png`  
> - NDTV report (optional): `assets/ndtv-report.png`  

---

<!-- 2019 vs 2026 Comparison Image Placeholder -->
![2019 vs 2026 Comparison](assets/2019-vs-2026-comparison.png)
*Side-by-side comparison of the 2019 Dtrack malware incident and the 2026 World Leaks supply chain breach.*

---

## 📚 References

### 2026 Incident (Primary Sources)
1. **Al Jazeera (via Reuters)** – *“Data breach reportedly targets India’s Kudankulam nuclear power plant”*, 16 July 2026.  
   [Link](https://www.aljazeera.com/news/2026/7/16/data-breach-reportedly-targets-indias-kudankulam-nuclear-power-plant)  
   *Reports the breach, the 14.3 GB dataset, and that Reuters reviewed the documents but could not verify authenticity.*

2. **The Hindu** – *“Wealth of lacunae: On the Kudankulam nuclear plant data leak”* (Editorial), 17 July 2026.  
   [Link](https://www.thehindu.com/opinion/editorial/wealth-of-lacunae-on-the-kudankulam-nuclear-plant-data-leak/article71230157.ece)  
   *Provides the 29 May detection date, the June 11 data appearance, and critical commentary on India’s disclosure practices.*

3. **India Today (Reuters)** – *“Files linked to Kudankulam N-power plant exposed in data breach: Reuters”*, 15 July 2026.  
   *Confirms the data came from Reliance Group’s Yotta‑hosted server, the types of files, and the non‑involvement of core reactor systems.*

4. **NDTV** – *“Nuclear Body Underplays Concerns Over Data Breach At India’s Largest Reactor”*, 15 July 2026.  
   *Includes direct quote from NPCIL acting CMD Rajesh V: “These pertain to the common service balance of plant systems that have no connection with nuclear safety and security.”*

5. **Reuters** exclusive report, 15 July 2026 (referenced in the above articles).  
   Additional coverage: **Indian Express**, “Not the first data breach at Kudankulam”, 18 July 2026.

### 2019 Incident (Comparison Source)
6. **Maj Gen P.K. Mallick (VIF)** – *“Cyber Attack on Kudankulam Nuclear Power Plant – A Wake Up Call”*, December 2019.  
   *Used solely for the historical comparison; details the Dtrack malware attack and does not relate to the 2026 breach.*

---

<p align="center">
  <sub>This case study is part of my cybersecurity portfolio — demonstrating the ability to analyse real‑world incidents from open‑source intelligence and present findings in a structured, professional format.</sub>
</p>
