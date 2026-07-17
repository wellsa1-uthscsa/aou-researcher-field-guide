# The All of Us Researcher Field Guide

# Standard Page Template

**Version:** 1.0.0  
**Status:** Complete  
**Effective Date:** July 17, 2026  
**Document role:** Internal project specification  
**Visibility:** Repository only

---

# Purpose

Every public instructional page should follow this template to ensure consistency across the Field Guide.

---

# Standard Structure

1. Title
2. One-sentence description
3. Reading time
4. Difficulty
5. Last updated
6. Prerequisites
7. Learning objectives
8. Why This Matters
9. Background
10. Implementation
11. Validation
12. Common Mistakes
13. Performance Tips (optional)
14. Related Guides
15. References

---

# Required Front Matter

```yaml
---
title:
layout: guide
parent:
grand_parent:
nav_order:
description:
reading_time:
difficulty:
last_updated:
applicable_cdr:
page_type: guide
---
```

---

# Learning Objectives

Use 3–6 objectives beginning with action verbs.

Examples:

- Describe
- Construct
- Validate
- Compare
- Interpret

---

# Why This Matters

Explain the scientific motivation before discussing implementation.

---

# Background

Provide conceptual knowledge required for the workflow.

---

# Implementation

Present reproducible steps with explanatory text and tested code examples.

---

# Validation

Describe expected outputs, quality-control checks, and common indicators of success.

---

# Common Mistakes

List frequent errors and explain how to recognize and correct them.

---

# Performance Tips

Optional optimization strategies for large datasets or computational efficiency.

---

# Related Guides

Link to:

- Prerequisites
- Next recommended guide
- Relevant pipelines
- Related concepts

---

# References

Prefer primary literature and official documentation.

---

# Completion Standard

A completed page should enable a reader to understand the scientific rationale, reproduce the workflow, validate the results, and identify where the method fits within the broader analytical framework.
