# Story Bank — Justin Nguyen

Master reusable STAR+R stories. Each story can be adapted across multiple interviews by adjusting the framing to match the JD's language.

---

## STORY-01 — BMS/IoT Detection Design (JPMC)

**Core theme:** Built detection architecture from scratch for OT/IoT environments
**Use for:** Detection Engineering, Threat Hunting, Security Engineer OT roles

- **S:** BMS/IoT environments at JPMC had zero detection coverage for post-exploitation TTPs — EDR policies existed for laptops but not converged OT systems
- **T:** Design and implement detection rules for lateral movement and post-exploitation in BMS/IoT environments
- **A:** Mapped MITRE ATT&CK TTPs relevant to BMS/IoT attacks → built detection rules tuned for OT protocols and building system behavior → iterated to reduce false positives
- **R:** 50% reduction in incident response time for BMS/IoT incidents
- **Reflection:** Learned to start narrow (high-confidence TTPs only) rather than broad coverage — broad rules create noise that erodes SOC trust in detections

**Adapters:**
- Detection Eng framing: "I built high-fidelity detection content for OT environments, owning it end-to-end from gap analysis to production tuning"
- Red Team framing: "I modeled the attacker's view first (MITRE ATT&CK mapping) before writing a single detection rule"
- OT framing: "BMS systems behave differently from IT endpoints — I had to build new detection baselines specific to PLC/BAS communication patterns"

---

## STORY-02 — Kestra Armis Centrix Pipeline (JPMC)

**Core theme:** Built ETL detection data pipeline from OT telemetry source to remediation system
**Use for:** Detection Engineering, Security Automation, Platform Security roles

- **S:** No automated path from Armis Centrix EDR alerts → vulnerability remediation system; analysts were manually triaging every alert
- **T:** Build automated ingest, enrichment, and routing pipeline to eliminate toil and accelerate remediation
- **A:** Designed Kestra workflows: Armis Centrix alert ingest → IOC enrichment → deduplication → formatted output routed to enterprise vulnerability tracker
- **R:** Full automation of the triage loop; reduced analyst toil; improved remediation velocity and visibility
- **Reflection:** Should have added deduplication earlier — duplicate alerts from Armis created noise in the tracker in the first two weeks; now that step is always first in any pipeline I build

**Adapters:**
- Data pipeline framing: "I built an ETL pipeline normalizing OT telemetry from Armis Centrix — ingest, enrichment, and downstream routing"
- SOAR framing: "The Kestra workflow functioned as a lightweight SOAR — automated triage, enrichment, and case creation without a dedicated SOAR platform"
- Scale framing: "This ran across multiple enterprise campuses, processing thousands of alerts per day"

---

## STORY-03 — Multi-Environment Detection Coverage ($3M OT Initiative)

**Core theme:** Unified detection coverage across heterogeneous OT + IT + cloud environment
**Use for:** OT Security Engineer, Senior Security Engineer, Critical Infrastructure roles

- **S:** $3M IoT/OT security initiative required visibility across BMS, IoT sensors, enterprise IT, and cloud-connected systems — each with different telemetry, protocols, and baselines
- **T:** Establish consistent detection coverage and asset visibility across converged environments
- **A:** Deployed Armis Centrix across multiple flagship campuses; normalized asset inventory; unified detection controls across OT and IT layers; aligned to NIST 800-53 and IEC 62443
- **R:** 25% cybersecurity risk reduction across flagship facilities
- **Reflection:** OT environments require separate detection tuning from IT — a rule that works perfectly on Windows endpoints will fire constantly on PLCs operating in their normal cycle. Learned to build separate detection profiles per asset class.

---

## STORY-04 — MITRE ATT&CK Coverage Gap Analysis (JPMC)

**Core theme:** Connected threat model output to detection gaps — closed 4 high-risk coverage holes
**Use for:** Threat Modeling, Detection Engineering, Red Team adjacent roles

- **S:** Threat models existed but weren't connected to detection coverage — teams were modeling threats that had no detections watching for them
- **T:** Map threat model outputs to SIEM detection coverage; identify and close the highest-risk gaps
- **A:** Used ATT&CK Navigator to compare documented TTPs against existing detection rules; identified 12 coverage gaps; built prioritized detection backlog; secured cross-functional buy-in from SOC
- **R:** 4 high-risk gaps closed in Q1; contributed to the 25% risk reduction across facilities
- **Reflection:** ATT&CK coverage mapping is a team sport — involving SOC leads in the gap analysis itself (not just handing them a backlog) made prioritization faster and execution more committed

---

## STORY-05 — West Point SWAG (Offensive OT/ICS Simulation)

**Core theme:** Executed offensive campaigns against SCADA networks to expose vulnerabilities
**Use for:** Red Team, Offensive Security, OT Penetration Testing roles

- **S:** Critical infrastructure operators needed to understand their actual vulnerability to adversaries attacking ICS/SCADA — standard compliance assessments weren't finding real attack paths
- **T:** Simulate realistic offensive cyberattacks against OT/ICS/SCADA systems to identify exploitable paths
- **A:** Designed and executed offensive campaign against OT/SCADA network; mapped attack paths through ICS protocols; identified 3 vulnerability classes lacking standard detection coverage
- **R:** Vulnerabilities and attack paths documented; defense recommendations implemented to harden critical infrastructure
- **Reflection:** The best detections come from running the offense first — you can't write a detection for an attack you've never executed or studied hands-on

---

## STORY-06 — C/C++ Rootkit Development (West Point)

**Core theme:** Engineered offensive tooling demonstrating low-level implementation ability
**Use for:** Offensive Security Engineer, Vulnerability Researcher, Red Team roles

- **S:** Understanding evasion and data exfiltration at implementation level — not just using tools but building them
- **T:** Engineer a stealth rootkit in C/C++ to study data exfiltration and EDR evasion
- **A:** Developed stealth C/C++ rootkit with data exfiltration and evasion capabilities; studied detection bypass techniques; built in reverse engineering environment
- **R:** Functional rootkit with documented evasion techniques; deep understanding of how EDR hooks work at kernel level
- **Reflection:** Building offensive tools made me a better defensive engineer — I understand exactly what EDR needs to see (and what attackers hide) because I've been on both sides
