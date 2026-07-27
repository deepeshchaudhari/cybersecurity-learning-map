＝＝＝ ONE-SHOT PROMPT: "The Cybersecurity Landscape — Interactive Teaching Map" ＝＝＝

Build a single, self-contained **`cybersecurity-map.html`** file (all HTML, CSS, and JS inline; no build step; works offline). It is an interactive teaching map of the cybersecurity field. Only external dependency allowed: Google Fonts. No frameworks, no localStorage/sessionStorage.

## Visual design ("dark blueprint")
- Background: deep navy `#0B1420`→`#0E1A29` with a subtle fixed grid (two crossed linear-gradients, 40px, low opacity, radial-masked so it fades). A soft cyan radial glow top-left.
- Palette: ink `#E4ECF5`, dim `#8FA6BF`, faint `#5E7591`, lines `#1D3450`, panels `#122134`. Primary accent cyan `#38BDF8`.
- Seven family accent colors: f1 `#38BDF8`, f2 `#FB7185`, f3 `#A78BFA`, f4 `#34D399`, f5 `#FBBF24`, f6 `#F472B6`, f7 `#FB923C`.
- Fonts: display **Space Grotesk**, body **Inter**, utility/mono **IBM Plex Mono**.
- Feel: technical, calm, projector-legible. Minimal, disciplined; the animations are the one lively element. Rounded 14px cards, thin borders, mono labels/eyebrows. Respect `prefers-reduced-motion` (pause SMIL via `svg.pauseAnimations()`), visible keyboard focus, responsive down to mobile.

## Top byline strip (identity)
A slim bar above the title, with a bottom border, that wraps on mobile:
- A **Blockstash logo** (a white PNG icon) inside a 38px dark rounded chip with a subtle cyan glow, plus the wordmark "Blockstash" and small "blockstash.in" beneath — the whole thing links to `https://blockstash.in`. (Embed the logo as a base64 data URI so it works offline; it's a white icon, so keep the chip dark.)
- A divider, then **Deepesh Chaudhari** / "Founder, Blockstash".
- A spacer, then a **LinkedIn** button (inline SVG icon + "LinkedIn") linking to `https://www.linkedin.com/in/amideepesh/`.

## Header
Eyebrow "TEACHING MAP" (mono, cyan, with a leading rule). H1: "The **Cybersecurity** Landscape" (cyan on the middle word). A lede paragraph. A mono meta row: "7 families · 27 domains · Click a branch → pick a domain → teach".

## Three modes (segmented switcher: Explore / Learning paths / Quiz)
A pill segmented control toggles three views. Active pill = cyan fill.

### 1) EXPLORE (default): branching map + detail panel (two columns, stacks on mobile)
- LEFT — a tree. A mono "Root · Cybersecurity" trunk label, then 7 **family** accordion cards (color-coded left border + a rotating square node + chevron; one starts open). Each expands to its **domain** leaves (dashed connector line, small ringed bullet). Selecting a leaf highlights it (filled with family color) and renders the detail panel.
- A search box (filters domains by name/topic/tool, auto-expanding matching families) and a "Reset map" button sit above the tree.
- RIGHT — a sticky **detail panel** with a top accent bar in the family color. Empty state prompts selection. On select, show, in order: family eyebrow, domain name (Space Grotesk), one-line definition, **an animation** (see below), then chip sections: **Prerequisites**, **Core topics**, **Tools of the trade** (mono chips), **Where it leads** (roles, in accent color), **Certifications** (amber mono chips). Never expose file paths or the mechanism; just render.

### 2) LEARNING PATHS: a grid of 5 track cards
Each card = colored left border, title, tagline, and a numbered vertical step list with a connector line. Steps 1–4 are the shared **foundations** (muted): "Networking & TCP/IP", "Operating systems & Linux", "Scripting (Python / Bash)", "Security fundamentals". Following steps are **domains** rendered as clickable buttons (with a ↗) that jump to that domain in Explore. Tracks:
- **Defender · Blue Team** (cyan) — foundations → Network Security → Endpoint → SOC → Incident Response → DFIR.
- **Attacker · Red Team** (rose) — foundations → Network Security → Vulnerability Mgmt → Penetration Testing → Red Teaming → Exploit Dev.
- **AppSec & Cloud** (violet) — foundations → AppSec → API & Mobile → Cloud → DevSecOps.
- **Investigator · Forensics** (pink) — foundations → DFIR → Malware Analysis → Threat Intelligence → OSINT & Blockchain Forensics.
- **GRC & Risk** (amber) — Security fundamentals → Risk & business basics → Governance & Risk → Compliance & Audit → Security Awareness → BC/DR.
A footnote: paths overlap and aren't the only way in.

### 3) QUIZ: single-question self-check
One question at a time, options shuffled each render, instant correct/wrong coloring, a one-line explanation, running score, Next button, and a final score screen with a message tier and Restart. Questions (answer + short "why"):
1. Chain of custody / recovering digital evidence → **Digital Forensics (DFIR)**.
2. OWASP Top 10 is central to → **Application Security**.
3. A SOC analyst mainly uses → **SIEM**.
4. MITRE ATT&CK maps adversary → **Tactics & techniques**.
5. MFA, SSO, least privilege → **Identity & Access Management**.
6. Reentrancy is a bug in → **Blockchain / Web3 smart contracts**.
7. CVSS prioritises → **Vulnerabilities**.
8. Detonating a file in an isolated sandbox → **Malware Analysis**.
9. ISO 27001 & SOC 2 → **Governance, Risk & Compliance**.
10. Tracing funds across wallets → **OSINT & Blockchain Forensics**.
11. Adversarial perturbation flipping a prediction → **AI / ML Security**.
12. Shifting security "left" into CI/CD → **DevSecOps**.
(Give each 3 plausible distractors.)

## Per-domain animations
Each domain has a small inline SVG scene (~340×130 viewBox) using SMIL animation, looping, with a one-line mono caption. Accent parts use `currentColor` (set to the family color); threats red `#FB7185`, success green `#34D399`, neutral `#3A5170`. Keep them simple and legible. Intended mechanic per domain:
- Network Security: green packets pass a firewall bar; a red one is stopped at it.
- Endpoint: shields pulse over 3 devices; a threat drops onto one and retreats.
- SOC: a rotating radar sweep with a blip + flickering log bars.
- Incident Response: a dot loops a ring through Detect→Contain→Eradicate→Recover.
- Penetration Testing: a magnifier scans a brick wall; a gap glows when found.
- Red Teaming: an attacker dot hops inward through 3 nested layers to a pulsing core star.
- Vulnerability Mgmt: a scan line sweeps a grid of asset tiles that flip to red/amber/green.
- Exploit Dev: a fill bar grows past a buffer boundary marker and turns red (overflow).
- AppSec: a highlight scans code lines; a red bug shrinks to 0 and "fixed" appears.
- Cloud: a padlock's shackle closes over a cloud (three circles); "config locked".
- DevSecOps: build boxes ride a conveyor through a security gate that pulses green.
- API & Mobile: a request token flies client→API, a green response returns; a lock icon.
- Cryptography: "HELLO" crossfades to ciphertext through a lock; "ENCRYPT →".
- IAM: PWD + MFA factors light up in sequence, gate barrier lifts, "ACCESS GRANTED".
- Data & Privacy: DB cylinder rows mask to ****/XXXX (incl. an "Aadhaar" field); a shield with a check.
- Governance & Risk: a gauge arc fills and a needle sweeps LOW→HIGH.
- Compliance & Audit: checklist items (ISO 27001, SOC 2, PCI-DSS) tick in turn; a rotated "PASS" stamp.
- Security Awareness: a phishing hook + envelope dangles at a person; a red X, then it yanks up.
- BC/DR: primary server fails (red X), flow reroutes to the green backup (check).
- DFIR: a magnifier sweeps a timeline; hidden artifact dots reveal as it passes.
- Threat Intelligence: edges draw from a red central ACTOR node out to lighting IOC nodes.
- Malware Analysis: a red blob pulses in a dashed SANDBOX; a scan line reveals inner structure.
- OSINT & Blockchain Forensics: a coin hops wallet→wallet across a chain; the last node gets a red flag.
- IoT/OT/ICS: a signal travels a pipeline through PLC gears; a shield over one; "SCADA / OT".
- AI/ML Security: a neural net (3→4→2 nodes) with a red "+noise" pulse flipping output CAT ✓ → DOG ✗.
- Hardware & Embedded: a probe on an MCU chip; a moving dot traces a waveform; "KEY LEAKED".
- Blockchain/Web3: blocks chain in sequence; a red reentrancy loop is caught by a green audit shield.

## Full dataset (7 families → 27 domains)
For each domain: name · definition · Prerequisites · Core topics · Tools · Roles · Certifications.

**A. Defensive Security** (Blue Team — detect, defend, respond)
1. Network Security — Protecting data in transit and the infrastructure that carries it. Prereq: TCP/IP networking, OSI model, Linux basics. Topics: Firewalls, IDS/IPS, VPNs, Network segmentation, Zero Trust, TLS. Tools: Wireshark, Suricata, Zeek, pfSense, Nmap. Roles: Network Security Engineer, NOC Analyst. Certs: CompTIA Network+, Security+, CCNA Security.
2. Endpoint Security — Securing laptops, servers, phones, every device. Prereq: OS internals, Windows/Linux admin, Networking basics. Topics: EDR/XDR, Host hardening, Patch management, Antivirus, Device control. Tools: CrowdStrike, MS Defender, SentinelOne, osquery. Roles: Endpoint Security Engineer. Certs: Security+, GCED.
3. Security Operations (SOC) — 24/7 monitoring, triage, alerting from a central hub. Prereq: Networking, Log & OS basics, Security fundamentals. Topics: SIEM, Log analysis, Alert triage, Detection engineering, SOAR. Tools: Splunk, Microsoft Sentinel, Elastic SIEM, Wazuh. Roles: SOC Analyst (T1–T3), Detection Engineer. Certs: Security+, CySA+, BTL1.
4. Incident Response — Containing, eradicating, recovering from breaches. Prereq: Networking, OS internals, SOC/monitoring basics. Topics: IR lifecycle, Containment, Playbooks, Chain of custody, Post-incident review. Tools: TheHive, Velociraptor, GRR, Cortex. Roles: Incident Responder, DFIR Analyst. Certs: GCIH, CySA+, BTL1.

**B. Offensive Security** (Red Team — find gaps first)
5. Penetration Testing — Authorized simulated attacks on systems/apps. Prereq: Networking, Linux, Scripting (Python/Bash), Web basics. Topics: Reconnaissance, Exploitation, Privilege escalation, OWASP Top 10, Reporting. Tools: Metasploit, Burp Suite, Kali Linux, sqlmap, Nmap. Roles: Penetration Tester, Ethical Hacker. Certs: OSCP, PNPT, CEH, eJPT.
6. Red Teaming — Full-scope adversary simulation of people, process, tech. Prereq: Pentesting experience, Active Directory, Windows internals. Topics: MITRE ATT&CK, C2 frameworks, Social engineering, Evasion, Physical intrusion. Tools: Cobalt Strike, Sliver, BloodHound, Covenant. Roles: Red Team Operator. Certs: OSEP, CRTO, GPEN.
7. Vulnerability Management — Find, score, track weaknesses at scale. Prereq: Networking, OS basics, Security fundamentals. Topics: Scanning, CVSS scoring, Patch prioritization, Attack surface mgmt. Tools: Nessus, Qualys, OpenVAS, Tenable. Roles: Vulnerability Analyst. Certs: Security+, CySA+.
8. Exploit Development — Research flaws, build working exploits. Prereq: C/Assembly, OS & memory internals, Reverse engineering. Topics: Reverse engineering, Fuzzing, Buffer overflows, Shellcode, 0-days. Tools: Ghidra, IDA Pro, GDB, pwntools, AFL. Roles: Security Researcher, Exploit Developer. Certs: OSED, OSCE³, GXPN.

**C. Application & Cloud** (build security into software/platforms)
9. Application Security (AppSec) — Securing software across the lifecycle. Prereq: A programming language, Web fundamentals, OWASP Top 10. Topics: OWASP Top 10, SAST/DAST, Secure code review, Threat modeling. Tools: Burp Suite, Semgrep, Snyk, OWASP ZAP. Roles: Application Security Engineer. Certs: CSSLP, GWAPT, BSCP.
10. Cloud Security — Protecting workloads/data in AWS, Azure, GCP. Prereq: Cloud fundamentals, Networking, IAM basics. Topics: IAM policies, CSPM, Misconfiguration, Shared responsibility, Containers. Tools: Prowler, ScoutSuite, Wiz, AWS Security Hub. Roles: Cloud Security Engineer. Certs: AWS Security Specialty, AZ-500, CCSP.
11. DevSecOps — Automating security in CI/CD; shifting left. Prereq: CI/CD basics, Scripting, Containers/IaC. Topics: Shift-left, IaC scanning, Secrets management, SBOM, Pipeline security. Tools: Trivy, Checkov, HashiCorp Vault, GitLab CI. Roles: DevSecOps Engineer. Certs: Certified DevSecOps Pro, CKS.
12. API & Mobile Security — Securing APIs and mobile apps. Prereq: Web & API fundamentals, HTTP, Mobile basics. Topics: API authentication, OWASP API Top 10, Cert pinning, Mobile RE. Tools: Postman, MobSF, Frida, Burp Suite. Roles: API Security Specialist. Certs: BSCP, GMOB.

**D. Cryptography & Identity** (protect secrets, control access)
13. Cryptography — The math of securing data, messages, identities. Prereq: Discrete math, Number theory basics, Programming. Topics: Symmetric/asymmetric, Hashing, PKI, Digital signatures, Post-quantum. Tools: OpenSSL, GnuPG, Hashcat, CyberChef. Roles: Cryptographer, PKI Engineer. Certs: EC-Council ECES, (largely academic).
14. Identity & Access Management — Managing identities and permissions. Prereq: Directory services, Networking, OAuth/SAML. Topics: SSO, MFA, RBAC, Least privilege, Federation, Zero Trust. Tools: Okta, Entra ID, Keycloak, CyberArk. Roles: IAM Engineer. Certs: SC-300, Okta Certified, CIAM.
15. Data Security & Privacy — Protecting sensitive data; meeting privacy law. Prereq: Database basics, Security fundamentals, Privacy-law awareness. Topics: Encryption at rest, DLP, Data classification, GDPR/DPDP, Masking. Tools: MS Purview, Varonis, BigID. Roles: Privacy Engineer, Data Protection Officer. Certs: CIPP, CDPSE, DCPP (India).

**E. Governance, Risk & Compliance** (align security with business/law)
16. Governance & Risk — Policy and organizational risk. Prereq: Security fundamentals, Risk basics, Business awareness. Topics: Risk assessment, Security policy, NIST CSF, ISO 27001, Business impact. Tools: Risk registers, Archer, Vanta. Roles: GRC Analyst, CISO. Certs: CISSP, CRISC, ISO 27001 LI.
17. Compliance & Audit — Proving controls meet standards/regulations. Prereq: Security fundamentals, Audit basics, Framework familiarity. Topics: ISO 27001, SOC 2, PCI-DSS, HIPAA, Evidence collection. Tools: Vanta, Drata, AuditBoard. Roles: Compliance Analyst, IT Auditor. Certs: CISA, ISO 27001 LA, CRISC.
18. Security Awareness — People as the first line of defense. Prereq: Security fundamentals, Communication skills. Topics: Phishing simulation, Human risk, Security culture, Policy training. Tools: KnowBe4, GoPhish, Proofpoint. Roles: Security Awareness Manager. Certs: SANS Security Awareness, Security+.
19. Business Continuity & DR — Keeping the business running through disruption. Prereq: IT operations, Risk basics. Topics: BCP, Disaster recovery, RTO/RPO, Tabletop exercises, Resilience. Tools: Runbooks, Backup platforms. Roles: BC/DR Specialist. Certs: CBCP, ISO 22301 LI.

**F. Intelligence & Forensics** (investigate attackers, evidence, threats)
20. Digital Forensics (DFIR) — Recovering and analyzing digital evidence. Prereq: OS internals, File systems, Networking. Topics: Disk & memory forensics, Chain of custody, Timeline analysis, Artifacts, Anti-forensics. Tools: Autopsy, Volatility, FTK, Magnet AXIOM. Roles: Digital Forensic Analyst. Certs: GCFA, GCFE, EnCE.
21. Threat Intelligence — Studying adversaries, techniques, indicators. Prereq: Security fundamentals, Networking, Analytical writing. Topics: IOCs, MITRE ATT&CK, Actor tracking, Intel lifecycle, TLP. Tools: MISP, OpenCTI, VirusTotal, Recorded Future. Roles: Threat Intelligence Analyst. Certs: GCTI, CTIA.
22. Malware Analysis — Dissecting malicious code to detect it. Prereq: Assembly/C, OS internals, Reverse engineering. Topics: Static/dynamic analysis, Sandboxing, Unpacking, YARA rules, RE. Tools: Ghidra, REMnux, ANY.RUN, Cuckoo. Roles: Malware Analyst, Reverse Engineer. Certs: GREM, eCMAP.
23. OSINT & Blockchain Forensics — Tracing people, assets, crypto across open sources and the chain. Prereq: Research skills, Networking, Blockchain basics. Topics: OSINT, On-chain analysis, Wallet attribution, Laundering typologies, Crypto tracing. Tools: Maltego, SpiderFoot, Chainalysis, Chain explorers. Roles: OSINT Investigator, Crypto Forensic Investigator. Certs: GOSI, Chainalysis (CReX), TRM/Elliptic training.

**G. Specialized & Emerging** (new attack surfaces)
24. IoT / OT / ICS Security — Securing industrial systems and critical infrastructure. Prereq: Networking, Embedded basics, Protocols (Modbus…). Topics: SCADA, PLCs, Purdue model, Modbus/protocols, Safety. Tools: Shodan, Claroty, Wireshark, Nmap. Roles: OT Security Engineer. Certs: GICSP, GRID, ISA/IEC 62443.
25. AI / ML Security — Defending ML systems; using AI in defense. Prereq: Machine-learning basics, Python, Security fundamentals. Topics: Adversarial ML, Prompt injection, Data poisoning, Model theft, LLM security. Tools: Garak, PyRIT, ART toolbox. Roles: AI Security Researcher. Certs: (emerging field), AI security training.
26. Hardware & Embedded — Attacking/defending chips, firmware, devices. Prereq: Electronics basics, C/Assembly, Reverse engineering. Topics: Firmware analysis, Side-channel attacks, JTAG, Secure boot, TPM. Tools: ChipWhisperer, Binwalk, Bus Pirate. Roles: Hardware Security Researcher. Certs: (specialized; few formal certs).
27. Blockchain / Web3 Security — Auditing smart contracts; securing dApps. Prereq: Solidity/smart contracts, Blockchain fundamentals, AppSec basics. Topics: Contract audits, Reentrancy, DeFi exploits, Wallet security, Consensus attacks. Tools: Slither, Mythril, Foundry, Echidna. Roles: Smart Contract Auditor. Certs: Smart-Contract Auditor cert, (audit/CTF portfolio).

## Output
Return only the finished `cybersecurity-map.html`. It must run by opening the file — no server, no external JS/CSS besides Google Fonts. Keep chips/labels in the user's own words; represent tool/cert lists as "representative, not exhaustive."

＝＝＝ END OF PROMPT ＝＝＝
