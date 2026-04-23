# Vue Landing Page

Single-page landing website built with Vue 3, TypeScript, and Vite.

Live demo: [landing-vue-seven.vercel.app](https://landing-vue-seven.vercel.app/)

## Features

- Component-based page structure (header, hero, services, contact, etc.)
- Multilingual UI with Vue I18n (Polish and English)
- Header language switcher (PL / EN)
- Light and dark theme switcher with icon toggle
- Theme persistence in localStorage
- Initial theme detection from system preference (`prefers-color-scheme`)
- Contact form validation with Vuelidate
- SCSS component styles + global CSS design tokens
- PrimeIcons integration

## Page Sections

- Header
- Hero
- About company
- Services
- Why choose us
- Special offers
- Testimonials
- Call to action
- Contact
- Footer
- Floating action button

## Tech Stack

- Vue 3
- TypeScript
- Vite
- Vue I18n
- Vuelidate (`@vuelidate/core`, `@vuelidate/validators`)
- Sass (SCSS in component styles)
- PrimeIcons
- PostCSS
- Tailwind CSS (installed in tooling)

## Getting Started

Install dependencies:

```sh
npm install
```

Run development server:

```sh
npm run dev
```

Build for production (with type checking):

```sh
npm run build
```

Preview production build:

```sh
npm run preview
```

## Available Scripts

- `npm run dev` - start Vite dev server
- `npm run build` - type check + production build
- `npm run build-only` - production build only
- `npm run type-check` - run `vue-tsc`
- `npm run preview` - preview built app

## Localization (i18n)

- Locale messages are in `src/i18n/en.json` and `src/i18n/pl.json`
- I18n setup is in `src/i18n/index.ts`
- Default locale is `pl`
- UI locale is switched from header buttons (`PL` / `EN`)

## Theme System

- Global color tokens are defined in `src/assets/main.css`
- Theme is controlled via `data-theme` on the root HTML element
- Dark theme palette is defined under `:root[data-theme='dark']`
- Current theme is stored in browser localStorage

## Form Validation

- Contact form uses Vuelidate for client-side validation
- Required fields: first name, last name, phone, email
- Email format and minimum lengths are validated
- Validation messages are translated via Vue I18n

## Project Structure

```text
src/
  assets/
    main.css
  components/
    Header.vue
    Hero.vue
    AboutCompany.vue
    Services.vue
    About.vue
    SpecialOffers.vue
    Testimonial.vue
    Cta.vue
    Contact.vue
    Footer.vue
    FloatingButton.vue
  i18n/
    index.ts
    en.json
    pl.json
  App.vue
  main.ts
```

## Environment

- Node.js: `^20.19.0 || >=22.12.0`
- npm
- VS Code + Vue Official extension (recommended)
