# Project Intelligence & Structural Observations: Portfolio Cloud

This file centralizes the technical and structural context for Juan Carlos Diaz's portfolio. Treat it as a handoff notebook for future agents, not end-user documentation. Keep project documentation in English unless the user explicitly asks otherwise.

## 1. Project Architecture
- **Model:** Multi-Page Application (MPA).
- **Technologies:** HTML5, CSS3 (custom variables, grids, flexbox), vanilla JavaScript.
- **File structure:** Flat structure, with all primary HTML files in the project root.
- **Navigation:** Hub-and-spoke system. `index.html` acts as the central hub and links to project-specific pages such as `nexusgrid.html`, `soltech_english.html`, and others.

## 2. Engineering Observations

### Strengths
- **CSS variables:** Strong use of `:root` variables to keep each project micro-brand coherent.
- **Visual performance:** Canvas/background animations use `requestAnimationFrame`, with recent optimizations to avoid permanent loops when no visible animation is active.
- **Interactions:** Custom cursors and reveal/hover effects give the portfolio a polished feel.
- **Security:** External links correctly use `target="_blank"` with `rel="noopener noreferrer"`.

### Technical Debt
- **Code duplication:** Global elements such as Google Analytics, cursor logic, navigation, and footer patterns are manually repeated across pages.
    - *Suggestion:* Move to a static site generator such as Astro or Jekyll when reuse starts costing more than the current simple setup.
- **Asset management:** Styles and scripts are inline inside HTML files, which limits browser caching and makes maintenance harder.
- **Accessibility:** Some decorative elements and links with button-like behavior could use stronger semantics for screen readers.

## 3. Project Breakdown (Micro-Brands)
Each portfolio page/card has its own visual language:
1. **Lighttown Barbershop:** Client website for a Dutch barbershop (cream/burgundy/gold, retro aesthetic, animated barber pole).
2. **Emma 3.0:** Local-first hybrid AI assistant with LangChain/RAG, compatible with local models and external services (electric blues, lens/blue-dot mark, technical interface).
3. **Emma Node:** The same functional Emma concept rebuilt with Node.js and React (Node green/React cyan, visually related to Emma 3.0).
4. **Aesthetic Store:** Frontend visual reference catalog for humans and AI agents (cyan/coral/lime, compact cards, visual-library feel).
5. **Santo Rosario:** Offline Android app for praying the Holy Rosary, built with vanilla HTML/CSS/JS and Capacitor (deep blue/parchment/gold, rosary icon, serene and readable for older users).
6. **AI Mascot:** Embeddable JavaScript AI mascot widget (green/turquoise/lime, friendly, small public API, smiling icon).
7. **Audiobook Generator TTS:** Local XTTS audiobook pipeline (violet/cyan/amber, audio-wave icon, long-form/ACX-oriented).
8. **NexusGrid:** Cyberpunk/high-tech visual system (blue/cyan, Share Tech Mono).
9. **SolTech:** Solar-tech fusion (orange/yellow/cyan, orbital solar icon).
10. **Verdant:** Organic/sustainable design system (greens/mint, leaf icon).
11. **Lumex:** Neon futurism (purple/cyan/amber, lightning icon).
12. **TalkingDutch:** Dutch institutional branding (red/white/blue/orange).
13. **Clara Nightwell:** Automated AI YouTube/content pipeline card (purple/pink/blue, generated-media icon).

## 4. Critical Component Status

| Component | Status | Notes |
| :--- | :--- | :--- |
| **Global Cursor** | Operational | Repeated across multiple files with color variations. |
| **Canvas background** | Optimized | Flash effects in `index.html` and `contact.html` are burst-scheduled; Lumex particles are FPS-limited. |
| **Contact form** | UI only | The frontend is robust, but still needs backend/service integration such as Formspree or Netlify Forms for real submissions. |
| **SEO / Meta** | Basic | OpenGraph tags and meta descriptions should eventually be standardized across all pages. |
| **PCAP Certification** | Visible | `index.html` links to `certificate_XkrV.RHDC.X8CV.pdf` from the secondary CTA below `Contact`. |

## 5. Current Main Portfolio State
- **Visible name:** The main hero and contact page use `Juan Carlos Diaz`; `Juan Carlos` stays white and `Diaz` keeps the blue/glitch gradient treatment.
- **Name responsiveness:** `index.html` and `contact.html` keep the name on one line via `white-space: nowrap` and targeted breakpoints to avoid horizontal overflow on narrow viewports. In `contact.html`, the `h1` uses a full-bleed band (`width: 100vw` plus `margin-left: calc(50% - 50vw)`) so the name centers against the viewport rather than the contact card width.
- **Hero CTAs:** On desktop, `Contact` and `PCAP Certification` appear below the bio. On narrow screens, both remain centered even when the hero text is left-aligned.
- **Grid order:** All portfolio cards remain in `index.html`. When the full grid is unlocked, they flow as 3 columns on desktop, 2 columns on tablet, and 1 column on mobile.
- **Hidden grid mode:** On initial load, `index.html` shows only the first 6 cards. If the user clicks the background 6 times within 20 seconds, `portfolio-unlocked` is added to `body`, revealing the remaining cards with the same staggered entrance animation and a canvas flash burst.
- **Refreshed legacy cards:** The cards that were hidden the longest (`NexusGrid`, `Lumex`, `TalkingDutch`, `SolTech`, `Verdant`, and `Clara Nightwell`) were updated to match the newer aesthetic: multi-accent backgrounds, decorative CSS icons, more refined pills, and improved contrast.
- **Privacy / location:** `index.html` and `contact.html` do not show a personal location. Any inherited visible reference to a previous city should be replaced with `Buenos Aires` and kept in English.
- **Animation performance:** The lightning/flash effect in `index.html` and `contact.html` no longer runs in a continuous `requestAnimationFrame` loop. It is scheduled in bursts, pauses when `document.hidden`, and respects `prefers-reduced-motion`.
- **Lumex:** `lumex.html` keeps its neon identity; the particle canvas is limited to 30fps, uses fewer particles, pauses on hidden tabs, and throttles the custom cursor through RAF.
- **SolTech:** `soltech_english.html` is visible in the main grid after unlock.
- **Verdant:** `verdant.html` is visible in the main grid after unlock.
- **NexusGrid:** `nexusgrid.html` is visible in the main grid after unlock.
- **Lighttown Barbershop:** The card links to `https://lighttown-barbershop.nl/` and presents the Dutch client site built with HTML, CSS, and JavaScript.
- **Emma Node:** The card links to `https://github.com/sistaterro/emma_node` and presents the Node.js/React rebuild of Emma.
- **Santo Rosario:** The card links to `https://github.com/sistaterro/santo_rosario` and presents the offline Android rosary app built with vanilla HTML/CSS/JS and Capacitor.
- **AI Mascot:** The card links to `https://github.com/sistaterro/ai_mascot` and is visible in the main grid after unlock.
- **TalkingDutch:** The card links to `https://talkingdutch.com/` and is visible in the main grid after unlock.
- **Audiobook Generator TTS:** The card links to `https://github.com/sistaterro/audiobook_generator_tts` and describes the local XTTS pipeline for turning narratable scripts into audiobook-ready WAV/MP3 output with curated voices, silence cleanup, merge, and ACX-style export.
- **Removed projects:** ForoBardo and CodeRisk AI were intentionally removed from the portfolio because those projects disappeared and should not be reintroduced unless the user explicitly asks.

## 6. Recommended Refactor Roadmap
1. **Extract assets:** Move inline `<style>` and `<script>` blocks into shared `.css` and `.js` files.
2. **Normalize analytics:** Centralize Google Tag Manager / Analytics snippets to avoid measurement drift between pages.
3. **Optimize images:** Ensure favicons and any future image assets use modern formats such as WebP/SVG where appropriate.
4. **Contact logic:** Add visual feedback such as toast notifications when users interact with contact forms.

---
*Updated to reflect the current portfolio state and recent implementation decisions.*
