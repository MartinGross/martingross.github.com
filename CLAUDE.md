# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based blog (DATA ZOO) hosted on GitHub Pages using the Minimal Mistakes theme. The site is built with Jekyll 2.x and uses Sass for styling.

## Build and Development Commands

### Jekyll Commands
```bash
# Build the site
bundle exec jekyll build

# Serve the site locally (typically at http://localhost:4000)
bundle exec jekyll serve

# Serve with drafts visible
bundle exec jekyll serve --drafts
```

### Grunt Commands (for asset optimization)
```bash
# Install dependencies first
npm install

# Default build task (clean, uglify JS, optimize images)
grunt

# Watch mode for development (watches JS changes, runs jshint and uglify)
grunt dev
```

## Architecture

### Content Structure
- **Blog posts**: `_posts/` - Markdown/Textile files with YYYY-MM-DD prefix
- **Draft posts**: `_drafts/` - Posts not yet published
- **Static pages**: Root level `.md` files (about, index, posts)

### Theme Components
- **Layouts**: `_layouts/` (home, page, post, post-index)
- **Includes**: `_includes/` (reusable components like _head.html, _footer.html, _author-bio.html)
- **Data files**: `_data/` (authors.yml, navigation.yml)
- **Styles**: `_sass/` (Sass partials, compiled via Jekyll)
- **Assets**: `assets/` (JS, images, fonts)

### JavaScript Build Process
JavaScript files are concatenated and minified via Grunt:
- Source: `assets/js/plugins/*.js` and `assets/js/_*.js`
- Output: `assets/js/scripts.min.js`

### Configuration
- **Main config**: `_config.yml` - Site title, owner info, Jekyll settings, social media links
- **URL structure**: `//www.datazoo.de`
- **Permalink format**: `/:categories/:title/`
- **Markdown**: kramdown with pygments syntax highlighting
- **Analytics**: Google Analytics (G-H7GFKNNBPK)

### Key Settings
- Site uses protocol-relative URLs (`//www.datazoo.de`)
- Disqus comments enabled (shortname: datazoo)
- Jekyll sitemap plugin enabled

## Git Repository Structure

### Branches
- **master**: Active development branch (deployed to GitHub Pages)
- **origin/gh-pages**: Legacy branch (deprecated, not actively used)

### Remote Repositories
- **origin**: `https://github.com/MartinGross/martingross.github.com.git`
- **upstream**: `https://github.com/mmistakes/minimal-mistakes.git` (Original Minimal Mistakes theme)

### Upstream Branches (Reference Only)
The following upstream branches are from the original Minimal Mistakes theme repository and are not actively used:
- `upstream/master`: Current theme development
- `upstream/gh-pages-2.2.1`, `upstream/gh-pages-3.1.6`: Old theme versions
- `upstream/flexbox-sticky-footer`, `upstream/navbar-menu`: Feature branches

**Note**: This site uses `master` branch for GitHub Pages (standard for user page repositories). The `origin/gh-pages` branch is outdated and no longer maintained.