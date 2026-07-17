# The All of Us Researcher Field Guide

# Website Architecture

**Version:** 1.0.0  
**Status:** Complete  
**Effective Date:** July 17, 2026  
**Document role:** Internal project specification  
**Visibility:** Repository home folder only; not included in public site navigation

---

# 1. Purpose

This document defines the technical and information architecture of the **All of Us Researcher Field Guide** website.

It establishes:

- The repository and folder structure
- The public site hierarchy
- Navigation rules
- Page types
- URL and filename conventions
- Layout and template responsibilities
- Asset organization
- Search and cross-linking behavior
- Jekyll and Just the Docs configuration
- GitHub Pages deployment conventions
- Content maintenance and quality-control requirements

The purpose of this architecture is to keep the Field Guide coherent, searchable, maintainable, and scalable as it grows from a small collection of guides into a large educational resource.

---

# 2. Architectural Principles

The website architecture follows eight principles.

## 2.1 Separate project governance from public content

Internal planning documents belong in the repository root or a private planning folder but must not appear in the public navigation.

These include:

- Project Charter
- Editorial Style Guide
- Website Architecture
- Design System
- Editorial Roadmap
- Page Template
- Contributor Guide
- Changelog

Public educational content belongs in dedicated topic folders.

## 2.2 Organize around user tasks

Readers should navigate by what they are trying to accomplish, not by the source notebook, research project, or code language.

For example:

- Build a cohort
- Understand an OMOP table
- Engineer a phenotype
- Analyze genomic data
- Validate a model
- Reproduce a complete pipeline

## 2.3 Keep pages short and focused

Each instructional page should answer one primary question. Large subjects should be divided into linked pages.

## 2.4 Preserve stable URLs

Published paths should remain stable whenever possible. Renaming or moving a page requires a redirect or preserved permalink.

## 2.5 Make navigation shallow

A reader should usually reach any guide within three navigation levels:

1. Major section
2. Topic group
3. Guide page

Avoid deeply nested hierarchies.

## 2.6 Treat complete pipelines as applications of core methods

Pipeline pages should link back to reusable foundational guides rather than duplicating explanations.

## 2.7 Design for gradual expansion

Folders may contain only a few pages initially, but their names and responsibilities should support future growth.

## 2.8 Prefer explicit structure over automation

Navigation order, page relationships, and metadata should be intentionally defined. The website should not depend on filenames or automatic alphabetical sorting to determine the reader's path.

---

# 3. Technology Stack

The public site uses:

- **GitHub Pages** for hosting
- **Jekyll** for static-site generation
- **Just the Docs** as the documentation theme
- **GitHub Actions** for build and deployment
- **Markdown** for educational content
- **Liquid** for reusable page components
- **Sass/CSS** for customization
- **Mermaid** for supported diagrams
- **SVG** for logos, icons, and durable vector figures
- **JavaScript** only when needed for focused enhancements

The architecture should remain compatible with standard GitHub Pages and avoid unnecessary dependencies.

---

# 4. Canonical Repository Structure

The repository should use the following top-level structure.

```text
aou-researcher-field-guide/
│
├── .github/
│   └── workflows/
│       └── pages.yml
│
├── _config.yml
├── Gemfile
├── Gemfile.lock
├── index.md
├── 404.html
├── README.md
├── LICENSE
├── CHANGELOG.md
│
├── 01_project_charter.md
├── 02_editorial_style_guide.md
├── 03_website_architecture.md
├── 04_design_system.md
├── 05_editorial_roadmap.md
├── 06_page_template.md
├── 07_contributor_guide.md
│
├── _includes/
│   ├── page-meta.html
│   ├── learning-objectives.html
│   ├── callout.html
│   ├── next-guide.html
│   ├── source-notebooks.html
│   └── footer-custom.html
│
├── _layouts/
│   ├── default.html
│   ├── home.html
│   ├── guide.html
│   ├── reference.html
│   └── pipeline.html
│
├── _sass/
│   ├── custom/
│   │   ├── _variables.scss
│   │   ├── _typography.scss
│   │   ├── _navigation.scss
│   │   ├── _homepage.scss
│   │   ├── _cards.scss
│   │   ├── _callouts.scss
│   │   ├── _code.scss
│   │   ├── _tables.scss
│   │   ├── _page-meta.scss
│   │   └── _responsive.scss
│   └── color_schemes/
│       └── field-guide.scss
│
├── assets/
│   ├── css/
│   │   └── custom.scss
│   ├── js/
│   │   ├── mermaid-init.js
│   │   └── field-guide.js
│   ├── images/
│   │   ├── brand/
│   │   ├── home/
│   │   ├── workspace/
│   │   ├── ehr/
│   │   ├── genomics/
│   │   ├── wearables/
│   │   ├── analysis/
│   │   ├── pipelines/
│   │   └── shared/
│   ├── icons/
│   └── downloads/
│
├── getting-started/
│   ├── index.md
│   ├── orientation.md
│   ├── choosing-a-workflow.md
│   └── first-analysis.md
│
├── workspace/
│   ├── index.md
│   ├── workbench-overview.md
│   ├── workspace-organization.md
│   ├── dataset-builder.md
│   ├── bigquery-basics.md
│   ├── notebooks-and-environments.md
│   ├── cloud-storage.md
│   ├── cost-management.md
│   └── reproducible-project-structure.md
│
├── ehr/
│   ├── index.md
│   ├── omop/
│   │   ├── index.md
│   │   ├── person.md
│   │   ├── condition-occurrence.md
│   │   ├── drug-exposure.md
│   │   ├── procedure-occurrence.md
│   │   ├── measurement.md
│   │   ├── observation.md
│   │   └── visit-occurrence.md
│   ├── cohorts/
│   │   ├── index.md
│   │   ├── defining-eligibility.md
│   │   ├── index-dates.md
│   │   ├── washout-periods.md
│   │   ├── comparator-groups.md
│   │   └── cohort-validation.md
│   ├── concepts/
│   │   ├── index.md
│   │   ├── concept-sets.md
│   │   ├── descendants.md
│   │   ├── standard-concepts.md
│   │   └── codeset-auditing.md
│   └── phenotypes/
│       ├── index.md
│       ├── phenotype-specification.md
│       ├── temporal-logic.md
│       ├── repeated-events.md
│       ├── missingness.md
│       └── phenotype-validation.md
│
├── genomics/
│   ├── index.md
│   ├── data-access/
│   ├── variants/
│   ├── structural-variation/
│   ├── polygenic-risk/
│   ├── association-testing/
│   ├── ancestry/
│   └── quality-control/
│
├── wearables/
│   ├── index.md
│   ├── fitbit-overview.md
│   ├── data-discovery.md
│   ├── daily-summary.md
│   ├── heart-rate.md
│   ├── activity.md
│   ├── sleep/
│   │   ├── index.md
│   │   ├── sleep-state-data.md
│   │   ├── session-construction.md
│   │   ├── feature-engineering.md
│   │   ├── quality-control.md
│   │   └── phenotype-validation.md
│   └── multimodal-integration.md
│
├── analysis/
│   ├── index.md
│   ├── study-design/
│   ├── data-engineering/
│   ├── statistical-modeling/
│   ├── sensitivity-analysis/
│   ├── multiple-testing/
│   ├── visualization/
│   ├── reproducibility/
│   └── reporting/
│
├── pipelines/
│   ├── index.md
│   ├── sleep-state-atlas/
│   ├── nd-cnv/
│   ├── il34/
│   ├── ftd-grn/
│   └── future-pipelines/
│
└── resources/
    ├── index.md
    ├── glossary.md
    ├── code-patterns.md
    ├── validation-checklists.md
    ├── troubleshooting.md
    ├── references.md
    └── release-notes.md
```

Folders may be introduced gradually. Empty public folders should not be added to navigation until they contain useful content.

---

# 5. Internal Files and Public Visibility

The following files are internal project documents and should remain in the repository home folder:

```text
01_project_charter.md
02_editorial_style_guide.md
03_website_architecture.md
04_design_system.md
05_editorial_roadmap.md
06_page_template.md
07_contributor_guide.md
```

They should not contain public navigation front matter.

To prevent Jekyll from publishing them, add them to `_config.yml`:

```yaml
exclude:
  - 01_project_charter.md
  - 02_editorial_style_guide.md
  - 03_website_architecture.md
  - 04_design_system.md
  - 05_editorial_roadmap.md
  - 06_page_template.md
  - 07_contributor_guide.md
```

The repository `README.md` may link to these documents for contributors without making them part of the public website.

---

# 6. Public Information Architecture

The public site has nine primary navigation sections.

## 6.1 Welcome

Purpose:

- Explain what the Field Guide is
- Identify its audience
- Provide clear entry points
- Introduce the Field Guide Method
- Direct readers to a learning pathway

Primary page:

```text
/
```

## 6.2 Getting Started

Purpose:

- Orient new Workbench users
- Explain how to use the guide
- Help readers choose a first workflow
- Provide the shortest path to a successful first analysis

Primary path:

```text
/getting-started/
```

## 6.3 Workspace

Purpose:

- Teach the working environment
- Explain Dataset Builder, BigQuery, notebooks, cloud storage, and costs
- Establish reproducible project organization

Primary path:

```text
/workspace/
```

## 6.4 EHR

Purpose:

- Teach OMOP
- Build cohorts
- Define concept sets
- Engineer and validate clinical phenotypes

Primary path:

```text
/ehr/
```

## 6.5 Genomics

Purpose:

- Explain genomic data products
- Teach variant and structural-variant workflows
- Cover PRS, association testing, ancestry, and QC

Primary path:

```text
/genomics/
```

## 6.6 Wearables

Purpose:

- Explain Fitbit data structures
- Construct sleep, activity, and heart-rate phenotypes
- Integrate wearable data with other domains

Primary path:

```text
/wearables/
```

## 6.7 Analysis

Purpose:

- Teach study design, data engineering, statistics, validation, visualization, reproducibility, and reporting

Primary path:

```text
/analysis/
```

## 6.8 Complete Pipelines

Purpose:

- Demonstrate end-to-end research workflows
- Show how foundational methods combine in real studies
- Document methodological evolution and validation decisions

Primary path:

```text
/pipelines/
```

## 6.9 Resources

Purpose:

- Provide quick-reference material
- Maintain a glossary
- Centralize reusable code patterns, checklists, troubleshooting, and references

Primary path:

```text
/resources/
```

---

# 7. Sidebar Navigation

The sidebar should use short, clear labels.

Recommended top-level order:

```text
Welcome
Getting Started
Workspace
EHR
Genomics
Wearables
Analysis
Complete Pipelines
Resources
```

## 7.1 Navigation depth

Use no more than three visible levels.

Example:

```text
EHR
├── OMOP
│   ├── Person
│   ├── Condition Occurrence
│   └── Measurement
├── Cohorts
├── Concept Sets
└── Phenotypes
```

## 7.2 Navigation ordering

Use explicit Just the Docs navigation metadata.

Example:

```yaml
---
title: Condition Occurrence
parent: OMOP
grand_parent: EHR
nav_order: 20
---
```

Do not rely on alphabetical order.

## 7.3 Section landing pages

Every top-level section and substantial topic group must have an `index.md` landing page.

A section landing page should include:

- A concise section overview
- Who the section is for
- Recommended starting point
- Topic cards or grouped links
- Suggested reading order
- Relevant complete pipelines

## 7.4 Navigation exclusions

Pages should use:

```yaml
nav_exclude: true
```

when they are:

- Supporting files
- Redirect pages
- Special landing pages not intended for the sidebar
- Drafts temporarily committed for review

---

# 8. Page Types

The site uses five public page types.

## 8.1 Home page

Purpose:

- Establish identity
- Explain the guide's value
- Provide immediate learning pathways
- Highlight major domains and selected pipelines

Layout:

```yaml
layout: home
```

## 8.2 Section landing page

Purpose:

- Orient readers within a major subject area
- Organize related guides
- Recommend a reading sequence

Examples:

- EHR
- Genomics
- Wearables
- Analysis

Recommended layout:

```yaml
layout: default
has_children: true
```

## 8.3 Guide

Purpose:

- Teach one focused concept or workflow
- Provide implementation, validation, and next steps

Layout:

```yaml
layout: guide
```

## 8.4 Reference

Purpose:

- Provide concise lookup information
- Define schemas, terms, code patterns, or decision aids
- Prioritize scanning over sequential reading

Layout:

```yaml
layout: reference
```

## 8.5 Pipeline

Purpose:

- Present an end-to-end research workflow
- Integrate foundational guides
- Document scientific decisions, revisions, and validation

Layout:

```yaml
layout: pipeline
```

---

# 9. Required Page Metadata

Every public guide, reference, or pipeline page should include YAML front matter.

Minimum guide front matter:

```yaml
---
title: Building Sleep Sessions
layout: guide
parent: Sleep
grand_parent: Wearables
nav_order: 20
permalink: /wearables/sleep/building-sleep-sessions/
page_type: guide
description: Construct participant-level sleep sessions from Fitbit sleep-state records.
reading_time: 12 minutes
difficulty: Intermediate
last_updated: 2026-07-17
applicable_cdr: CDR v8
prerequisites:
  - Fitbit Data Overview
  - BigQuery Basics
source_notebooks:
  - 02_aou_fitbit_psg_like_sleep_state_feature_engineering
---
```

Required metadata fields:

- `title`
- `layout`
- `page_type`
- `description`
- `reading_time`
- `difficulty`
- `last_updated`

Required when applicable:

- `parent`
- `grand_parent`
- `nav_order`
- `permalink`
- `applicable_cdr`
- `prerequisites`
- `source_notebooks`

Accepted difficulty values:

```text
Beginner
Intermediate
Advanced
```

Accepted page-type values:

```text
guide
reference
pipeline
landing
```

---

# 10. URL and Permalink Conventions

## 10.1 General rules

URLs should be:

- Lowercase
- Human-readable
- Hyphen-separated
- Stable
- Free of dates and version numbers unless versioning is essential

Preferred:

```text
/ehr/cohorts/defining-index-dates/
```

Avoid:

```text
/ehr/page17/
/EHR/Index_Dates/
/ehr/index-dates-v2-2026/
```

## 10.2 Directory-style URLs

Use trailing-slash directory paths through explicit permalinks.

## 10.3 Section paths

Keep the URL aligned with the public information architecture.

## 10.4 Renamed pages

When a published page is renamed:

1. Preserve the original permalink when possible.
2. If the URL must change, create a redirect.
3. Update all internal links.
4. Record the change in `CHANGELOG.md`.

---

# 11. Filename Conventions

Use:

```text
lowercase-kebab-case.md
```

Examples:

```text
dataset-builder.md
reciprocal-overlap.md
phenotype-validation.md
```

Use `index.md` for folder landing pages.

Do not include:

- Spaces
- Capital letters
- Dates
- Draft labels
- Version labels

Draft status belongs in front matter or a development branch, not the filename.

---

# 12. Homepage Architecture

The homepage should be a custom landing page rather than a default documentation page.

Recommended content order:

1. Hero
2. Primary call to action
3. Field Guide Method overview
4. Learn / Build / Validate or Learn / Build / Publish cards
5. Major pathway cards
6. Featured complete pipelines
7. Recently updated content
8. Mission statement
9. Footer

## 12.1 Hero

Required elements:

- Field Guide title
- Clear subtitle
- One primary action: **Start Learning**
- One secondary action: **Browse Complete Pipelines**
- Purposeful workflow illustration

## 12.2 Major pathway cards

Recommended cards:

- Getting Started
- EHR
- Genomics
- Wearables
- Analysis
- Complete Pipelines

## 12.3 Homepage exclusions

The homepage should not:

- Reproduce the full sidebar
- Present long narrative text
- Display internal project documents
- Use decorative scientific imagery without educational value
- Depend on emoji as permanent icons

---

# 13. Layout Responsibilities

## 13.1 `home.html`

Responsible for:

- Full-width homepage sections
- Hero treatment
- Homepage cards
- Featured pathway layout
- Recently updated content

## 13.2 `guide.html`

Responsible for:

- Standard page metadata
- Guide content width
- Learning-objective component
- Previous/next navigation
- Source notebook attribution
- Related guide links

## 13.3 `reference.html`

Responsible for:

- Compact metadata
- Scan-friendly content width
- Optional sticky table of contents
- Dense tables and quick links

## 13.4 `pipeline.html`

Responsible for:

- Pipeline overview
- Field Guide Method stage map
- Source notebook list
- Development history
- End-to-end workflow
- Related foundational guides

## 13.5 `default.html`

Used for:

- Section landing pages
- Special public pages
- Resources not requiring a specialized layout

---

# 14. Reusable Includes

Reusable visual or semantic components should be implemented as Liquid includes.

## 14.1 Page metadata

File:

```text
_includes/page-meta.html
```

Displays:

- Reading time
- Difficulty
- Last updated
- Applicable CDR
- Page type

## 14.2 Learning objectives

File:

```text
_includes/learning-objectives.html
```

Displays a consistent objectives panel.

## 14.3 Callout

File:

```text
_includes/callout.html
```

Supports only the approved types:

- Background
- Tip
- Validation
- Performance
- Common Mistake

## 14.4 Next guide

File:

```text
_includes/next-guide.html
```

Displays:

- Previous guide
- Next guide
- Optional pathway return link

## 14.5 Source notebooks

File:

```text
_includes/source-notebooks.html
```

Records which production notebooks informed the page without exposing restricted data or internal paths.

---

# 15. Content Relationships

Every guide page should connect to the larger site in four ways.

## 15.1 Prerequisites

Link to concepts the reader should understand first.

## 15.2 Next recommended guide

Provide a clear sequential next step.

## 15.3 Related guides

Link to nonsequential topics that deepen or extend the method.

## 15.4 Pipeline applications

Link to complete pipelines that use the method.

This relationship model allows readers to use the site as both:

- A sequential learning pathway
- A searchable reference

---

# 16. Search Architecture

Just the Docs search should index all public educational pages.

Internal planning documents must be excluded from the build and therefore from search.

## 16.1 Search-oriented writing

Every public page should include:

- A descriptive title
- A one-sentence description
- Clear headings
- Consistent terminology
- Synonyms where users may search different terms

## 16.2 Search result quality

Avoid duplicate or vague page titles.

Bad:

```text
Introduction
Overview
Basics
```

Preferred:

```text
Understanding Fitbit Sleep-State Records
Choosing an Index Date
Validating a Concept Set
```

## 16.3 Glossary

The glossary should provide brief definitions and link to full guides rather than duplicate instructional content.

---

# 17. Asset Architecture

## 17.1 Images

Store images by subject area.

Example:

```text
assets/images/wearables/sleep-session-construction.svg
```

Shared diagrams belong in:

```text
assets/images/shared/
```

Brand assets belong in:

```text
assets/images/brand/
```

## 17.2 File naming

Use descriptive lowercase filenames:

```text
cnv-reciprocal-overlap.svg
omop-table-relationships.svg
sleep-session-qc-example.png
```

## 17.3 Preferred formats

Use:

- SVG for diagrams, icons, and logos
- PNG for interface screenshots
- JPG only for photographic images
- WebP when useful and supported

## 17.4 Image requirements

Every educational image should have:

- Descriptive alt text
- A figure caption when interpretation is required
- A source or attribution when externally derived
- Sufficient resolution
- No restricted participant-level information

## 17.5 Downloads

Reusable notebooks, templates, and static resources belong in:

```text
assets/downloads/
```

Do not place large raw datasets in the repository.

---

# 18. Mermaid Diagrams

Mermaid may be used for:

- Workflows
- Decision trees
- Data-flow diagrams
- Architecture diagrams
- Study-design diagrams

Mermaid should not be used for:

- Publication figures requiring precise visual control
- Dense statistical plots
- Diagrams that become unreadable on mobile
- Figures that depend on unsupported syntax

All Mermaid diagrams must be tested in the deployed site.

---

# 19. Code Architecture

## 19.1 Code blocks

Use fenced code blocks with an explicit language.

Example:

```python
participant_count = cohort["person_id"].nunique()
```

## 19.2 Reusable code

Short reusable patterns may be shown directly in guides.

Long functions or full pipelines should be:

- Stored in downloadable notebooks or scripts
- Linked from the relevant guide
- Explained conceptually in the page

## 19.3 Data safety

Public examples must not expose:

- Participant-level data
- Controlled-access identifiers
- Workspace-specific secrets
- Billing project identifiers
- Restricted bucket paths
- Credentials or tokens

Use clearly marked placeholders where necessary.

---

# 20. Drafting and Publication States

Public content follows four states.

## 20.1 Planned

Listed only in the editorial roadmap.

## 20.2 Draft

Exists in a development branch or uses:

```yaml
published: false
```

## 20.3 Review

Content is complete but awaiting technical or editorial review.

## 20.4 Published

Merged into the default branch, indexed in search, and linked from the appropriate section.

Incomplete public pages should not be represented as finished guides.

---

# 21. GitHub Workflow

Recommended branch model:

```text
main
content/<topic>
design/<feature>
fix/<issue>
```

The `main` branch should remain deployable.

Recommended contribution sequence:

1. Create a focused branch.
2. Add or update content.
3. Preview locally when possible.
4. Open a pull request.
5. Complete editorial and technical review.
6. Merge into `main`.
7. Confirm successful Pages deployment.
8. Verify the live page.

Direct commits to `main` may be used during the initial solo-development phase, but pull requests are preferred once contributors join.

---

# 22. GitHub Pages Deployment

The site should deploy through GitHub Actions.

Canonical workflow location:

```text
.github/workflows/pages.yml
```

The workflow should:

1. Check out the repository.
2. Configure GitHub Pages.
3. Set up Ruby.
4. Install dependencies.
5. Build the Jekyll site.
6. Upload the Pages artifact.
7. Deploy the artifact.

The Pages source should be configured as:

```text
GitHub Actions
```

Build failures must be resolved before merging additional structural changes.

---

# 23. `_config.yml` Responsibilities

The Jekyll configuration should define:

- Site title
- Site description
- Repository URL
- Base URL
- Theme
- Color scheme
- Search behavior
- Heading anchors
- Back-to-top links
- Footer text
- Mermaid support
- Excluded internal files
- Auxiliary links
- Plugins permitted by GitHub Pages

Example structural settings:

```yaml
title: The All of Us Researcher Field Guide
description: Practical methods for reproducible EHR, genomic, and wearable data analysis in the All of Us Researcher Workbench.

remote_theme: just-the-docs/just-the-docs
color_scheme: field-guide

search_enabled: true
heading_anchors: true

back_to_top: true
back_to_top_text: Back to top

exclude:
  - 01_project_charter.md
  - 02_editorial_style_guide.md
  - 03_website_architecture.md
  - 04_design_system.md
  - 05_editorial_roadmap.md
  - 06_page_template.md
  - 07_contributor_guide.md
```

Repository-specific `url` and `baseurl` values must match the GitHub Pages deployment.

---

# 24. Responsive Design

All public pages must function on:

- Desktop
- Tablet
- Mobile

Responsive priorities:

- Readable line length
- Accessible sidebar behavior
- Cards that stack cleanly
- Tables that scroll horizontally when necessary
- Code blocks that do not break the page width
- Diagrams that remain legible
- Metadata that wraps without clutter

No essential content should depend on hover behavior.

---

# 25. Accessibility

The website should meet practical accessibility standards.

Required:

- Semantic heading order
- Descriptive link text
- Alt text for meaningful images
- Keyboard-accessible navigation
- Sufficient color contrast
- Visible focus states
- Tables with headers
- No meaning conveyed by color alone
- Reduced-motion compatibility for optional animation

Avoid links labeled only:

```text
Click here
Read more
This page
```

Use descriptive labels instead.

---

# 26. Performance

The website should remain lightweight.

Prefer:

- Static HTML
- SVG illustrations
- Compressed images
- Minimal JavaScript
- Theme-native behavior
- Reusable CSS classes

Avoid:

- Large client-side frameworks
- Autoplay media
- Uncompressed screenshots
- Duplicate libraries
- Decorative animation that delays reading

---

# 27. Versioning and Maintenance

## 27.1 Site versioning

Use semantic versioning for major public releases:

```text
MAJOR.MINOR.PATCH
```

Examples:

- `0.1.0`: Early structural prototype
- `0.5.0`: Core design and initial content
- `1.0.0`: First complete public release
- `1.1.0`: New content section
- `1.1.1`: Corrections without structural change

## 27.2 Page maintenance

Every public page should display `last_updated`.

Pages dependent on a specific All of Us data release should identify the applicable CDR.

## 27.3 Broken links

Internal and external links should be reviewed periodically.

## 27.4 Deprecated pages

Do not silently delete useful published pages.

Instead:

- Mark the page as deprecated
- Explain what replaced it
- Link to the current guide
- Preserve the old URL when feasible

---

# 28. Quality-Control Checklist

Before publishing a new section or structural change, verify:

## Repository structure

- File is located in the correct folder.
- Filename follows conventions.
- No internal planning document appears publicly.
- No restricted data or secrets are committed.

## Navigation

- Parent and grandparent values are correct.
- Navigation order is intentional.
- Section landing pages exist.
- The reader has a clear next step.

## URLs

- Permalink is readable and stable.
- Internal links use the correct base URL behavior.
- Renamed pages preserve or redirect old URLs.

## Layout

- Correct page layout is assigned.
- Page metadata renders correctly.
- Callouts use approved types.
- Tables and code blocks fit on mobile.

## Search

- Title is specific.
- Description is present.
- Headings use consistent terminology.
- Page is discoverable through likely search terms.

## Assets

- Images use descriptive filenames.
- Alt text is present.
- Figures contain no restricted information.
- File sizes are reasonable.

## Deployment

- Jekyll build succeeds.
- GitHub Actions deployment succeeds.
- Live page is checked after deployment.
- Browser console contains no relevant errors.

---

# 29. Initial Implementation Sequence

The architecture should be implemented in the following order.

## Phase 1: Core structure

1. Preserve the working GitHub Pages deployment.
2. Add internal planning documents to `_config.yml` exclusions.
3. Create the final top-level public folders.
4. Create section `index.md` landing pages.
5. Establish explicit sidebar navigation order.

## Phase 2: Layout foundation

1. Create specialized layouts.
2. Create reusable includes.
3. Add required page metadata conventions.
4. Implement previous/next navigation.
5. Test guide, reference, and pipeline page types.

## Phase 3: Visual system

1. Apply the approved color scheme.
2. Implement typography.
3. Style sidebar and navigation.
4. Style cards, callouts, tables, code blocks, and page metadata.
5. Validate mobile behavior.

## Phase 4: Homepage

1. Build custom homepage layout.
2. Add hero.
3. Add pathway cards.
4. Add Field Guide Method illustration.
5. Add featured pipelines and recent updates.

## Phase 5: Initial content

1. Publish Getting Started pages.
2. Publish Workspace fundamentals.
3. Publish foundational EHR pages.
4. Publish the first wearable and genomic guides.
5. Publish one complete pipeline demonstrating the architecture.

---

# 30. Architectural Decision Summary

The adopted architecture is:

- **Platform:** GitHub Pages
- **Generator:** Jekyll
- **Theme:** Just the Docs with substantial customization
- **Content format:** Markdown
- **Primary organization:** User tasks and analytical domains
- **Public depth:** Three navigation levels or fewer
- **Internal planning documents:** Repository root, excluded from Jekyll
- **Public page types:** Home, landing, guide, reference, pipeline
- **URLs:** Stable, lowercase, human-readable directory paths
- **Figures:** SVG-first, Mermaid where appropriate
- **Deployment:** GitHub Actions
- **Release model:** Semantic versioning
- **Core objective:** A scalable educational handbook that supports both sequential learning and rapid reference

---

# 31. Completion Standard

This architecture is considered successfully implemented when:

- The internal project documents remain available in the repository but do not appear on the public website.
- The homepage provides clear pathways into the guide.
- Every major section has a meaningful landing page.
- Public pages use consistent metadata and layouts.
- Navigation remains understandable as content expands.
- Search returns specific and useful results.
- Complete pipelines connect to reusable foundational guides.
- The site builds and deploys reliably through GitHub Actions.
- New contributors can determine where a page belongs without inventing new structural conventions.
