# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Architecture Overview

This is a Hugo static site blog using the Typo theme. The site includes:

- **Content Management**: Uses Decap CMS (formerly Netlify CMS) for content editing via `/admin/` interface
- **Theme**: Typo theme located in `themes/typo/`
- **Content Structure**: Blog posts in `content/posts/` with year/month/day folder structure
- **Static Assets**: Images and other assets in `static/images/`
- **Generated Site**: Built output in `public/` directory

## Essential Commands

### Development

- `hugo server -D` - Start development server with drafts included
- `hugo server --buildDrafts --buildFuture` - Development server including drafts and future posts
- `hugo` - Build the static site to `public/` directory
- `hugo new posts/YYYY/MM/DD/post-title.md` - Create new blog post with proper structure

### Content Management

- Posts are managed via Decap CMS at `/admin/` when deployed
- Configuration for CMS is in `static/admin/config.yml`
- Posts use frontmatter with title, date, categories, tags, and draft status

## Site Configuration

- Main config: `hugo.yaml`
- Base URL: https://cstalhem.github.io
- Permalink structure: `/posts/:year/:month/:day/:slug`
- Theme: Typo with customizations
- CMS Backend: GitHub with repository `cstalhem/cstalhem.github.io`

## Content Structure

- Posts are organized by date: `content/posts/YYYY/MM/DD/`
- Tags are managed as a separate collection via CMS
- Categories are limited to one per post
- Images stored in `static/images/` and referenced as `/images/filename`

## Deployment

Site is deployed to GitHub Pages at https://cstalhem.github.io from the main branch.
