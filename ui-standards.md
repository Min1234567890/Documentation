# UI Standards

## Purpose
This document defines the standard visual and interaction rules for backgrounds, splash screens, and buttons for web applications and Windows C# Forms–based software. These standards ensure consistency, usability, accessibility, and easier implementation across products and platforms.

## Scope
These rules apply to all new UI work unless a documented exception is approved.

---

# 1. Core Visual Standards

## 1.1 Color Principles
The default visual direction should remain simple, clean, and readable.

### Standard color guidance
- The **default background color should usually be white**.
- The primary working UI should favor **white backgrounds** for forms, content areas, data-entry screens, dialogs, and general application pages.
- Approved core colors are:
  - **Blue**: primary actions, links, selected states, information emphasis
  - **Red**: destructive actions, errors, critical warnings
  - **Yellow**: caution states, highlights, notices, pending attention
- Additional colors should be introduced only when necessary and must not conflict with these primary meanings.

## 1.2 Color Usage Rules
- White should be the standard base background for most screens.
- Blue should be the main accent color for interactive emphasis.
- Red must be reserved for destructive or error-related meaning.
- Yellow should be used sparingly for warnings, attention states, or highlights.
- Do not use red or yellow as general decorative brand colors for ordinary actions.
- Avoid overusing strong colors across large surfaces.
- Use neutral supporting colors where needed for borders, text, disabled states, and section separation.

## 1.3 Accessibility Requirements for Color
- Text and controls must remain readable against white and colored backgrounds.
- Blue, red, and yellow usage must preserve sufficient contrast.
- Meaning must not be communicated by color alone.
- Warnings, errors, and status states should also include text, icons, labels, or clear context.

---

# 2. Background Standards

## 2.1 Objective
Backgrounds must support content clarity, reinforce hierarchy, and maintain visual consistency without distracting from tasks.

## 2.2 Background Roles
Use backgrounds by semantic role, not by individual screen preference.

### Approved background roles
- **Default Background**: Main application screen background, usually white.
- **Surface Background**: Cards, grouped sections, panels, and containers.
- **Elevated Background**: Modals, popovers, dialogs, and floating surfaces.
- **Brand Background**: Approved branded surfaces used selectively.
- **Status Background**: Success, warning, error, or informational contextual surfaces.

## 2.3 Rules
- Use white as the default application background in most cases.
- Use only approved design system colors and tokens for backgrounds.
- Containers such as cards, sheets, and panels should use white or a subtle surface variation when separation is needed.
- Do not assign custom background colors to individual screens without design approval.
- Decorative gradients, patterns, textures, or image backgrounds are not recommended for normal workflow screens.
- Backgrounds must never reduce readability of text, icons, form fields, or controls.
- Layering should communicate hierarchy clearly through spacing, borders, grouping, or subtle elevation.

## 2.4 Accessibility Requirements
- Text and interactive elements placed on any background must meet accessibility contrast requirements.
- Background imagery must not interfere with legibility.
- Important information must never rely on subtle background changes alone.
- Status meaning must not be conveyed by color alone.

## 2.5 Usage Guidance
### Do
- Use white or very light neutral backgrounds for task-focused screens.
- Use sections, panels, and grouping to organize content.
- Keep visual noise low in workflow and productivity screens.
- Use blue as the main visual accent.

### Do Not
- Mix many unrelated background colors on one screen.
- Use photo backgrounds behind forms or dense text.
- Create one-off background treatments for individual features.
- Use low-contrast overlays that make content harder to read.

---

# 3. Splash Screen Standards

## 3.1 Objective
The splash screen introduces the product during launch and provides a brief, branded loading state while the application initializes.

## 3.2 Allowed Content
A splash screen may contain only the following:
- Official app logo
- Product or brand name
- Optional loading indicator
- Optional short tagline if officially approved

## 3.3 Prohibited Content
A splash screen must not contain:
- Promotional messaging
- Feature carousels
- Multiple calls to action
- Forms or inputs
- Dense descriptive text
- Unapproved illustrations or imagery

## 3.4 Layout Rules
- Keep the layout simple, centered, and visually balanced.
- Place the logo as the primary focal point.
- Maintain consistent spacing on all supported devices or windows.
- Preserve logo clear space and minimum size requirements.
- Avoid clutter and secondary visual elements.

## 3.5 Visual Rules
- Splash screens should usually use a **white background**.
- Blue should be the preferred accent color for brand emphasis.
- Red and yellow should not be dominant splash background colors except for a formally approved brand exception.
- Use only official brand assets.
- Animation is optional and must remain subtle.
- Motion must not distract, delay, or create perceived instability.

## 3.6 Behavior Rules
- Show the splash screen only during startup or required initialization.
- Transition to the first usable screen as soon as initialization is complete.
- Do not extend splash duration for branding alone.
- If loading takes longer than expected, provide a simple loading indicator or progress feedback where appropriate.
- The splash screen must fail gracefully if an asset cannot be loaded.

## 3.7 Accessibility Requirements
- All text and logo treatments must remain legible.
- Motion must be minimal and should respect reduced motion preferences when supported.
- The splash screen must not trap the user or block accessibility tools longer than necessary.

## 3.8 Usage Guidance
### Do
- Keep the splash screen minimal.
- Use a white background with blue accents where possible.
- Use a single approved logo lockup.
- Hand off quickly to the app.

### Do Not
- Add unnecessary text or marketing copy.
- Use the splash screen as an advertisement.
- Delay startup for decorative animation.
- Use inconsistent logo treatments across products.

---

# 4. Button Standards

## 4.1 Objective
Buttons communicate available actions and must provide clear hierarchy, consistent behavior, and accessible interaction states.

## 4.2 General Rules
- Use shared button components from the design system.
- Do not create custom one-off button styles for individual screens unless approved.
- Every button must clearly communicate its action.
- Buttons must be visually distinct from non-interactive elements.
- Buttons must provide consistent interaction feedback.

## 4.3 Supported Button Variants
### Primary Button
- Use for the most important action in a section or view.
- Primary buttons should usually use **blue**.

### Secondary Button
- Use for supporting actions that are less prominent than the primary action.
- Secondary buttons may use a white background with blue border or blue text.

### Tertiary or Text Button
- Use for low-emphasis actions.
- Tertiary buttons should generally use blue text or a subtle neutral style.

### Destructive Button
- Use for delete, remove, reset, or irreversible actions.
- Destructive buttons should use **red**.

### Warning or Attention Action
- Use yellow only when the action or message represents caution, review, or pending attention.
- Yellow should not replace blue as the general action color.

### Icon Button
- Use for compact actions when the icon meaning is universally clear or paired with an accessible label.

## 4.4 Hierarchy Rules
- A view or section should normally have one primary action.
- Do not place multiple competing primary buttons side by side unless a documented exception exists.
- Use secondary or tertiary styles for lower-priority actions.
- Destructive actions must not visually compete with a safe primary action unless deletion is the main task.

## 4.5 Labeling Rules
- Use clear action verbs such as **Save**, **Continue**, **Submit**, **Delete**, **Cancel**, or **Close**.
- Keep labels concise and specific.
- Avoid vague labels such as **OK** or **Click Here** unless context makes the meaning obvious.
- Use sentence case or the product-standard casing consistently.

## 4.6 Sizing and Layout
- Define standard sizes such as small, medium, and large if needed by the product.
- Maintain consistent horizontal padding, vertical padding, border radius, and typography.
- Buttons must meet minimum touch target size requirements.
- Preserve sufficient spacing between adjacent buttons and surrounding content.
- Icon and text spacing must be consistent.

## 4.7 Required States
Each button variant must define and support:
- Default
- Hover
- Focus
- Pressed or active
- Disabled
- Loading

## 4.8 State Behavior Rules
- Hover states should indicate interactivity without changing meaning.
- Focus states must be clearly visible and keyboard accessible.
- Pressed states should provide immediate tactile-style feedback.
- Disabled states must look inactive but remain legible.
- Loading states must prevent duplicate submissions when appropriate.
- A loading button should preserve layout stability and communicate progress.

## 4.9 Accessibility Requirements
- Buttons must be accessible by keyboard where applicable.
- Focus indicators must be visible and not removed without an accessible replacement.
- Color must not be the only cue for state or meaning.
- Icon-only buttons must include accessible names.
- Disabled and destructive buttons must still be understandable to all users.
- Touch and click targets must support accessible interaction.

## 4.10 Usage Guidance
### Do
- Use one primary action per area.
- Use blue for the main action.
- Use red only for destructive actions.
- Use yellow sparingly for warnings or caution emphasis.
- Show loading state for asynchronous actions.
- Keep button placement consistent across similar screens.

### Do Not
- Add many primary buttons in one place.
- Use red for normal actions.
- Use yellow as a replacement for primary action styling.
- Use icon-only buttons without accessible labels.
- Change button style arbitrarily between screens.

---

# 5. Web Platform Guidance

## 5.1 Web Background Standards
- Web application pages should usually use a white background.
- Content containers such as forms, cards, tables, and panels should maintain a clean, light appearance.
- Avoid background images behind forms, tables, or text-heavy interfaces.
- Blue should be the main interactive accent for links, buttons, selected states, and highlighted controls.
- Red should be reserved for validation errors, destructive actions, or critical notices.
- Yellow should be used for warnings, pending review, or caution messages.

## 5.2 Web Loading and Splash Standards
- Web applications should prefer lightweight loading states over heavy splash experiences.
- If a splash or branded loading screen is used, it should usually use a white background with blue visual emphasis.
- Loading screens must transition to usable UI immediately when core resources are ready.
- Long-running data loads should use inline loading indicators or skeleton states rather than repeated splash behavior.

## 5.3 Web Button Standards
- Use buttons for actions and links for navigation.
- All interactive buttons must support hover, focus-visible, active, disabled, and loading states.
- Keyboard users must be able to reach and trigger buttons predictably.
- Primary form actions should use blue.
- Destructive actions should use red.
- Warning-related attention actions may use yellow only when context supports caution.
- Loading buttons should preserve width where possible to avoid layout shift.

---

# 6. Windows Forms Platform Guidance

## 6.1 Windows Forms Background Standards
- Standard forms should usually use a white background.
- Data-entry and workflow screens should prioritize clarity over decorative styling.
- Panels, group boxes, and sections should provide structure instead of large decorative color blocks.
- Full-form gradients, wallpapers, or image backgrounds are not permitted in operational screens.
- Blue should be used for the main accent and action emphasis.
- Red should identify destructive or error-related meaning.
- Yellow should identify caution, notices, or items requiring review.

## 6.2 Windows Forms Splash Screen Standards
- Use a splash screen only when application startup time is long enough to require feedback.
- The splash screen should usually use a white background.
- Blue should be the preferred accent color for product identity.
- The splash screen should show the product identity and optional loading progress only.
- It must close automatically once the main form is ready.
- Splash screens must not contain setup choices, login inputs, or promotional content.

## 6.3 Windows Forms Button Standards
- Standard forms and dialogs must use consistent action ordering and labeling.
- The default action should be mapped to Enter where appropriate.
- The cancel or close action should be mapped to Escape where appropriate.
- Primary buttons should usually use blue.
- Destructive buttons should use red.
- Yellow should be reserved for caution-related actions only when truly needed.
- Buttons must use clear labels such as Save, Apply, Cancel, Close, Delete, or Export.
- Destructive actions should require confirmation if the action is irreversible.
- Tab navigation must move through controls in a logical order.
- Buttons must remain fully readable under system font scaling and high DPI settings.

---

# 7. Cross-Platform Consistency

- Shared design intent must remain consistent across web and Windows Forms implementations.
- White should remain the usual default background across both platforms.
- Blue should remain the main action color across both platforms.
- Red should consistently mean destructive, error, or critical action.
- Yellow should consistently mean warning, caution, review, or attention.
- Labels, hierarchy, and state behavior should remain aligned even when platform controls differ.
- Platform-native interaction patterns may be used as long as they do not conflict with the shared design system.

---

# 8. Design Tokens and Reuse

## 8.1 Principle
All background, splash, and button styles should be driven by shared design tokens and reusable components whenever possible.

## 8.2 Recommended Token Categories
Recommended token groups include:
- Background color
- Primary action color
- Destructive color
- Warning color
- Typography
- Spacing
- Border radius
- Elevation or shadow
- Motion duration and easing
- Opacity

## 8.3 Reuse Rules
- Reference shared tokens instead of hard-coded values.
- Reuse approved components before introducing a new pattern.
- Any new visual variation must be evaluated for reusability.
- If exact shades are defined later, they should continue to follow the same semantic meanings:
  - Blue = primary/information
  - Red = destructive/error
  - Yellow = warning/attention

---

# 9. Review and Exceptions

## 9.1 Review Process
Any deviation from these standards should be documented and reviewed before implementation.

## 9.2 Exception Criteria
Exceptions may be considered when:
- A platform has a documented native requirement.
- Accessibility requires an alternative treatment.
- Branding requirements have been formally approved.
- A new reusable pattern is being proposed for the design system.

---

# 10. Summary

These standards exist to ensure that:
- White remains the usual default background.
- Blue is used for primary and interactive emphasis.
- Red is used for destructive and error meaning.
- Yellow is used for warning and caution meaning.
- Splash screens remain minimal, branded, and performance-conscious.
- Buttons are consistent, understandable, and accessible.
- Web and Windows Forms applications follow the same design intent.

Teams should treat these rules as the baseline for all UI work and extend them only through documented design system decisions.
