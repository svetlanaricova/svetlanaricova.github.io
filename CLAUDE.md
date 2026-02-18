# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static CV/resume for Dr. Svetlana Ricova (Internal Medicine Specialist). No build system, no framework — just hand-crafted HTML+CSS with a Markdown data source.

## Architecture

- **`cv-data.md`** — Single source of truth for all resume content (Romanian language). Structured by sections: personal data, professional experience, education, additional studies, languages, digital skills, driver's license.
- **`cv.html`** — Styled resume document with all CSS embedded in `<style>`. Two-column layout: dark teal sidebar (75mm) + main content area. A4 print-optimized.
- **`*.pdf`** — PDF exports generated from the HTML (via browser print or Puppeteer).

## Workflow

When updating resume content: edit `cv-data.md` first, then update the corresponding sections in `cv.html` to match. The HTML is the rendered output — there is no automated md-to-html conversion.

## PDF Generation

Puppeteer MCP server is configured (`.claude/settings.local.json`). Use it to render `cv.html` to PDF at A4 size with no margins (the HTML handles its own page layout).

## Design Constraints

- Page size is exactly A4 (210mm × 297mm) — all content must fit within one page
- Typography: Playfair Display (headings), Source Sans Pro (body) via Google Fonts
- Color palette: dark teal sidebar (#1a3a4a, #1e4d5e), accent blue (#8ecae6), light text on dark (#e2e8f0, #cbd5e0)
- `print-color-adjust: exact` is required for correct PDF colors
- All text content is in Romanian
