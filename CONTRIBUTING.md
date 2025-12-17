# Contributing to AyuHealth Unified Compliance Framework

## Overview

This repository is a **portfolio project** demonstrating GRC (Governance, Risk, and Compliance) program design for a HealthTech startup. Contributions are welcome from cybersecurity professionals, GRC practitioners, and audit professionals who wish to enhance the framework.

## How to Contribute

### 1. For Enhancements to Documentation

- Fork the repository
- Create a feature branch: `git checkout -b enhance/your-feature-name`
- Edit the relevant markdown files in `/docs`, `/policies-and-controls`, or `/risk-assessment`
- Ensure changes align with the CCF mapping table and don't introduce contradictions with the framework
- Submit a pull request with a clear description of your enhancement

### 2. For Control Design Improvements

- If you identify gaps in the Common Controls Framework (CCF), open an Issue first with:
  - Control ID and domain (IAM, DP, OPS, RM, VM, HR, IM)
  - Specific requirement(s) from ISO 27001, SOC 2, HIPAA, SOX, or NIST CSF 2.0 not covered
  - Proposed control design
- Community feedback and CISO review required before implementation

### 3. For Risk Assessment Updates

- If you identify new threats relevant to HealthTech (2025 threat landscape):
  - Update `/risk-assessment/risk-register-ayuhealth.md` with:
    - Risk ID (follow existing numbering R-01 through R-08+)
    - Risk scenario and business impact
    - Likelihood and impact scores (using NIST SP 800-30 scale)
    - Proposed mitigation control ID
- Validate mapping to relevant CCF controls

### 4. For Compliance Mapping

- If you identify additional requirement-to-control mappings:
  - Update `/common-controls-framework/ccf-mapping-table.md`
  - Ensure alignment with Adobe CCF methodology
  - Include clause/requirement reference for all 5 frameworks (ISO 27001, SOC 2, HIPAA, SOX, NIST CSF 2.0)
  - Test for duplicate requirements or conflicting mappings

## Code of Conduct

- **Respect Confidentiality**: This is an academic/portfolio project simulating a real startup. Treat all data as proprietary.
- **Professional Tone**: Maintain technical rigor and professional communication in all pull requests and issues.
- **Framework Integrity**: Do not modify core CCF methodology without consensus from maintainers and GRC professionals.

## Review Process

1. Pull requests will be reviewed by maintainers for:
   - Alignment with "Test Once, Comply Many" philosophy
   - Accuracy of compliance mapping
   - Clarity and professionalism of documentation
   - No contradictions with existing controls

2. Standard review timeline: 5-7 business days

3. If changes require policy updates or control redesign, additional review may be needed

## Standards & Guidelines

### Markdown Style
- Use GitHub-flavored markdown
- Include clear headings (##, ###, ####)
- Link to related controls using [[Control ID]] format
- Include tables for mapping data

### Control Documentation
- **Control ID**: Domain-NN (e.g., IAM-01, DP-02, OPS-01)
- **Title**: Concise, action-oriented (e.g., "Provisioning with Least Privilege")
- **Description**: 2-3 sentences on control purpose
- **Implementation**: Specific technical steps (AWS, Okta, GitHub, tools)
- **Evidence**: What auditors should see
- **Mapping**: ISO Annex A, SOC 2 criteria, HIPAA Rule, NIST CSF, SOX ITGC

### Risk Documentation
- **Risk ID**: Consistent numbering (R-01, R-02, etc.)
- **Scenario**: 1-2 sentence business impact statement
- **Scoring**: Likelihood (1-5) × Impact (1-5) = Risk Score
- **Mitigation**: Link to specific CCF control(s)

## Framework Constraints

Do NOT change the following without justification:
- The 12-month phased roadmap structure (4 phases)
- The core CCF control domains (IAM, DP, OPS, RM, VM, HR, IM)
- The 315-control target (rationalization from 4,300 requirements)
- The "Test Once, Comply Many" philosophy

## Contact & Maintainers

- **Primary Maintainer**: Pranav Walgude (pranav.walgude@northeastern.edu)
- **Co-Author**: Rushikesh Muley
- **Course**: INFO 7374 - Cybersecurity and Compliance (Northeastern University)

## Questions?

Open an Issue with the label `question` and maintainers will respond within 5 business days.

---

**Project Status**: Academic Portfolio Project | **Last Updated**: December 2025 | **License**: MIT
