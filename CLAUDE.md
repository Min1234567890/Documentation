# CLAUDE.md

## Purpose
This file defines the mandatory operating rules Claude must follow when assisting with software development in this repository. These rules enforce **security, consistency, reuse, deployment discipline, and environment-aware tool selection**.

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
- When changing code, go through the entire relevant project to understand what the change will affect
- Try to localize changes to as few files as reasonably possible
- Avoid unnecessary changes beyond what is required for the fix or requested improvement

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
- Make broad or sweeping code changes when a localized fix is sufficient
- Introduce refactors unrelated to the requested fix unless they are necessary for correctness, safety, or maintainability of the change

---

## 1. Environment Decision Rules
Claude must determine the project type before giving implementation guidance.

### 1.1 Decision Table
| Question | Yes | No |
|----------|-----|----|
| Does the work involve existing company software? | Air-gapped | Continue evaluation |
| Does the work include proprietary source code? | Air-gapped | Continue evaluation |
| Does the work include sensitive business logic, credentials, or restricted integrations? | Air-gapped | Continue evaluation |
| Is the project greenfield with no confidential assets? | Continue evaluation | Air-gapped |
| Is the project approved for external tooling usage? | Connected | Air-gapped |

### 1.2 Air-Gapped Rules Apply When
Treat the project as **air-gapped** if it involves any of the following:
- Existing company software
- Proprietary source code
- Sensitive business logic
- Internal integrations
- Restricted customer or operational data
- Confidential infrastructure or system details

### 1.3 Connected Rules Apply When
Treat the project as **connected** only when all of the following are true:
- It is a new or greenfield project
- It does not contain proprietary code
- It does not include restricted business logic or secrets
- It is approved for external tooling usage

### 1.4 Default Rule
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
   - Follow the repository UI guidance in `ui-standards.md` when defining backgrounds, splash screens, buttons, and related UI patterns

3. **Planning**
   - Break work into tasks, milestones, or user stories
   - Define testing and release expectations

4. **Development**
   - Create a feature branch
   - Use approved tools only
   - Follow coding standards and repository conventions
   - Review the relevant project area to understand the impact of the change before modifying code
   - Keep the implementation as localized as possible
   - Do not make unrelated cleanup or refactoring changes unless required

5. **Code Review**
   - Open a pull request or merge request
   - Validate security, maintainability, test coverage, and consistency
   - Confirm the change scope is appropriate and does not include unnecessary modifications
   - Verify UI changes conform to `ui-standards.md`

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
- The shared guidance documented in `ui-standards.md`

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
- Change scope remains localized and does not include unnecessary modifications

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

## 11. Allowed vs Not Allowed Examples

### 11.1 Air-Gapped Examples
**Allowed:**
- Explaining internal code using a local model
- Recommending self-hosted Git and offline package mirrors
- Suggesting internal CI/CD for deployment
- Refactoring code entirely within the secure environment

**Not Allowed:**
- Pasting proprietary code into Claude, ChatGPT, or public AI tools
- Using cloud-based code assistants on restricted repositories
- Sending internal configs or secrets to external debugging tools
- Recommending public code hosting for sensitive projects

### 11.2 Connected Examples
**Allowed:**
- Using approved external LLMs for greenfield prototypes
- Referring to public framework documentation
- Using online package registries for non-sensitive projects
- Recommending modern internet-enabled development tools

**Not Allowed:**
- Mixing confidential internal code with connected-environment prompts
- Reusing restricted internal code in public or external tooling
- Moving project artifacts into the air-gapped environment without approval
- Exposing internal credentials in prompts or documentation

### 11.3 Change Scope Examples
**Allowed:**
- Fixing the bug in the few files directly involved
- Reading related project files first to understand impact
- Making a small supporting change that is necessary for the fix
- Leaving unrelated legacy code untouched when it does not block the change

**Not Allowed:**
- Refactoring unrelated modules during a bug fix
- Renaming, reformatting, or reorganizing unrelated files without need
- Expanding a small fix into a broad architecture rewrite without approval
- Making speculative cleanup changes that are not required for correctness

### 11.4 UI and Deployment Examples
**Allowed:**
- Reusing approved shared components
- Recommending staged releases through QA and UAT
- Enforcing UI review for consistency
- Using versioned pipelines and rollback plans
- Applying the standards defined in `ui-standards.md`

**Not Allowed:**
- Creating duplicate UI widgets without a valid reason
- Skipping staging validation before production
- Suggesting direct production edits for routine work
- Recommending inconsistent release processes across products
- Ignoring `ui-standards.md` when defining or reviewing UI decisions covered by that document

---

## 12. Exception Approval Workflow
If a requested action appears to violate these rules, Claude should not approve it by default.

### 12.1 Required Exception Process
Claude should instead recommend the following workflow:
1. Identify the policy conflict clearly
2. Explain the security, compliance, or consistency risk
3. Request confirmation that an approved exception process exists
4. Require review by the appropriate authority, such as:
   - Engineering lead
   - Security or governance lead
   - DevOps or platform owner
   - Business or system owner
5. Require logging of the exception decision
6. Require documenting scope, duration, and rollback or recovery steps

### 12.2 Examples of Exception Scenarios
- Moving code or artifacts between connected and air-gapped environments
- Allowing manual production intervention outside normal release process
- Using non-standard UI components in a product with shared design rules
- Using an external AI tool near borderline-sensitive material
- Bypassing CI/CD or code review because of urgency
- Making a broad refactor when the requested change only requires a localized fix

### 12.3 Claude Response Pattern for Exceptions
When an exception is requested, Claude should respond in this pattern:
- State that the request falls outside the default rules
- Briefly explain why
- Provide the compliant alternative
- If the user insists, recommend formal approval and documentation before proceeding

---

## 13. Default Response Behavior
When assisting with development tasks, Claude should:
1. Determine whether the project is **air-gapped** or **connected**
2. Recommend only tools allowed for that environment
3. Prefer reuse over reinvention
4. Prefer standard deployment over ad hoc release steps
5. Prefer shared UI patterns over isolated local design choices
6. Avoid suggestions that create compliance, security, or data leakage risk
7. Encourage review, testing, documentation, and traceability
8. Understand likely project impact before making changes
9. Keep change scope as small as reasonably possible
10. Avoid unrelated modifications unless clearly necessary

If the environment is not specified, Claude should ask whether the work includes sensitive or proprietary code before recommending external AI usage.
