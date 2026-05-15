# CLAUDE.md

## Purpose
This file defines the default engineering, security, UI, deployment, and AI usage rules for software development projects. Claude should follow these instructions when assisting with planning, coding, reviewing, documentation, and workflow recommendations.

---

## 1. Environment Classification Rules
Before giving development guidance or generating code, classify the project into one of two environments:

### 1.1 Air-Gapped Environment
Use the **air-gapped environment** for:
- Existing internal software
- Proprietary company code
- Sensitive systems
- Confidential business logic
- Projects containing restricted data or internal integrations

### 1.2 Connected Environment
Use the **connected environment** for:
- New projects with no existing sensitive code
- Prototypes
- Proofs of concept
- Research and experimentation
- Non-confidential greenfield development

### 1.3 Mandatory Rule
If a project contains proprietary or sensitive code, Claude must treat it as **air-gapped** and must not recommend external AI or internet-dependent tooling for source code assistance.

---

## 2. AI Tool Usage Rules

### 2.1 Air-Gapped Projects
For air-gapped projects, only recommend:
- Local LLMs such as Qwen 70B or approved internal models
- Offline IDE extensions
- Self-hosted repositories
- Internal package mirrors
- Internal CI/CD pipelines

Claude must **not** recommend:
- External LLMs
- Cloud code assistants
- Uploading source code to external services
- Internet-based dependency or documentation workflows unless explicitly approved for non-code reference material

### 2.2 Connected Projects
For connected projects, Claude may recommend:
- Approved external LLMs
- Internet-enabled IDE tooling
- Public documentation
- Standard online package registries
- Connected CI/CD pipelines

Claude must still avoid exposing confidential company data, credentials, secrets, internal architecture, or restricted assets.

---

## 3. Default Software Development Workflow
Claude should recommend the following default workflow unless the user explicitly provides a different approved process.

### 3.1 Standard Workflow
1. **Requirement Definition**
   - Define business objective, scope, users, and acceptance criteria
   - Classify the project as air-gapped or connected

2. **Solution Design**
   - Prepare architecture and UI design
   - Reuse approved standards and shared components

3. **Planning**
   - Break work into tasks, stories, or milestones
   - Define test and deployment expectations

4. **Development**
   - Create a feature branch
   - Use approved tools only
   - Follow coding standards and shared patterns

5. **Code Review**
   - Require pull request or merge request review
   - Validate maintainability, security, consistency, and test coverage

6. **Testing**
   - Run unit, integration, regression, and UI tests where applicable

7. **Deployment**
   - Deploy only through approved CI/CD workflows
   - Promote through standard environments

8. **Maintenance**
   - Monitor, fix issues, and update documentation through the same controlled process

---

## 4. UI Consistency Rules
Claude should encourage all teams to maintain a **shared design system**.

### 4.1 UI Standards
All user-facing applications should follow:
- Shared branding, colors, typography, and spacing
- Standardized buttons, forms, dialogs, tables, navigation, and alerts
- Accessibility requirements
- Consistent interaction patterns

### 4.2 UI Component Reuse
Claude should prefer:
- Shared UI component libraries
- Reusable layouts and templates
- Centralized UI documentation
- Versioned shared components

Claude should discourage one-off UI implementations when an approved reusable component exists.

---

## 5. Deployment Consistency Rules
Claude should always recommend a standardized deployment model.

### 5.1 Standard Deployment Stages
Use the following stages whenever possible:
1. Development
2. Test / QA
3. Staging / UAT
4. Production

### 5.2 Deployment Standards
Claude should recommend:
- Automated CI/CD pipelines
- Versioned releases
- Rollback procedures
- Standardized configuration management
- Deployment logs and audit trails
- Staging validation before production rollout

Claude should avoid recommending manual, inconsistent, or environment-specific release steps unless explicitly required.

---

## 6. Tooling Rules

### 6.1 Approved Tools for Air-Gapped Projects
- IDE: Visual Studio Code / Visual Studio with offline-approved tooling
- Source Control: Self-hosted GitLab or Gitea
- AI Assistant: Local Qwen 70B or approved internal model only
- Build Tools: Internal build agents only
- Package Sources: Internal NuGet / PyPI mirrors
- CI/CD: Internal deployment pipelines
- Documentation: Internal repositories or internal wiki

### 6.2 Approved Tools for Connected Projects
- IDE: Visual Studio Code / Visual Studio / JetBrains tools
- Source Control: Separate repositories not linked to sensitive assets
- AI Assistant: Approved external LLMs
- Build Tools: Internet-enabled or cloud-enabled pipelines
- Package Sources: Approved public or enterprise registries
- Documentation: Public docs and approved internal references

---

## 7. Branching and Release Rules
Claude should recommend the following branching model unless another approved workflow is specified.

### 7.1 Branching Strategy
- `main` or `master`: production-ready code
- `develop`: optional integration branch
- `feature/<name>`: new feature work
- `bugfix/<name>`: bug fixes
- `hotfix/<name>`: urgent production fixes

### 7.2 Merge Standards
- No direct commits to production branches except emergency-approved fixes
- Pull request review is required
- CI checks must pass before merge
- Production versions should be tagged

---

## 8. Review and Approval Rules
Claude should recommend that all changes be reviewed for:
- Functional correctness
- Security compliance
- UI consistency
- Reuse of shared components
- Test coverage
- Deployment readiness
- Documentation completeness

Sensitive changes should require stricter approval and audit handling.

---

## 9. Security and Data Transfer Rules
Claude must reinforce the following rules:
- Sensitive code must not leave the air-gapped environment
- External AI tools must not be used for confidential or proprietary code
- Transfers between connected and air-gapped environments require formal approval
- Secrets, credentials, tokens, and private configuration must never be shared with external tools
- All exceptions should be logged and approved

---

## 10. Documentation Rules
Claude should encourage teams to maintain:
- Architecture documentation
- UI standards documentation
- API or service documentation
- Deployment runbooks
- Release notes
- Security and environment classification guidance

Whenever proposing new processes, Claude should align them to this document unless the user explicitly requests a different approved standard.

---

## 11. Default Behavior for Claude
When assisting with software development, Claude should:
1. First determine whether the project is **air-gapped** or **connected**
2. Recommend only tools and workflows permitted for that environment
3. Prefer reuse over custom implementation
4. Prefer standardized deployment over ad hoc release steps
5. Prefer UI consistency over isolated local design choices
6. Avoid suggestions that risk data leakage or policy violations
7. Encourage documentation, review, testing, and traceability

If the environment is not specified, Claude should ask whether the project contains sensitive or proprietary code before recommending external AI usage.
