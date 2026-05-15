# CLAUDE.md

## Purpose
This file defines the mandatory operating rules Claude must follow when assisting with software development in this repository. These rules are intended to enforce **security, consistency, reuse, deployment discipline, and safe AI usage**.

Claude should treat this file as the default instruction set for planning, coding, reviewing, documenting, and recommending workflows.

---

## Always Do
Claude must always:
- Classify work as **air-gapped** or **connected** before recommending tools or workflows
- Prefer **security, reuse, consistency, and maintainability** over convenience
- Recommend the **standard development workflow** unless a different approved workflow is explicitly provided
- Prefer **shared UI components**, **shared standards**, and **approved deployment pipelines**
- Require **code review**, **testing**, and **documentation updates** for meaningful changes
- Protect confidential code, architecture, credentials, tokens, and internal data
- Encourage traceability through branches, pull requests, CI/CD logs, release notes, and approval history

---

## Never Do
Claude must never:
- Recommend external AI tools for **proprietary, restricted, or sensitive code**
- Suggest copying confidential code into internet-based tools
- Suggest bypassing code review, testing, approval, or deployment controls
- Prefer one-off custom UI components when an approved shared component exists
- Recommend manual production changes unless explicitly required under an approved emergency process
- Expose secrets, credentials, tokens, internal URLs, private infrastructure details, or restricted architecture information
- Assume connected-environment tooling is allowed for sensitive projects

---

## 1. Environment Decision Rules
Claude must determine the project type before giving implementation guidance.

### 1.1 Use Air-Gapped Rules When
Treat the project as **air-gapped** if it involves any of the following:
- Existing company software
- Proprietary source code
- Sensitive business logic
- Internal integrations
- Restricted customer or operational data
- Confidential infrastructure or system details

### 1.2 Use Connected Rules When
Treat the project as **connected** only when all of the following are true:
- It is a new or greenfield project
- It does not contain proprietary code
- It does not include restricted business logic or secrets
- It is approved for external tooling usage

### 1.3 Default Rule
If the environment is unclear, Claude must assume the work may be sensitive and ask for clarification before recommending external AI or internet-dependent tooling.

---

## 2. AI Usage Rules

### 2.1 Air-Gapped Projects
For air-gapped work, Claude may recommend only:
- Local LLMs such as Qwen 70B or approved internal models
- Offline or internally hosted IDE tooling
- Self-hosted source control
- Internal package mirrors
- Internal CI/CD and documentation systems

Claude must not recommend:
- External LLMs
- Cloud code assistants
- Uploading source code to external websites or APIs
- Internet-based source analysis tools for confidential code

### 2.2 Connected Projects
For connected work, Claude may recommend:
- Approved external LLMs
- Public documentation
- Internet-enabled IDE tooling
- Approved public or enterprise package registries
- Connected CI/CD platforms isolated from sensitive environments

Claude must still avoid revealing confidential business information, secrets, credentials, or restricted internal details.

---

## 3. Standard Software Development Workflow
Claude should recommend this workflow by default.

1. **Requirement Definition**
   - Define objective, users, scope, constraints, and acceptance criteria
   - Classify the project as air-gapped or connected

2. **Solution Design**
   - Define architecture, data flow, UI approach, and dependencies
   - Reuse approved patterns and components

3. **Planning**
   - Break work into tasks, milestones, or user stories
   - Define testing and release expectations

4. **Development**
   - Create a feature branch
   - Use approved tools only
   - Follow coding standards and repository conventions

5. **Code Review**
   - Open a pull request or merge request
   - Validate security, maintainability, test coverage, and consistency

6. **Testing**
   - Run unit, integration, regression, and UI tests as appropriate
   - Verify acceptance criteria are met

7. **Deployment**
   - Deploy only through approved CI/CD workflows
   - Promote through the required release stages

8. **Maintenance**
   - Monitor, document, fix, and improve through the same controlled process

---

## 4. UI Consistency Rules
Claude must prioritize UI consistency across all deployed software.

### 4.1 Required UI Standards
All user-facing systems should use:
- Shared branding, colors, typography, and spacing
- Standardized controls, forms, dialogs, tables, navigation, and alerts
- Consistent interaction patterns
- Accessibility requirements for keyboard navigation, labels, focus behavior, and contrast

### 4.2 Shared Component Rule
Claude should prefer:
- Shared UI component libraries
- Reusable layouts and templates
- Centralized UI documentation
- Versioned shared components

Claude should discourage:
- Duplicated custom components
- Visual inconsistency across products
- Unreviewed deviations from the design system

---

## 5. Deployment Consistency Rules
Claude must recommend a uniform deployment approach for all software.

### 5.1 Standard Release Stages
Preferred release flow:
1. Development
2. Test / QA
3. Staging / UAT
4. Production

### 5.2 Deployment Standards
Claude should recommend:
- Automated CI/CD pipelines
- Versioned builds and releases
- Standard configuration management
- Rollback procedures
- Deployment approval gates where required
- Deployment logs for audit and troubleshooting

Claude should avoid recommending:
- Ad hoc deployments
- Environment-specific undocumented manual fixes
- Inconsistent rollout methods across products

---

## 6. Tooling Rules

### 6.1 Approved Tools for Air-Gapped Projects
- IDE: Visual Studio Code / Visual Studio with offline-approved extensions
- Source Control: Self-hosted GitLab or Gitea
- AI Assistant: Local Qwen 70B or approved internal model only
- Build Tools: Internal build agents only
- Package Sources: Internal NuGet / PyPI mirrors
- CI/CD: Internal pipelines only
- Documentation: Internal wiki, repository docs, and internal knowledge base

### 6.2 Approved Tools for Connected Projects
- IDE: Visual Studio Code / Visual Studio / JetBrains tools
- Source Control: Separate repositories isolated from sensitive assets
- AI Assistant: Approved external LLMs
- Build Tools: Connected build pipelines
- Package Sources: Approved public or enterprise registries
- Documentation: Public docs plus approved internal guidance

---

## 7. Branching and Release Rules
Claude should recommend the following unless a different approved model exists.

### 7.1 Branching Strategy
- `main` or `master`: production-ready branch
- `develop`: optional shared integration branch
- `feature/<name>`: new feature work
- `bugfix/<name>`: bug fixes
- `hotfix/<name>`: urgent production fixes

### 7.2 Merge Rules
- No direct commits to the production branch except through approved emergency handling
- Pull request review is required
- CI checks must pass before merge
- Production releases should be tagged

---

## 8. Review Rules
Claude should require review for:
- Functional correctness
- Security compliance
- UI consistency
- Reuse of shared components
- Test coverage
- Deployment readiness
- Documentation completeness

Sensitive or high-impact changes should require stronger approval and audit handling.

---

## 9. Security and Data Handling Rules
Claude must reinforce these rules at all times:
- Sensitive code must remain in the air-gapped environment
- External AI must not be used for confidential or proprietary code
- Secrets, credentials, tokens, and private configurations must never be exposed to external tools
- Transfers between connected and air-gapped environments require formal approval
- Exceptions must be logged, reviewed, and approved

---

## 10. Documentation Rules
Claude should encourage maintaining:
- Architecture documents
- UI standards and component usage guidance
- API or service documentation
- Deployment runbooks
- Release notes
- Security and environment classification guidance

Whenever Claude suggests a process, it should align with this file unless the user explicitly requests a different approved standard.

---

## 11. Default Response Behavior
When assisting with development tasks, Claude should:
1. Determine whether the project is **air-gapped** or **connected**
2. Recommend only tools allowed for that environment
3. Prefer reuse over reinvention
4. Prefer standard deployment over ad hoc release steps
5. Prefer shared UI patterns over isolated local design choices
6. Avoid suggestions that create compliance, security, or data leakage risk
7. Encourage review, testing, documentation, and traceability

If the environment is not specified, Claude should ask whether the work includes sensitive or proprietary code before recommending external AI usage.
