# Vue Landing Page

**Live Demo:** [landing-vue-seven.vercel.app](https://landing-vue-seven.vercel.app/)

This project is a single-page landing website built with Vue 3, TypeScript, and Vite.

The page is split into reusable Vue sections and UI blocks:

- Header
- Hero section
- About company section
- Services section
- Why choose us section
- Special offers section
- Testimonials
- Call to action
- Contact section
- Footer
- Floating action button

## Tech Stack

- Vue 3
- TypeScript
- Vite
- Vue I18n
- Sass (SCSS in component styles)
- PrimeIcons
- Vuelidate (`@vuelidate/core`, `@vuelidate/validators`)

## Getting Started

Install dependencies:

```sh
npm install
```

Start the development server:

```sh
npm run dev
```

Build the project for production:

```sh
npm run build
```

Preview the production build locally:

```sh
npm run preview
```

## Localization (i18n)

- Locales are defined in `src/i18n/en.json` and `src/i18n/pl.json`.
- I18n bootstrap is configured in `src/i18n/index.ts` and initialized in `src/main.ts`.
- Language is switched from the header language switcher (`PL` / `EN`).
- Current default locale is `pl`.

Translated sections currently include:

- Header navigation
- Hero
- About company
- Why choose us
- Services
- Special offers
- Testimonials
- Call to action
- Contact
- Footer

## Available Scripts

- `npm run dev` starts the Vite development server.
- `npm run build` runs type checking and creates a production build.
- `npm run build-only` creates a production build without type checking.
- `npm run type-check` runs Vue TypeScript checks.
- `npm run preview` serves the built app locally for preview.

## Project Structure

```text
src/
  components/
  assets/
  main.ts
  App.vue
```

The main page layout is assembled in `src/App.vue`, where each landing-page section is imported as a separate component.

## Styling Notes

- Global design tokens are stored in `src/assets/main.css` under `:root`.
- Use `var(--color-...)` for direct color usage.
- For alpha colors, use RGB-channel variables with `rgba(var(--color-...-rgb), alpha)`.
  - Example: `rgba(var(--color-primary-rgb), 0.15)`

## Recommended Environment

- Node.js: `^20.19.0 || >=22.12.0`
- npm
- VS Code with the Vue Official extension

## Notes

- The project uses `vue-tsc` for type checking.
- Styling is configured with SCSS, PostCSS, and global CSS variables.
- The contact form uses Vuelidate for client-side validation; successful submit currently shows a temporary alert placeholder.
- The app is set up with Vite for fast local development and production builds.
