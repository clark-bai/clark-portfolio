---
title: "Portfolio Website"
description: "This website — a statically generated portfolio built with Astro, TypeScript, and a CI/CD pipeline deploying to Vercel."
tags: ["Astro", "TypeScript", "CSS", "GitHub Actions"]
github: "https://github.com/clark-bai/clark-portfolio"
date: 2025-04-01
featured: false
---

## Overview

A personal portfolio site designed for fast load times, accessibility, and easy content management. Built with Astro for static generation, styled with CSS custom properties (no framework), and deployed automatically via GitHub Actions to Vercel.

## Approach

- **Framework** — Astro, chosen for its zero-JS-by-default philosophy. Client-side JavaScript is only added where genuinely needed (e.g. the typed-text hero effect).
- **Styling** — A design token system using CSS custom properties for colours, spacing, and typography. Dark mode is handled entirely through token swaps — no duplicate stylesheets.
- **Content** — Projects and blog posts are Markdown files in content collections. Adding content means adding a file, with no layout or component changes required.
- **CI/CD** — GitHub Actions runs linting, builds, Lighthouse audits, and link checks on every pull request. Merges to main trigger automatic deployment.
- **Accessibility** — Semantic HTML, WCAG 2.1 AA contrast ratios, keyboard navigation, and screen reader landmarks throughout.

## Outcome

The site scores 95+ on Lighthouse across all categories, loads in under 1 second on a fast connection, and weighs less than 300 KB uncompressed. Adding a new project or blog post requires zero code changes.

## Lessons learnt

- CSS custom properties make dark mode almost free if you commit to the token system from the start.
- Astro's content collections enforce frontmatter schemas at build time, which catches errors before they reach production.
- A good CI pipeline pays for itself on the first broken build it catches.
