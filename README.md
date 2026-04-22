# Vue Landing Page

**Live Demo:** [landing-vue-seven.vercel.app](https://landing-vue-seven.vercel.app/)

This project is a single-page landing website built with Vue 3, TypeScript, Vite, and Tailwind CSS.

It is structured as a modular set of reusable sections and UI blocks, including:

- Header
- Hero section
- About company section
- Services section
- Additional about section
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
- Tailwind CSS
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

## Available Scripts

- `npm run dev` starts the Vite development server.
- `npm run build` runs type checking and creates a production build.
- `npm run build-only` creates a production build without type checking.
- `npm run type-check` runs Vue TypeScript checks.
- `npm run preview` serves the built app locally for preview.
- `npm run server` starts `json-server` on port 3000.

## Project Structure

```text
src/
  components/
  assets/
  main.ts
  App.vue
```

The main page layout is assembled in `src/App.vue`, where each landing-page section is imported as a separate component.

## Recommended Environment

- Node.js: `^20.19.0 || >=22.12.0`
- npm
- VS Code with the Vue Official extension

## Notes

- The project uses `vue-tsc` for type checking.
- Styling is configured with Tailwind CSS and PostCSS.
- The app is set up with Vite for fast local development and production builds.
