# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Folex Lite is an Astro 5 + Tailwind CSS 4 theme for creative agencies and portfolios. It uses TOML-based configuration, supports multilingual content, and follows a component-based architecture.

## Commands

```bash
# Development
pnpm dev              # Start dev server at localhost:4321
pnpm run build        # Check types, build, and remove drafts from sitemap
pnpm run check        # Run Astro type checking
pnpm run preview      # Build and preview production site

# Formatting
pnpm run format       # Format code with Prettier

# Utilities
pnpm run generate-favicons         # Generate favicons from config favicon image
pnpm run remove-multilingual       # Remove multilingual content (keep English only)
pnpm run remove-draft-from-sitemap # Clean draft pages from sitemap (runs automatically on build)
```

**Package Manager:** This project uses `pnpm@8.15.5` as specified in package.json. Do not use npm or yarn.

**Node.js Versions:** Supports Node.js >=18.20.8 <19 || >=20.3.0 <21 || >=22.0.0

## Configuration Architecture

### TOML-Based Configuration

The entire site is configured via `src/config/config.toml`, which is parsed at build time by `src/lib/utils/tomlUtils.ts`. The TOML file is cached in memory for performance.

**Key configuration sections:**
- `[site]` - Base URL, logo, trailing slash behavior, favicon settings
- `[seo]` - Author, keywords, robots.txt, sitemap settings
- `[settings]` - Content folder names, sticky header, contact form, multilingual settings
- `[settings.multilingual]` - Enable/disable i18n, default language, language visibility in URLs
- `[opengraph]` - Open Graph and Twitter Card metadata
- `[head]` - Custom scripts/styles to inject into <head>

**Important:** When changing `trailingSlash`, `multilingual` settings, or folder names, you must manually restart the dev server.

**Hot Reload:** The TOML file has a custom Vite plugin (`reloadOnTomlChange`) that triggers a full page reload when config.toml changes.

### Path Aliases

TypeScript path aliases are defined in `tsconfig.json`:
- `@/*` → `./src/*`
- `@/components/*` → `./src/layouts/components/*`
- `@/shortcodes/*` → `./src/layouts/shortcodes/*`
- `@/helpers/*` → `./src/layouts/helpers/*`

## Content Architecture

### Content Collections

Content collections are defined in `src/content.config.ts` using Astro's Content Layer API with Zod schemas.

**Collections:**
- `pages` - General pages (privacy, terms, etc.)
- `sections` - Reusable homepage sections (banner, services, pricing, etc.)
- `homepage` - Homepage-specific content organized by language
- `services` - Service items (folder name configurable via `settings.servicesFolder` in config.toml)
- `portfolio` - Portfolio/project items (folder name configurable via `settings.portfolioFolder` in config.toml)

**Content Organization:**
- Content is organized by language directories: `english/`, `french/`
- Each language directory structure mirrors the collection structure
- Frontmatter schemas are defined in `src/content.config.ts` and `src/content/sections.schema.ts`

### Multilingual (i18n) System

**Language Configuration:**
- Languages are defined in `src/config/language.json` with `languageCode` and `contentDir` mappings
- Menu translations: `src/config/menu.{lang}.json`
- UI translations: `src/i18n/{lang}.json`

**URL Generation:**
- `src/lib/utils/i18nUtils.ts` handles all i18n logic
- `getLocaleUrlCTM()` generates localized URLs based on config settings
- `useTranslations()` provides translation function `t(key)` with dot notation for nested keys
- Default language can be shown/hidden in URLs via `showDefaultLangInUrl` config

**Key i18n utilities:**
- `enabledLanguages` - List of active language codes (respects `disableLanguages` config)
- `supportedLanguages` - Full language objects for enabled languages
- `generatePaths()` - Generates static paths for all language variants
- `getLocaleUrlCTM(url, lang, prependValue?)` - Converts URLs to localized versions

**Routing:**
- Astro's i18n routing is configured in `astro.config.mjs` based on TOML settings
- Pages use `[...lang]` dynamic routes to handle multiple languages

## Key Utilities

### TOML Parsing
- `parseTomlToJson()` in `src/lib/utils/tomlUtils.ts` - Cached parser for config.toml
- Automatically removes empty keys from parsed config

### Content Utilities
- `remarkParseContent.ts` - Custom remark plugin for parsing content sections
- `filteredEnabled.ts` - Filters content items based on `enable` flag
- `extractSlug.ts` - Extracts slugs from content entries
- `textConverter.ts` - Converts markdown to plain text

### SEO Utilities
- `JsonLdGenerator.ts` - Generates JSON-LD structured data
- Components in `src/layouts/components/seo/` handle meta tags, OpenGraph, favicons

### Form Handling
- `HandleForm.ts` supports multiple providers: Formspree, Formsubmit.co, Netlify
- Provider is configured via `settings.contactFormProvider` in config.toml

## Layout Structure

**Base Layout:** `src/layouts/Base.astro` - Main layout wrapper with Head, Header, Footer

**Components:**
- `src/layouts/components/global/` - Header, Footer, Logo, Navigation
- `src/layouts/components/sections/` - Reusable section components (Banner, Services, Portfolio, etc.)
- `src/layouts/components/widgets/` - Utility widgets (ContactForm, Breadcrumbs, JsonLD, etc.)
- `src/layouts/components/cards/` - Card components for portfolio and pricing
- `src/layouts/components/seo/` - SEO-related components

**Helper Components:**
- `src/layouts/helpers/ReactIcons.astro` - Renders React Icons dynamically

## Image Handling

- Uses Astro's built-in image optimization with Sharp
- `OptimizedImage.astro` - Wrapper component for responsive images
- `bgOptimizedImage.ts` - Generates optimized background image CSS

## Styling

- **Tailwind CSS 4** via `@tailwindcss/vite` plugin
- Preline UI components for accordions, overlays, select, collapse
- AOS (Animate On Scroll) for scroll animations
- Custom styles in `src/styles/`

## Scripts

Three utility scripts in `scripts/`:
1. `generate-favicons.mjs` - Generates favicons from the image specified in config.toml
2. `remove-draft-from-sitemap.mjs` - Removes draft pages from the generated sitemap
3. `remove-multilingual.mjs` - Removes all non-English content, menus, and i18n files

## Development Notes

- **Server Restart Required:** Changes to `trailingSlash`, multilingual settings, or content folder names in config.toml require manual server restart
- **Content Folder Names:** When changing `servicesFolder` or `portfolioFolder` in config.toml, you must also rename the corresponding folders in `src/content/` and update collection references
- **TypeScript:** Project uses strict mode with Astro's strict tsconfig
- **Content Queries:** Use Astro's `getCollection()` and `getEntry()` APIs to fetch content
- **Draft Content:** Pages with `draft: true` in frontmatter are excluded from production sitemap
