# Portfolio Cloud

Static multi-page portfolio for Juan Carlos Díaz, built with HTML, CSS and vanilla JavaScript. The site uses a hub-and-spoke structure where `index.html` presents the main profile and links to individual project pages, each with its own visual identity.

Repository: https://github.com/sistaterro/portfolio_cloud

## Pages

- `index.html` - Main portfolio hub with project cards, contact CTA and PCAP certification link.
- `contact.html` - Contact card with copy-to-clipboard email interaction.
- `nexusgrid.html` - Cyberpunk/high-tech project page.
- `soltech_english.html` - Solar-tech project page, currently hidden from the main portfolio grid.
- `verdant.html` - Organic/sustainable energy project page, currently hidden from the main portfolio grid.
- `lumex.html` - Neon-futurist Dutch solar energy concept page.
- `talkingdutch.html` - Web design/cloud deploy project page.

## External Project Cards

- Aesthetic Store - Frontend visual reference catalog linked from the main portfolio grid.
- AI Mascot - Embeddable JavaScript mascot widget linked from the main portfolio grid.

## Assets

- `favicon.svg` and `favicon.ico` - Site icons.
- `certificate_XkrV.RHDC.X8CV.pdf` - PCAP certification PDF linked from the main hero.

## Local Usage

This project is fully static. Open `index.html` directly in a browser, or serve the folder with any static server.

Example:

```bash
python -m http.server 8000
```

Then visit:

```text
http://localhost:8000
```

## Implementation Notes

- No build step is required.
- Styles and scripts are currently inline per page.
- Animations use canvas, CSS keyframes and vanilla JavaScript.
- Main flash effects pause when the tab is hidden and respect `prefers-reduced-motion`.
- The contact and hero name layouts include narrow viewport breakpoints to avoid horizontal overflow.

## Maintenance Notes

See `AGENTS.md` for project structure, visual-system notes, current implementation decisions and recommended refactoring roadmap.
