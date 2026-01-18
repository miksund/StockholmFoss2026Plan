# CLAUDE.md

This file provides guidance to Claude Code when working with the StockholmFoss 2026 website.

## Project Overview

StockholmFoss 2026 is a Jekyll-based static site for a fictional Nordic open source conference. The site is deployed to GitHub Pages at:

**Live URL:** https://miksund.github.io/StockholmFoss2026Plan/

## Tech Stack

- **Static Site Generator:** Jekyll 4.3+
- **Hosting:** GitHub Pages
- **Styling:** Custom CSS (no preprocessor needed for GitHub Pages)
- **JavaScript:** Minimal vanilla JS for tab filtering only

## Project Structure

```
StockholmFoss/
├── _config.yml              # Jekyll configuration (baseurl, collections, sponsors)
├── _layouts/
│   ├── default.html         # Base HTML structure with CSS variables
│   ├── page.html            # Standard content pages
│   └── speaker.html         # Individual speaker profile pages
├── _includes/
│   ├── header.html          # Navigation with mobile hamburger menu
│   ├── footer.html          # Sponsors and contact info
│   └── schedule-track.html  # Reusable schedule component
├── _speakers/               # Jekyll collection (52 speaker files)
│   └── *.md                 # Speaker front matter (name, bio, talk info)
├── assets/css/
│   └── style.css            # All styles (~650 lines, Nordic minimal theme)
├── index.md                 # Home page
├── schedule.md              # Full conference schedule
├── speakers.md              # Speaker grid with filtering
├── practical.md             # Venue, CoC, accessibility info
├── Gemfile                  # Jekyll dependencies
├── STOCKHOLMFOSS_2026_SCHEDULE.md  # Source schedule data (excluded from build)
└── speakers/                # Original speaker profiles (excluded from build)
```

## Development Commands

```bash
# Install dependencies (first time only)
bundle install

# Run local development server
bundle exec jekyll serve

# Build for production
bundle exec jekyll build

# Local server with live reload
bundle exec jekyll serve --livereload
```

Local site runs at: http://localhost:4000/StockholmFoss2026Plan/

## Important Configuration

### baseurl Setting

The site is deployed to a subdirectory, so `_config.yml` must have:

```yaml
baseurl: "/StockholmFoss2026Plan"
url: "https://miksund.github.io"
```

**Critical:** All internal links must use `| relative_url` filter:
```liquid
<a href="{{ '/schedule/' | relative_url }}">Schedule</a>
<link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}">
```

### Speaker Collection

Speakers are defined in `_speakers/*.md` with front matter:

```yaml
---
name: "Speaker Name"
title: "Job Title | Company"
location: "City, Sweden"
github: "github.com/username"
mastodon: "@user@instance"
bio: "Short biography for display"
track: "Main"  # Main, Infrastructure, Development, Community, Nordic Focus, Lightning, Keynote, Organizer
talk_title: "Talk Title"
talk_time: "11:00"
talk_room: "Aula Magna"
keynote: true  # Optional, only for keynote speakers
---
```

## Design System

### Colors (CSS Variables)

```css
--primary: #1a365d;       /* Deep blue - headers, buttons */
--primary-light: #2c5282; /* Lighter blue - hover states */
--secondary: #e2e8f0;     /* Light gray - cards, backgrounds */
--accent: #3182ce;        /* Links */
--text: #1a202c;          /* Body text */
--text-muted: #4a5568;    /* Secondary text */
```

### Track Badge Colors

- Keynote/Main: `#1a365d` (deep blue)
- Infrastructure: `#2c5282`
- Development: `#2b6cb0`
- Community: `#38a169` (green)
- Nordic Focus: `#0077b6`
- Lightning: `#d69e2e` (gold)

### Speaker Avatars

Avatars are CSS-generated circles with initials:
```liquid
{{ speaker.name | split: ' ' | map: 'first' | join: '' | upcase | truncate: 2, '' }}
```

## Common Tasks

### Adding a New Speaker

1. Create `_speakers/firstname-lastname.md` with front matter
2. Add talk info to `schedule.md` if presenting
3. The speaker will automatically appear in the speakers grid

### Updating the Schedule

Edit `schedule.md` directly. The schedule uses HTML within markdown for the timeline layout.

### Changing Sponsors

Edit the `sponsors` section in `_config.yml`:

```yaml
sponsors:
  platinum:
    - name: "Sponsor Name"
      url: "https://sponsor.com"
```

### Modifying Styles

All styles are in `assets/css/style.css`. Key sections:
- Lines 1-100: Header & Navigation
- Lines 100-200: Page Layouts
- Lines 200-350: Speaker Cards & Profiles
- Lines 350-500: Schedule & Timeline
- Lines 500-600: Footer & Utilities

## Deployment

The site auto-deploys via GitHub Pages when pushing to `main`. Build takes ~1-2 minutes.

To verify deployment:
1. Go to repository Settings > Pages
2. Check "Your site is live at..." message
3. Hard refresh browser (Cmd+Shift+R) if CSS looks stale

## Source Data

Original content is preserved but excluded from the Jekyll build:

- `STOCKHOLMFOSS_2026_SCHEDULE.md` - Full schedule in markdown
- `speakers/*.md` - Detailed speaker profiles (52 files)

The `_speakers/` collection contains simplified front-matter versions for Jekyll.

## Troubleshooting

### CSS Not Loading
- Check `baseurl` in `_config.yml` matches repository name
- Verify `| relative_url` filter on stylesheet link
- Hard refresh browser to clear cache

### Speaker Pages 404
- Ensure file is in `_speakers/` (not `speakers/`)
- Check front matter has `---` delimiters
- Verify `collections.speakers.output: true` in config

### Local Build Fails
- Run `bundle install` to ensure dependencies
- Check for YAML syntax errors in front matter
- Verify no tabs in YAML (use spaces only)
