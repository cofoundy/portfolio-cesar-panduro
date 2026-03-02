# QA Report: Cesar Erick Panduro Mendoza

**Date:** 2026-03-01
**URL:** https://cesar-panduro.cofoundy.dev
**Status:** FAIL

## Data Validation
- [x] Name matches source: "Cesar Erick Panduro Mendoza" matches Google Sheet and config.ts
- [x] Email matches source: ericsompm1994@gmail.com (Cloudflare email-protected, but present)
- [x] Title "Profesional" -- acceptable given no specific title in CV/Sheet
- [x] No hallucinated data -- all content matches research-notes.md and config.ts
- [x] Empty arrays (projects, experience, education) correctly hidden from page

## Clean Deploy
- [x] No "Powered by" / "Made with" / "Built with" watermarks
- [x] No "Lorem ipsum" or placeholder text
- [x] No template links (View source, Fork, GitHub)
- [x] No "undefined" or "null" visible in content
- [ ] meta generator tag shows "Astro v5.12.3" (in HTML head only, not visible to users -- acceptable)

## Technical
- [x] CSS loads: /_astro/index.CPQErQgZ.css -- HTTP 200
- [x] Favicon loads: /favicon.svg -- HTTP 200
- [x] profile.jpg exists on server -- HTTP 200
- [x] Google Fonts (IBM Plex Mono) loading correctly
- [x] Cloudflare email protection active

## Issues Found

### ISSUE 1 (MEDIUM): Profile photo not displayed on page
- profile.jpg returns HTTP 200 at https://cesar-panduro.cofoundy.dev/profile.jpg
- However, there are ZERO <img> tags in the entire page HTML
- The hero section has no photo -- only text (name + title)
- The About section also has no photo
- Client uploaded a professional photo (formal suit with tie) -- it should be shown
- **Fix:** Add profile photo to hero section or about section

### ISSUE 2 (LOW): LinkedIn not linked
- Client wrote "Linkedlh" in social media field (likely typo for LinkedIn)
- No LinkedIn URL was found during research
- Current page only shows email icon in hero and footer
- **Status:** Acceptable -- no LinkedIn URL available to link

### ISSUE 3 (LOW): Generic title "Profesional"
- The job title shows as just "Profesional" which is very generic
- However, the client did not provide a CV or specific job title
- research-notes.md confirms "Titulo profesional: No especificado"
- **Status:** Acceptable given available data, but could be improved if client provides more info

### ISSUE 4 (INFO): Phone number not shown
- Client provided phone 931452706 in the form
- Not displayed on portfolio
- **Status:** Minor -- phone display is optional

## Summary
The portfolio is technically healthy (CSS, favicon, assets all load correctly). Empty sections are properly hidden. The name, email, and content match source data with no hallucinations. However, the client's professional photo is uploaded but NOT displayed anywhere on the page, which is a significant gap for a portfolio site.

## Evidence
- Screenshots not available (no browser automation tool in current session)
- All checks performed via curl HTTP requests and HTML content analysis

## Verdict
**FAIL** -- Profile photo must be displayed on the page before delivery.
