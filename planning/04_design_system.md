# The All of Us Researcher Field Guide

# Design System

**Version:** 1.0.0  
**Status:** Complete  
**Effective Date:** July 17, 2026  
**Document role:** Internal project specification  
**Visibility:** Repository only

---

# 1. Purpose

This document defines the visual language of the All of Us Researcher Field Guide. It establishes consistent standards for typography, color, spacing, navigation, components, imagery, icons, code presentation, tables, and responsive behavior.

The design should communicate **scientific credibility**, **clarity**, and **approachability**. The aesthetic target is best described as *modern academic*—clean, restrained, and durable.

---

# 2. Design Principles

1. Content is always the primary focus.
2. Minimize visual noise.
3. Reward exploration without overwhelming new users.
4. Maintain consistency across all page types.
5. Prefer whitespace over decoration.
6. Every visual element should serve an educational purpose.

---

# 3. Visual Identity

**Desired aesthetic**

- Johns Hopkins meets Apple
- Modern academic
- Clean documentation
- Minimalist
- High readability
- Long-form reading optimized

Avoid:

- Dashboard aesthetics
- Corporate SaaS styling
- Government website styling
- Excessive gradients or animation

---

# 4. Color Palette

| Role | Hex |
|------|------|
| Primary Navy | #183A5A |
| Secondary Blue | #2F6FA5 |
| Light Blue | #EAF3FA |
| Accent Gold | #C7A44D |
| Background Gray | #F7F8FA |
| White | #FFFFFF |
| Body Text | #2B2B2B |
| Secondary Text | #666666 |
| Borders | #DDDDDD |

Gold should be used sparingly for emphasis rather than branding.

---

# 5. Typography

## Headings

Primary serif:

- Merriweather

Fallback:

- Georgia
- serif

## Body

Primary sans-serif:

- Inter

Fallback:

- Source Sans 3
- system-ui

## Code

- JetBrains Mono
- Consolas
- monospace

Recommended scale:

- H1: 2.6rem
- H2: 2.0rem
- H3: 1.5rem
- H4: 1.25rem
- Body: 1rem
- Small: 0.9rem

---

# 6. Layout

Maximum content width:

900–1000 px

Content should be left-aligned within the reading column.

Maintain generous vertical spacing between sections.

---

# 7. Homepage

The homepage is intentionally distinct from documentation pages.

Structure:

1. Hero
2. Mission
3. Field Guide Method
4. Major pathway cards
5. Featured pipelines
6. Recently updated
7. Footer

---

# 8. Navigation

Sidebar:

- Fixed hierarchy
- Three visible levels maximum
- Explicit ordering
- Clear active-page indication

Breadcrumbs should appear above content.

---

# 9. Cards

Cards are the primary navigation component.

Each card contains:

- Title
- One-sentence description
- Optional icon
- Entire card clickable

Cards should use subtle elevation only.

---

# 10. Buttons

Primary:

- Filled navy background

Secondary:

- White background
- Navy border

Use sentence case.

---

# 11. Callouts

Only five callout styles exist.

| Type | Color |
|------|------|
| Background | Gray |
| Tip | Blue |
| Validation | Green |
| Performance | Gold |
| Common Mistake | Red |

All callouts use identical spacing and typography.

---

# 12. Code Blocks

Requirements:

- Rounded corners
- Horizontal scrolling
- Monospaced font
- Syntax highlighting
- Copy button (future enhancement)

---

# 13. Tables

Use minimal borders.

Avoid zebra striping.

Numeric values should be right-aligned where appropriate.

---

# 14. Figures

Preferred order:

1. SVG diagrams
2. Mermaid diagrams
3. Annotated screenshots
4. PNG/JPG

Every figure should include:

- Figure number
- Caption
- Alt text

---

# 15. Icons

Prefer simple line icons.

Icons should reinforce meaning rather than decorate.

---

# 16. Spacing

Use a consistent spacing scale.

Suggested:

- 8 px
- 16 px
- 24 px
- 32 px
- 48 px
- 64 px

Avoid arbitrary spacing values.

---

# 17. Responsive Design

Desktop is the primary target.

Tablet and mobile must preserve:

- Readability
- Sidebar usability
- Code scrolling
- Table accessibility

---

# 18. Accessibility

Minimum expectations:

- WCAG-conscious color contrast
- Keyboard navigation
- Visible focus states
- Descriptive link text
- Alt text for meaningful figures

---

# 19. Animation

Animation should be subtle and optional.

Acceptable:

- Hover transitions
- Card elevation
- Smooth scrolling

Avoid:

- Auto-playing animations
- Motion-heavy interfaces
- Decorative effects

---

# 20. CSS Organization

```text
_sass/
    custom/
        _variables.scss
        _typography.scss
        _navigation.scss
        _homepage.scss
        _cards.scss
        _callouts.scss
        _tables.scss
        _code.scss
        _page-meta.scss
        _responsive.scss
```

Each partial should have one clearly defined responsibility.

---

# 21. Component Library

Standard reusable components:

- Hero
- Section heading
- Navigation card
- Metadata panel
- Callout
- Figure
- Table
- Code block
- Previous / Next navigation
- Pipeline stage diagram

New components should only be added when reusable across multiple sections.

---

# 22. Visual Consistency Checklist

Before implementing a new page, verify:

- Typography matches standards.
- Colors come from the approved palette.
- Spacing follows the design scale.
- Components are reused rather than reinvented.
- Images support learning.
- Layout matches the appropriate page type.
- Mobile rendering remains readable.

---

# 23. Future Enhancements

Potential additions after Version 1.0:

- Dark mode
- Interactive pathway diagrams
- Progress indicators
- Interactive workflow visualizations
- Search result highlighting
- Copy-to-clipboard buttons
- Expandable code annotations

These enhancements should not compromise performance or readability.

---

# 24. Completion Standard

The design system is complete when a reader can move between any pages of the Field Guide and experience a unified visual identity that reinforces learning without distracting from the scientific content.
