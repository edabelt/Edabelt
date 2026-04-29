# Ever Beltrán

Bilingual personal portfolio built with SvelteKit.

This project is a minimalist personal website designed to present professional work across software development, writing, and research. It includes English and Spanish versions of the site and is structured as a lightweight content-first portfolio focused on clarity, readability, and maintainable front-end architecture.

## Overview

The site serves as a personal portfolio and publication space, combining:

- technical projects
- writing and research
- academic and professional background
- bilingual navigation (English / Spanish)

Rather than functioning as a blog or template-heavy portfolio, the site is designed as a clean editorial interface with emphasis on content hierarchy, typographic consistency, and lightweight performance.

## Built With

- **SvelteKit** — application framework
- **Svelte 5** — component architecture
- **Bulma** — layout and responsive UI structure
- **CSS** — custom editorial styling
- **Netlify Adapter** — deployment target

## Features

- bilingual routing (`/` and `/es`)
- custom editorial homepage
- portfolio project archive
- writing archive with structured categories
- academic CV (HTML + downloadable PDF)
- responsive layout
- lightweight static asset delivery

## Structure

```bash
src/routes/
├── about
├── contact
├── cv
├── projects
├── writing
└── es/
    ├── about
    ├── contact
    ├── cv
    ├── projects
    └── writing