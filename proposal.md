# Proposal: Hybrid Air‑Gapped & Token‑Based Development Environment

## Executive Summary
We propose a **dual‑environment software development setup** that balances **security for sensitive projects** with **flexibility for new initiatives**.  
- **Air‑gapped environment**: Protects company intellectual property and prevents data leakage.  
- **Token‑based external LLMs**: Enables rapid prototyping and innovation for new projects where no sensitive code exists.  

This approach ensures our developers can **debug faster, add features confidently, and deliver new projects quickly** without compromising company information.

---

## 1. Secure Air‑Gapped Environment
**Purpose**: Handle all existing projects and proprietary code.  

**Components**:
- Local deployment of **Qwen 70B** LLM for debugging and refactoring.  
- **Visual Studio Code** with offline extensions for C# and Python.  
- Self‑hosted Git server (GitLab/Gitea) with CI/CD pipeline.  
- Internal mirrors for NuGet and PyPI to ensure package availability offline.  

**Hardware**:
- 4–8× NVIDIA A100/H100 GPUs (80GB each).  
- 1–2 TB RAM, dual EPYC/Xeon CPUs.  
- 20 TB NVMe SSD storage with RAID redundancy.  
- 10–40 Gbps internal networking.  

**Benefits**:
- No external connectivity → zero risk of code leakage.  
- Developers improve debugging skills by working directly with local AI assistance.  
- Controlled updates via secure staging server.  

---

## 2. Connected Environment for New Projects
**Purpose**: Rapid development of projects with no prior sensitive code.  

**Components**:
- Token‑based access to external LLMs (DeepSeek, Claude, etc.).  
- Standard developer workstations with internet access.  
- Separate Git repositories and CI/CD pipelines, isolated from air‑gapped systems.  

**Benefits**:
- Quick turnaround for projects we’ve never coded before.  
- Access to cutting‑edge AI models without risking proprietary data.  
- Developers gain exposure to modern AI‑assisted coding practices.  

---

## 3. Security & Governance
- **Network Segmentation**:  
  - Air‑gapped subnet for sensitive projects.  
  - Internet‑enabled subnet for new projects.  
- **Access Control**:  
  - Developers authenticate separately depending on environment.  
- **Audit Logging**:  
  - Track usage of external LLMs to ensure compliance.  
- **Data Transfer Policy**:  
  - Strict controls on moving code between environments.  
  - Only approved managers can authorize migration.  

---

## 4. Developer Productivity Gains
- **Debugging**: Local Qwen 70B helps developers quickly identify and fix issues.  
- **Feature Development**: AI assistance accelerates adding new features to existing projects.  
- **Skill Growth**: Developers gain hands‑on experience with both air‑gapped AI and external token‑based AI.  
- **Innovation**: External LLMs allow experimentation with new languages, frameworks, and architectures.  

---

## 5. Business Impact
- **Risk Mitigation**: Sensitive code never leaves the air‑gapped environment.  
- **Faster Delivery**: New projects can be prototyped and delivered quickly using external AI.  
- **Cost Efficiency**: Hardware investment is focused only on secure workloads; external AI is pay‑per‑use.  
- **Competitive Advantage**: Balances security with agility, enabling us to innovate without exposing IP.  

---

## 6. Default Workflow for Consistent Software Development
To ensure consistency across all software projects, the company should adopt a **standard development workflow** that applies to both air‑gapped and connected environments.

### 6.1 UI Component Consistency
- Establish a **shared design system** with reusable UI components, styles, icons, and layouts.  
- Maintain a **central UI component library** for all deployed applications.  
- Define standards for:  
  - Colors, typography, spacing, and branding  
  - Buttons, forms, tables, dialogs, and navigation  
  - Accessibility requirements  
- Require all teams to build new interfaces using approved shared components rather than creating custom UI elements from scratch.  
- Review UI changes during pull request reviews to ensure visual and functional consistency.

**Recommended tools/process**:
- Use a shared frontend framework and component library.  
- Maintain UI guidelines documentation in the internal Git repository.  
- Version the component library so all applications can adopt controlled updates.

### 6.2 Deployment Consistency
- Standardize the deployment pipeline so all software is built, tested, approved, and released in the same way.  
- Use the same deployment stages for all projects:  
  1. Development  
  2. Testing / QA  
  3. Staging / UAT  
  4. Production  
- Use infrastructure templates and deployment scripts to avoid manual differences between systems.  
- Keep environment variables, configuration management, and release approvals standardized.  
- Ensure all users receive software through the same approved deployment mechanism.

**Recommended tools/process**:
- CI/CD pipelines in GitLab, Gitea, or Jenkins.  
- Standard build scripts for C# and Python applications.  
- Containerization where possible to ensure identical runtime environments.  
- Release versioning and rollback procedures for every deployment.

### 6.3 Default Software Development Workflow
The following workflow is recommended as the company default:

1. **Requirement Definition**  
   - Define business requirement, scope, and security classification.  
   - Decide whether the work belongs in the **air‑gapped** or **connected** environment.  

2. **Design Phase**  
   - Prepare architecture, UI design, and technical approach.  
   - Reuse approved design patterns, coding standards, and UI components.  

3. **Development Phase**  
   - Create a feature branch in Git.  
   - Use AI tools only within the approved environment:  
     - **Air‑gapped projects** → local Qwen 70B only  
     - **New non-sensitive projects** → approved external LLMs  
   - Developers write code following coding conventions and shared libraries.  

4. **Code Review Phase**  
   - Submit merge/pull request.  
   - Validate:  
     - Code quality  
     - Security compliance  
     - UI consistency  
     - Reuse of shared components  
     - Test coverage  

5. **Testing Phase**  
   - Run automated tests (unit, integration, regression).  
   - Perform UI validation and user acceptance testing where needed.  

6. **Deployment Phase**  
   - Deploy through the standard CI/CD pipeline only.  
   - Release to staging before production.  
   - Record deployment logs and version history.  

7. **Maintenance Phase**  
   - Monitor issues, performance, and user feedback.  
   - Apply fixes through the same controlled workflow.  

### 6.4 Suggested Tool Usage Workflow
To guide developers, the company should define a default tool usage model:

**For Air‑Gapped Sensitive Projects**:
- IDE: Visual Studio Code / Visual Studio  
- Source Control: Self-hosted GitLab or Gitea  
- AI Assistant: Local Qwen 70B only  
- Build Tools: Internal build agents  
- Package Sources: Internal NuGet / PyPI mirrors  
- Deployment: Internal CI/CD only  

**For Connected New Projects**:
- IDE: Visual Studio Code / JetBrains / Visual Studio  
- Source Control: Separate Git repositories  
- AI Assistant: Approved token-based LLMs  
- Build Tools: Cloud or internet-enabled CI/CD pipeline  
- Deployment: Segregated staging and production environments  

### 6.5 Governance Rules for Workflow Consistency
- Every project must follow the same branching strategy.  
- Every project must use the same definition of done.  
- Every UI must use approved shared components.  
- Every deployment must pass testing and approval gates.  
- Every use of external AI tools must be logged and restricted to approved project types.  
- No code may move from connected systems into the air‑gapped environment without approval and review.

---

## Architecture Diagram

```text
                        ┌───────────────────────────────┐
                        │        Developer PCs          │
                        │  - VS Code (C#/Python)        │
                        │  - Local debugging            │
                        │  - Git client                 │
                        └───────────────┬───────────────┘
                                        │
                                        │ Internal LAN
                                        │
        ┌───────────────────────────────┴───────────────────────────────┐
        │                        Air-Gapped Subnet                      │
        │                                                               │
        │   ┌───────────────────────────────┐   ┌────────────────────┐  │
        │   │   Secure Compute Server       │   │   Git/CI/CD Server │  │
        │   │ - Qwen 70B LLM (local)        │   │ - GitLab/Gitea     │  │
        │   │ - 4–8× A100/H100 GPUs         │   │ - Jenkins CI/CD    │  │
        │   │ - 1–2 TB RAM                  │   │ - Package mirrors  │  │
        │   │ - 20 TB NVMe storage          │   │ - Internal repos   │  │
        │   └───────────────────────────────┘   └────────────────────┘  │
        │                                                               │
        │   Purpose: Debugging, refactoring, sensitive projects          │
        └───────────────────────────────────────────────────────────────┘

                                        │
                                        │ Controlled Access Boundary
                                        │
        ┌───────────────────────────────┴───────────────────────────────┐
        │                      Connected Subnet                         │
        │                                                               │
        │   ┌───────────────────────────────┐                           │
        │   │   Developer Workstations      │                           │
        │   │ - Internet enabled            │                           │
        │   │ - Token-based LLM access      │                           │
        │   │   (DeepSeek, Claude, etc.)    │                           │
        │   └───────────────────────────────┘                           │
        │                                                               │
        │   Purpose: Rapid prototyping, new projects, experimentation   │
        └───────────────────────────────────────────────────────────────┘
```

---

## Recommendation
Adopt this **hybrid model** immediately:  
- Deploy the air‑gapped server cluster for existing projects.  
- Enable token‑based external LLMs for new projects.  
- Standardize the software development workflow across all teams.  
- Train developers on environment separation, UI standards, deployment consistency, and security protocols.  

This solution ensures **no leakage of company information**, **improves developer skill sets**, and **accelerates delivery of new projects** while maintaining **consistent UI, deployment, and engineering practices**.
