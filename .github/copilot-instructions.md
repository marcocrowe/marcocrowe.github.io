# Jekyll DevLopr Theme - Developer Guide

## Project Overview

This is a personal portfolio website for Mark Crowe built on Jekyll using the DevLopr theme - a developer-focused theme with built-in blogging, project showcase, and multi-author support capabilities.

## Architecture & Structure

### Core Configuration

- **Main config**: `_config.yml` - Contains site metadata, navigation, author details, and feature toggles
- **Deployment strategy**: `DEPLOY_STRATEGY` file controls CI/CD target (`none`, `gh-pages`, or `firebase`)
- **Build output**: Generated site goes to `./build` directory (not standard `_site`)

### Content Organization

- **Posts**: `_posts/` using YYYY-MM-DD-title.md naming convention
- **Authors**: `_authors/` markdown files + `_data/authors.yml` for multi-author support  
- **Products**: `_products/` for shop/portfolio items
- **Pages**: Root-level `.md` files (about.md, contact.md, etc.)

### Theme Structure

- **Layouts**: `_layouts/` - Inherits from `compress.html` → `default.html` → specific layouts
- **Includes**: `_includes/` - Modular components (header, footer, blog sidebar, etc.)
- **Assets**: `assets/` contains Bower components, images, CSS/SCSS, and JavaScript

## Key Development Patterns

### Post Front Matter Template

```yaml
---
layout: post
title: "Post Title"
date: 2020-11-21 17:32
category:
- Software Development
- Java
author: markcrowe  # Must match _data/authors.yml key
keywords: Java, Tools, Utilities
summary: Brief description for SEO/social
thumbnail: /assets/img/posts/image.jpg
permalink: /blog/custom-url/
tags:
- tag1
- tag2
---
```

### Author System

- Add authors to `_data/authors.yml` with social links and bio
- Create corresponding `_authors/username.md` files
- Reference by username in post front matter

### Feature Toggles in _config.yml

```yaml
show_author_work_experiences: true
show_author_education_details: true  
show_author_project_details: true
```

## Development Workflow

### Local Development

```bash
# Install dependencies
bundle install

# Development server with live reload
bundle exec jekyll serve --livereload
# Serves at http://localhost:4000

# Admin interface (if jekyll-admin plugin enabled)
# Access at http://localhost:4000/admin
```

### Docker Development

```bash
# Development mode
docker-compose -f docker-compose-dev.yml up --build

# Production mode  
docker-compose -f docker-compose-prod.yml up --build
```

### Deployment

- **Strategy controlled by**: `DEPLOY_STRATEGY` file content
- **GitHub Actions**: `.github/workflows/deploy.yml` handles CI/CD
- **Firebase**: Requires `FIREBASE_TOKEN` and `FIREBASE_PROJECT_ID` secrets
- **GitHub Pages**: Uses `sujaykundu777/jekyll-deploy-action@1.0.5`

## Theme-Specific Features

### Navigation

- Configured in `_config.yml` under `urls:` array
- Mix of internal paths and external URLs
- GitHub link included for developer portfolios

### Content Collections

- **Products**: E-commerce/portfolio items in `_products/`
- **Authors**: Multi-author blog support
- **Gallery**: Special permalink structure for media

### Integrated Services

- **Analytics**: Wakatime coding activity (`wakatime_username`)
- **Comments**: Disqus or Hyvor Talk support
- **Newsletter**: Mailchimp integration
- **E-commerce**: Snipcart integration for selling products
- **CMS**: Netlify CMS admin interface

## Important Files to Modify

- `_config.yml` - Primary configuration and content
- `_data/authors.yml` - Author information
- `DEPLOY_STRATEGY` - Controls deployment target
- `assets/img/` - Images and media assets
- `_sass/devlopr.scss` - Theme styling customization

## Common Tasks

- **New blog post**: Create in `_posts/` with proper front matter
- **Add author**: Update `_data/authors.yml` and create `_authors/username.md`
- **Navigation change**: Modify `urls:` in `_config.yml`
- **Deploy strategy**: Update `DEPLOY_STRATEGY` file content
- **Theme customization**: Modify files in `_sass/` directory
