# UI Standards

## Purpose
This document defines the standard visual and interaction rules for backgrounds, splash screens, and buttons. These standards ensure consistency, usability, accessibility, and easier implementation across products and platforms.

## Scope
These rules apply to all new UI work unless a documented exception is approved.

---

# 1. Background Standards

## 1.1 Objective
Backgrounds must support content clarity, reinforce hierarchy, and maintain visual consistency without distracting from tasks.

## 1.2 Background Roles
Use backgrounds by semantic role, not by individual screen preference.

### Approved background roles
- **Default Background**: Main application screen background.
- **Surface Background**: Cards, grouped sections, panels, and containers.
- **Elevated Background**: Modals, popovers, dialogs, and floating surfaces.
- **Brand Background**: Approved branded surfaces for onboarding, marketing, or launch experiences.
- **Status Background**: Success, warning, error, or informational contextual surfaces.

## 1.3 Rules
- Use only approved design system color tokens for backgrounds.
- Default application pages must use the default background token.
- Containers such as cards, sheets, and panels must use surface or elevated tokens.
- Do not assign custom background colors to individual screens without design approval.
- Decorative gradients, patterns, textures, or image backgrounds are only allowed in branded or explicitly approved experiences.
- Backgrounds must never reduce readability of text, icons, form fields, or controls.
- Backgrounds must support all active themes, including light mode and dark mode if applicable.
- Layering should communicate hierarchy clearly through contrast, elevation, or both.

## 1.4 Accessibility Requirements
- Text and interactive elements placed on any background must meet accessibility contrast requirements.
- Background imagery must not interfere with legibility.
- Important information must never rely on subtle background changes alone.
- Status meaning must not be conveyed by color alone.

## 1.5 Usage Guidance
### Do
- Use neutral backgrounds for task-focused screens.
- Use surface layers to separate sections.
- Keep visual noise low in workflow and productivity screens.
- Use brand backgrounds sparingly and consistently.

### Do Not
- Mix many unrelated background colors on one screen.
- Use photo backgrounds behind core transactional content.
- Create one-off background treatments for individual features.
- Use low-contrast overlays that make content harder to read.

---

# 2. Splash Screen Standards

## 2.1 Objective
The splash screen introduces the product during launch and provides a brief, branded loading state while the app initializes.

## 2.2 Allowed Content
A splash screen may contain only the following:
- Official app logo
- Product or brand name
- Optional loading indicator
- Optional short tagline if officially approved

## 2.3 Prohibited Content
A splash screen must not contain:
- Promotional messaging
- Feature carousels
- Multiple calls to action
- Forms or inputs
- Dense descriptive text
- Unapproved illustrations or imagery

## 2.4 Layout Rules
- Keep the layout simple, centered, and visually balanced.
- Place the logo as the primary focal point.
- Maintain consistent safe area spacing on all supported devices.
- Preserve logo clear space and minimum size requirements.
- Avoid clutter and secondary visual elements.

## 2.5 Visual Rules
- Use only the approved splash background color or approved branded gradient.
- Use only official brand assets.
- Animation is optional and must remain subtle.
- Motion must not distract, delay, or create perceived instability.
- If dark mode support is provided, splash assets must be designed specifically for it.

## 2.6 Behavior Rules
- Show the splash screen only during startup or required initialization.
- Transition to the first usable screen as soon as initialization is complete.
- Do not extend splash duration for branding alone.
- If loading takes longer than expected, provide a simple loading indicator or progress feedback where appropriate.
- The splash screen must fail gracefully if an asset cannot be loaded.

## 2.7 Accessibility Requirements
- All text and logo treatments must remain legible.
- Motion must be minimal and should respect reduced motion preferences when supported.
- The splash screen must not trap the user or block accessibility tools longer than necessary.

## 2.8 Usage Guidance
### Do
- Keep the splash screen minimal.
- Use a single approved logo lockup.
- Hand off quickly to the app.
- Optimize assets for performance.

### Do Not
- Add unnecessary text or marketing copy.
- Use the splash screen as an advertisement.
- Delay startup for decorative animation.
- Use inconsistent logo treatments across products.

---

# 3. Button Standards

## 3.1 Objective
Buttons communicate available actions and must provide clear hierarchy, consistent behavior, and accessible interaction states.

## 3.2 General Rules
- Use shared button components from the design system.
- Do not create custom one-off button styles for individual screens unless approved.
- Every button must clearly communicate its action.
- Buttons must be visually distinct from non-interactive elements.
- Buttons must provide consistent interaction feedback.

## 3.3 Supported Button Variants
### Primary Button
Use for the most important action in a section or view.

### Secondary Button
Use for supporting actions that are less prominent than the primary action.

### Tertiary or Text Button
Use for low-emphasis actions, especially in dense interfaces.

### Destructive Button
Use for delete, remove, reset, or irreversible actions.

### Icon Button
Use for compact actions when the icon meaning is universally clear or paired with an accessible label.

## 3.4 Hierarchy Rules
- A view or section should normally have one primary action.
- Do not place multiple competing primary buttons side by side unless a documented exception exists.
- Use secondary or tertiary styles for lower-priority actions.
- Destructive actions must never visually compete with a safe primary action unless deletion is the main task.

## 3.5 Labeling Rules
- Use clear action verbs such as **Save**, **Continue**, **Submit**, **Delete**, or **Cancel**.
- Keep labels concise and specific.
- Avoid vague labels such as **OK** or **Click Here** unless context makes the meaning obvious.
- Use sentence case or the product-standard casing consistently.

## 3.6 Sizing and Layout
- Define standard sizes such as small, medium, and large if needed by the product.
- Maintain consistent horizontal padding, vertical padding, border radius, and typography.
- Buttons must meet minimum touch target size requirements.
- Preserve sufficient spacing between adjacent buttons and surrounding content.
- Icon and text spacing must be consistent.

## 3.7 Required States
Each button variant must define and support:
- Default
- Hover
- Focus
- Pressed or active
- Disabled
- Loading

## 3.8 State Behavior Rules
- Hover states should indicate interactivity without changing meaning.
- Focus states must be clearly visible and keyboard accessible.
- Pressed states should provide immediate tactile-style feedback.
- Disabled states must look inactive but remain legible.
- Loading states must prevent duplicate submissions when appropriate.
- A loading button should preserve layout stability and communicate progress.

## 3.9 Accessibility Requirements
- Buttons must be accessible by keyboard where applicable.
- Focus indicators must be visible and not removed without an accessible replacement.
- Color must not be the only cue for state or meaning.
- Icon-only buttons must include accessible names.
- Disabled and destructive buttons must still be understandable to all users.
- Touch and click targets must support accessible interaction.

## 3.10 Usage Guidance
### Do
- Use one primary action per area.
- Use descriptive labels.
- Show loading state for asynchronous actions.
- Use destructive styling only for risky actions.
- Keep button placement consistent across similar screens.

### Do Not
- Add many primary buttons in one place.
- Use color alone to communicate destructive meaning.
- Use icon-only buttons without accessible labels.
- Change button style arbitrarily between screens.
- Hide important actions behind unclear styling.

---

# 4. Design Tokens and Reuse

## 4.1 Principle
All background, splash, and button styles should be driven by shared design tokens and reusable components whenever possible.

## 4.2 Token Categories
Recommended token groups include:
- Color
- Typography
- Spacing
- Border radius
- Elevation or shadow
- Motion duration and easing
- Opacity

## 4.3 Reuse Rules
- Reference shared tokens instead of hard-coded values.
- Reuse approved components before introducing a new pattern.
- Any new visual variation must be evaluated for reusability.

---

# 5. Review and Exceptions

## 5.1 Review Process
Any deviation from these standards should be documented and reviewed before implementation.

## 5.2 Exception Criteria
Exceptions may be considered when:
- A platform has a documented native requirement.
- Accessibility requires an alternative treatment.
- Branding requirements have been formally approved.
- A new reusable pattern is being proposed for the design system.

---

# 6. Summary

These standards exist to ensure that:
- Backgrounds support readability and hierarchy.
- Splash screens remain minimal, branded, and performance-conscious.
- Buttons are consistent, understandable, and accessible.

Teams should treat these rules as the baseline for all UI work and extend them only through documented design system decisions.
