# Proposal: Hybrid Air-Gapped & Token-Based Development Environment

## Executive Summary
This proposal recommends adopting a **hybrid software development model** that combines a **secure air-gapped environment** for sensitive and proprietary software with a **connected development environment** for new, non-sensitive projects. This approach balances **security, productivity, consistency, and innovation**.

The model protects company intellectual property by ensuring sensitive source code and systems remain isolated from the internet, while still allowing teams to use modern external AI tools for rapid prototyping and experimentation where no confidential information is involved.

In addition to environment separation, this proposal defines a **default software development workflow** to ensure all teams follow the same standards for UI design, coding, testing, deployment, and governance.

**Key outcomes:**
- Protect sensitive code and business data
- Improve development speed and code quality
- Standardize UI and deployment practices across all software
- Enable safe adoption of AI-assisted development tools
- Increase delivery consistency for all users and teams

---

## 1. Objectives
The objectives of this proposal are to:
- Protect proprietary software and confidential business logic
- Establish a secure development model for existing internal systems
- Provide a controlled way to use external AI tools for new project development
- Define a standard workflow for software delivery across all teams
- Ensure UI consistency across deployed applications
- Ensure deployment consistency for all users and environments
- Improve governance, auditability, and engineering discipline

---

## 2. Scope
This proposal applies to:
- Internal software development teams
- Existing software products containing proprietary or sensitive code
- New software projects that do not contain confidential intellectual property at project start
- Development workflows for C#, Python, web, and service-based applications
- UI design, source control, testing, deployment, and release management practices

---

## 3. Proposed Development Model

### 3.1 Secure Air-Gapped Environment
**Purpose:** Support development, maintenance, debugging, and enhancement of sensitive or proprietary projects.

**Core components:**
- Local deployment of **Qwen 70B** or equivalent internal LLM for debugging, code explanation, and refactoring assistance
- **Visual Studio Code** and approved offline development extensions for C# and Python
- Self-hosted Git platform such as **GitLab** or **Gitea**
- Internal CI/CD infrastructure
- Internal package mirrors for **NuGet** and **PyPI**
- Secure local documentation and artifact repositories

**Indicative hardware requirements:**
- 4-8x NVIDIA A100/H100 GPUs (80 GB each)
- 1-2 TB RAM
- Dual EPYC/Xeon CPUs
- 20 TB NVMe SSD storage with RAID
- 10-40 Gbps internal networking

**Benefits:**
- Sensitive code never leaves the protected environment
- Reduced risk of intellectual property leakage
- Developers receive AI support without external exposure
- Controlled and auditable software changes
- Reliable offline development capability

### 3.2 Connected Environment for New Projects
**Purpose:** Support rapid development of new projects, prototypes, proofs of concept, and research initiatives that do not contain sensitive code.

**Core components:**
- Token-based access to approved external LLMs such as Claude, DeepSeek, or other enterprise-approved providers
- Internet-enabled developer workstations
- Separate repositories and CI/CD pipelines isolated from sensitive environments
- Standard cloud or internet-enabled package and documentation access

**Benefits:**
- Faster delivery for new initiatives
- Access to the latest AI-assisted development capabilities
- Lower up-front infrastructure cost for exploratory work
- Improved experimentation with modern frameworks, tools, and architectures

---

## 4. Security and Governance Model
To protect company information while maintaining operational efficiency, the following controls are required:

### 4.1 Network Segmentation
- Maintain a fully isolated **air-gapped subnet** for sensitive projects
- Maintain a separate **connected subnet** for new project work
- Prohibit direct synchronization between the two environments unless explicitly approved

### 4.2 Access Control
- Developers must authenticate separately for each environment
- Access should be role-based and approved according to project classification
- Administrative access should be limited and fully audited

### 4.3 Data Transfer Policy
- Movement of code, artifacts, or documents between environments must follow a formal approval process
- Only designated managers or security-authorized approvers may approve transfers
- All imports into the air-gapped environment must be reviewed and scanned before acceptance

### 4.4 Audit and Compliance
- Log external AI tool usage for approved connected-environment projects
- Track repository changes, releases, and deployment approvals
- Retain records for security review and operational audit

---

## 5. Default Workflow for Consistent Software Development
A default engineering workflow is required to ensure software is built, reviewed, tested, deployed, and maintained consistently across all teams.

### 5.1 Standard Delivery Workflow
All software projects should follow the workflow below:

1. **Requirement Definition**
   - Define business objective, scope, users, and acceptance criteria
   - Classify the work as **sensitive** or **non-sensitive**
   - Assign the project to the correct environment

2. **Solution Design**
   - Create architecture, UI design, and technical design documents
   - Reuse approved patterns, frameworks, and shared components
   - Review security and deployment implications early

3. **Planning and Task Breakdown**
   - Break work into features, user stories, or implementation tasks
   - Estimate effort and assign owners
   - Define test requirements and release targets

4. **Development**
   - Create a feature branch from the approved base branch
   - Develop using approved IDEs, libraries, and AI tools
   - Follow coding standards and shared engineering conventions

5. **Code Review**
   - Submit a pull request or merge request
   - Review for functionality, readability, maintainability, security, UI consistency, and test coverage
   - Require approval before merging

6. **Testing**
   - Execute unit, integration, regression, and where applicable UI tests
   - Validate against acceptance criteria
   - Record test evidence for release readiness

7. **Deployment**
   - Deploy only through the approved CI/CD pipeline
   - Promote through defined stages: Development, QA, Staging/UAT, Production
   - Record version, approver, and deployment outcome

8. **Monitoring and Maintenance**
   - Monitor usage, errors, performance, and feedback
   - Fix defects and deploy updates through the same controlled workflow

---

## 6. UI Consistency Standard
To ensure UI component consistency across all deployed software, the company should establish a **shared design system**.

### 6.1 Required UI Standards
All user-facing applications should use:
- Shared color palette and branding rules
- Standard typography and spacing scale
- Standard buttons, forms, dialogs, navigation, tables, and alerts
- Accessibility standards for keyboard use, contrast, labels, and focus behavior
- Responsive layout standards where applicable

### 6.2 Shared Component Strategy
- Maintain a **central UI component library** for all common controls
- Version the component library to support controlled upgrades
- Require teams to reuse approved components instead of building duplicate custom components
- Maintain UI documentation and examples in the internal repository

### 6.3 UI Review Requirements
During code review, teams must verify:
- Conformance to approved design guidelines
- Reuse of shared UI components
- Accessibility compliance
- Consistent user interaction patterns across applications

---

## 7. Deployment Consistency Standard
To ensure software is deployed consistently for all users, deployment must follow a common release model.

### 7.1 Standard Deployment Stages
Every project should use the same promotion path:
1. Development
2. Test / QA
3. Staging / UAT
4. Production

### 7.2 Deployment Rules
- All deployments must be automated through CI/CD where possible
- Manual production deployment should be exception-only and approved
- Release packages must be versioned
- Rollback procedures must exist for every production release
- Environment configuration must be standardized and documented
- Deployment logs must be retained for audit and troubleshooting

### 7.3 End-User Consistency
To ensure consistency for all users:
- Use the same approved release process for all applications
- Use standardized environment configuration templates
- Validate software in staging before production rollout
- Control phased release or full release according to business need

---

## 8. Default Tool Usage Workflow
The company should define a default way to use tools for software development so engineers work consistently and safely.

### 8.1 Approved Tool Usage for Sensitive Projects
**Environment:** Air-gapped
- IDE: Visual Studio Code / Visual Studio
- Source control: Self-hosted GitLab or Gitea
- AI assistant: Local Qwen 70B or approved internal model only
- Build agents: Internal build servers only
- Package sources: Internal NuGet / PyPI mirrors
- CI/CD: Internal pipeline only
- Documentation: Internal wiki / repository documentation only

**Rule:** No external AI, cloud repository, or internet-based code assistant may be used with sensitive code.

### 8.2 Approved Tool Usage for New Non-Sensitive Projects
**Environment:** Connected
- IDE: Visual Studio Code / Visual Studio / JetBrains tools
- Source control: Separate repositories not connected to air-gapped assets
- AI assistant: Approved external token-based LLMs
- Package sources: Approved public or enterprise-managed registries
- CI/CD: Connected pipeline isolated from sensitive systems
- Documentation: Public documentation and approved enterprise knowledge sources

**Rule:** External AI tools may only be used where no confidential company code or restricted data is involved.

### 8.3 Recommended Day-to-Day Developer Workflow
1. Confirm project classification before starting work
2. Select the correct development environment
3. Pull latest code from the approved repository
4. Create a feature branch using the standard branch naming convention
5. Implement changes using approved tools only
6. Run local tests before review
7. Open merge/pull request and complete peer review
8. Merge only after approval and successful pipeline checks
9. Deploy through the standard release pipeline
10. Update documentation and release notes

---

## 9. Recommended Branching and Release Model
To support consistency, the following baseline model is recommended:

### 9.1 Branching Strategy
- `main` or `master`: production-ready code
- `develop` (optional): integration branch for active development
- `feature/<name>`: feature development
- `bugfix/<name>`: defect fixes
- `hotfix/<name>`: urgent production fixes

### 9.2 Merge Rules
- No direct commit to production branch except under approved emergency procedure
- All merges require code review
- CI checks must pass before merge
- Release tags should be created for production versions

---

## 10. Roles and Responsibilities
### Engineering Team
- Build software according to standards and approved workflow
- Reuse shared components and follow coding conventions
- Write and maintain tests

### Technical Leads / Architects
- Review architecture and design decisions
- Enforce standards for maintainability and reuse
- Approve exceptions to normal design patterns where justified

### DevOps / Platform Team
- Maintain CI/CD pipelines and deployment standards
- Provide infrastructure templates and automation support
- Maintain package mirrors and internal tooling where required

### Security / Governance Team
- Define classification and usage policies
- Review environment separation and data transfer controls
- Audit external AI usage and compliance records

### Management
- Approve the operating model
- Fund required infrastructure and training
- Enforce policy adoption across teams

---

## 11. Risks and Mitigations
| Risk | Impact | Mitigation |
|------|--------|------------|
| Developers use the wrong environment | Data leakage or policy breach | Mandatory project classification and access control |
| UI inconsistency across applications | Poor user experience and increased maintenance | Shared design system and mandatory component reuse |
| Inconsistent deployment processes | Release failures and user confusion | Standard CI/CD pipeline and release gates |
| Overdependence on external AI tools | Compliance and IP exposure risk | Restrict external AI to approved non-sensitive projects |
| High cost of air-gapped infrastructure | Budget pressure | Limit secure infrastructure use to sensitive workloads |

---

## 12. Implementation Plan
### Phase 1: Governance and Standards
- Approve policy for environment usage
- Define project classification rules
- Publish coding, UI, and deployment standards

### Phase 2: Tooling and Infrastructure
- Deploy or confirm air-gapped compute and internal repositories
- Configure internal package mirrors and CI/CD pipelines
- Establish connected environment controls for external AI usage

### Phase 3: Shared Engineering Assets
- Create shared UI component library
- Create templates for repositories, pipelines, and environments
- Publish workflow documentation and development checklists

### Phase 4: Training and Adoption
- Train developers on environment selection and tool usage
- Train reviewers on UI, security, and deployment consistency checks
- Monitor adoption and collect improvement feedback

---

## 13. Recommendation
Adopt this hybrid model as the company standard for software development.

**Recommended decisions:**
- Approve the air-gapped environment for sensitive software
- Approve controlled use of external AI tools for new non-sensitive projects
- Standardize the software development lifecycle across all teams
- Enforce shared UI, testing, and deployment standards
- Implement governance for environment separation and data transfer

This model provides a practical balance between **security and innovation** while improving **engineering consistency, software quality, and delivery reliability**.
