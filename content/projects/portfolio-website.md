---
title: "Portfolio Website (Hugo + PaperMod)"
date: 2026-01-31
draft: false
tags: ["Hugo", "Static Site", "Deployment", "Security Mindset"]
summary: "Built and deployed a production portfolio site with working social links and a hosted resume download, focused on clear UX and secure, low-attack-surface design."
---

## Current status
This portfolio site is live and actively being iterated on. It serves as my public hub for projects, resume access, and contact links while I build toward cloud security engineering.

**Live site:** https://troypeiler.com

## What’s working now
- **Profile-mode homepage** with a clear intro, subtitle, and primary CTAs (Projects / Resume / Contact)
- **Social icons** (LinkedIn, GitHub, Email) rendered via PaperMod config
- **Resume download link** hosted as a static asset at `/resume/resume.pdf`
- **Top navigation** for Resume / About / Projects / Posts

## Technical details
- **Framework:** Hugo
- **Theme:** PaperMod
- **Static assets:** served from the `static/` directory (resume hosted under `static/resume/resume.pdf`)
- **Config-driven UI:** homepage profile mode + buttons + social icons configured via `hugo.toml`

## Security / reliability considerations
- **Low attack surface:** static site with no server-side runtime
- **Safe linking:** external links use standard `rel` practices via theme defaults
- **Operational thinking:** debugged PDF loading and CDN/browser caching behavior (validated via browser Network tools)
- **No sensitive data:** site content is public-facing; avoids embedding secrets or internal-only details

## What I learned
- How to structure a Hugo site (content sections, static assets, theme configuration)
- How to troubleshoot production issues using Network headers/status codes and cache behavior
- How to ship incremental improvements quickly (social links, resume routing, navigation UX)

## Next improvements (roadmap)
- Create a more compelling **Projects** landing page with 3 polished project write-ups + screenshots
- Add a **Contact** page with clear call-to-action for recruiters/collaboration
- Add basic **security headers** (CSP/HSTS) depending on hosting setup
- Use a **versioned resume filename** (e.g., `Troy-Peiler-Resume-2026.pdf`) to eliminate caching confusion on updates

## Links
- **Source code:** (https://github.com/tpeiler/tpeiler.github.io.git)
- **Resume:** https://troypeiler.com/resume/resume.pdf
- **LinkedIn:** https://www.linkedin.com/in/troy-peiler-a23139189/
- **GitHub:** https://github.com/tpeiler