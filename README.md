# Unified Compliance Framework for AyuHealth Tech Solutions

This repository documents the design of a unified compliance program for AyuHealth Tech Solutions, a Series-B HealthTech startup targeting the US and Indian healthcare markets, integrating ISO 27001, SOC 2, HIPAA, SOX, and NIST CSF 2.0 using the Adobe Common Controls Framework (CCF).

## Executive Summary: "Test Once, Comply Many"

Healthcare startups expanding into regulated markets face "compliance fatigue" when each standard is implemented and audited in isolation, generating duplicated evidence requests, inconsistent control implementations, and chronic distraction for engineering teams. This project uses Adobe's Common Controls Framework (CCF) to rationalize over 4,300 requirements into approximately 315 common controls, allowing AyuHealth to implement and test one control once and inherit coverage across ISO 27001, SOC 2, HIPAA, SOX ITGC, and NIST CSF 2.0.

By mapping the strictest requirement across frameworks into unified CCF control IDs (for example IAM-01 for provisioning, DP-01 for encryption, OPS-01 for immutable backups), the organization can operate a single "Trust Assurance Engine" that drives multiple certifications and regulatory obligations in parallel. The result is a measurable reduction in audit fatigue, faster sales cycles for US hospital deals, and earlier IPO-readiness through SOX-aligned IT general controls.

## Technical Deep Dive: IAM and Data Protection

The unified framework makes Identity and Access Management (IAM) and Data Protection the backbone of both security posture and audit readiness, with controls deliberately aligned to ISO Annex A, SOC 2 Security & Availability, HIPAA Security Rule, NIST CSF Protect, and SOX ITGC requirements.

### Phishing-Resistant IAM with FIDO2/YubiKeys and Okta RBAC

Control IAM-02 mandates FIDO2 hardware security keys (YubiKeys) for administrators and privileged users, eliminating SMS MFA and significantly reducing credential-phishing and SIM-swap risk while satisfying MFA expectations across ISO 27001, SOC 2, HIPAA, and NIST CSF PR.AA. RBAC is implemented via Okta as the single identity plane for AWS, the production database, and the EHR integration layer (IAM-01), with direct database access restricted to a monitored "break-glass" account and quarterly access reviews (IAM-03) to meet SOX change and access control expectations.

### Data Protection with AWS S3 Object Lock and End-to-End Encryption

Control OPS-01 configures AWS Backup to take daily snapshots of critical databases stored in S3 buckets with Object Lock in Compliance Mode, creating immutable, WORM backups that cannot be deleted even by root within the retention window, directly mitigating ransomware and supporting HIPAA and ISO disaster-recovery requirements. Control DP-01 enforces "encryption everywhere" using AWS KMS AES-256 for all EBS volumes and S3 buckets, TLS 1.2 for data in transit, and BitLocker/FileVault on endpoints, complemented by DP-02 endpoint DLP to prevent unauthorized exfiltration of PHI, PII, and financial data.

Together, these IAM and Data Protection controls provide a coherent chain from user identity, to system access, to data confidentiality and integrity, enabling consistent evidence across ISO 27001 Annex A, SOC 2 TSC, HIPAA Security Rule safeguards, NIST CSF PR.AA/PR.DS, and SOX ITGC over financial systems.

## Risk Management: NIST SP 800-30 and the 2025 Threat Landscape

The risk assessment follows NIST SP 800-30, applying a structured process of identifying threat sources, vulnerabilities, likelihood, and impact, then calculating a risk score as the product of likelihood and impact, with risks >= 12 classified as "Unacceptable" and requiring immediate remediation. The resulting risk matrix highlights ransomware, cloud misconfiguration, third-party vendor breaches, insider data theft, phishing-enabled credential theft, AI model vulnerabilities, regulatory non-compliance, and financial reporting errors as key scenarios.

The 2025 HealthTech threat landscape is characterized by double-extortion ransomware against ePHI, AI-specific threats such as model poisoning and model inversion against diagnostic models, and supply-chain attacks via SaaS vendors with access to PHI and financial data. Controls like OPS-01 (immutable backups), IAM-02 (YubiKeys), DP-02 (endpoint DLP), RM-02 (AI risk management based on NIST AI RMF), VM-01 (vendor security lifecycle and BAAs), and OPS-02 (GitHub change management and branch protection) are mapped back to specific risk IDs in the matrix to show clear traceability from risk to control to evidence.

## 12-Month Implementation Roadmap

The implementation roadmap is structured into four phases designed to move AyuHealth from "startup mode" to "enterprise-ready" in 12 months while staying aligned with IPO and market-entry goals.

### Phase 1 – Critical Mitigation (Months 1–3)

Focus on high-impact technical risks: enable AWS Backup with Object Lock (OPS-01), deploy YubiKeys for admins and enforce FIDO2 MFA (IAM-02), roll out endpoint DLP (DP-02), and enforce AWS KMS encryption on all storage (DP-01), with a milestone of fully mitigating ransomware and cloud misconfiguration risks with scores >= 15.

### Phase 2 – Governance and Compliance (Months 4–7)

Establish governance foundations by auditing all SaaS vendors and executing BAAs for PHI handlers (VM-01), locking down GitHub main branches with mandatory peer review for SOX-relevant systems (OPS-02), executing the first quarterly access review (IAM-03), and approving the core policy stack (Information Security, AUP, Incident Response, Vendor Management), closing key HIPAA and SOX gaps.

### Phase 3 – Operationalisation and AI Maturity (Months 8–10)

Implement adversarial stress testing and monitoring for diagnostic AI models (RM-02), run the first Incident Response "Game Day" simulation (IM-01), deploy automated data inventory for privacy laws such as CCPA/DPDP (RM-01), and complete company-wide security awareness training (HR-01), elevating AI and privacy risk management capability.

### Phase 4 – Audit and Certification (Months 11–12)

Engage a third-party penetration test, perform a mock internal audit using the CCF mapping table, and host external auditors for SOC 2 Type I and ISO 27001 Stage 1 assessments, targeting issuance of a SOC 2 Type I report and ISO 27001 certification recommendation by the end of Month 12.

## Repository Structure

This repository is organized to support audit readiness and stakeholder communication:

- **/docs** – Comprehensive compliance documentation (final report, policies, methodology, threat landscape)
- **/common-controls-framework** – CCF mapping table, control-to-requirement mapping logic
- **/risk-assessment** – Risk matrix, risk register, gap analysis
- **/policies-and-controls** – IAM, data protection, vendor management, and SOX ITGC policy packs
- **/dashboards** – Executive, SOC Admin, and compliance dashboards (specs and wireframes)
- **/artifacts** – Evidence examples (AWS configs, Okta screenshots, GitHub branch protection) and audit templates
- **/meta** – Contributing guidelines, license, changelog

## File Descriptions

### The Risk Matrix
The Risk Matrix file quantifies AyuHealth's top threats using NIST SP 800-30-aligned likelihood and impact scoring, making it easy for executives to see which scenarios (e.g., ransomware, AI model attacks, SOX failures) demand immediate action. It translates technical vulnerabilities into a prioritized remediation backlog, directly supporting resource allocation, board reporting, and audit discussions around risk-based control design.

### The Mapping Table
The Mapping Table is the "Rosetta Stone" that aligns each CCF control (e.g., IAM-01, DP-01, OPS-01, RM-02) to ISO 27001 clauses, SOC 2 criteria, HIPAA safeguards, NIST CSF 2.0 functions, and SOX ITGC focus areas. This allows auditors and stakeholders to see exactly how "test once" controls provide multi-framework coverage, reducing duplicate work and clarifying certification readiness at a glance.

### The Executive Dashboard
The Executive Dashboard aggregates metrics like Compliance Readiness Score, Risk Heat Map, Vendor Risk Exposure, and Mean Time to Resolution into a single board-level view that frames cybersecurity as an enterprise risk and value driver rather than a cost center. By tying control status and risk trends to IPO readiness and hospital sales enablement, it gives leadership a recurring, data-driven mechanism to govern the compliance program.

## Key Deliverables

- ✅ Unified CCF mapping across 5 frameworks (ISO 27001, SOC 2, HIPAA, SOX, NIST CSF 2.0)
- ✅ NIST SP 800-30 risk assessment with 2025 HealthTech threat landscape
- ✅ 12-month phased implementation roadmap with resource and budget estimates
- ✅ IAM hardening controls (FIDO2/YubiKeys, Okta RBAC, quarterly access reviews)
- ✅ Data protection controls (AWS KMS, S3 Object Lock, endpoint DLP)
- ✅ AI risk management framework (adversarial testing, model monitoring)
- ✅ SOX ITGC controls for financial systems and change management
- ✅ Executive and operational compliance dashboards

## Use Cases

**For GRC Teams**: Navigate the repository to understand how each control is designed to satisfy multiple audit objectives simultaneously, and use the mapping table during audits to efficiently address compliance questions.

**For Engineering Leaders**: Reference the implementation roadmap and control specifications to prioritize security and compliance work in your sprints, and use the dashboard to track progress toward Phase milestones.

**For Board and Executives**: Use the Executive Dashboard and risk matrix to monitor HealthTech regulatory compliance, audit readiness, and business impact of security controls in the context of IPO and hospital market sales.

**For Cybersecurity Recruiters and Hiring Managers**: Review this repository as a demonstration of integrated GRC program design, HealthTech domain knowledge, cloud security architecture, and the ability to rationalize complexity into business-driven compliance solutions.

## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

## Contact

For questions or collaboration opportunities, please contact: [Your Name] | [Email] | [LinkedIn]

---

**Last Updated**: December 2025 | **Project Status**: Complete (Ready for Portfolio & Interviews)
