# Mona Mayhem - AI Agent Instructions

## Project Overview

A retro arcade-themed Astro website that compares GitHub contribution graphs between two users. Built as a workshop template using **Astro v5** with server-side rendering.

**Tech Stack:**
- Framework: Astro v5 (SSR mode)
- Runtime: Node.js with `@astrojs/node` adapter (standalone mode)
- API: GitHub contribution graph endpoint

## Commands

```bash
npm run dev      # Start dev server
npm run build    # Build for production
npm run preview  # Preview production build
```

## Astro Best Practices

### Server-Side Rendering
- Project uses `output: 'server'` — all pages are rendered on-demand
- API routes must include `export const prerender = false;` at the top

### API Routes
- API endpoints go in `src/pages/api/`
- Use TypeScript `APIRoute` type for handlers
- Example pattern:
  ```typescript
  import type { APIRoute } from 'astro';
  
  export const prerender = false;
  
  export const GET: APIRoute = async ({ params, request }) => {
    return new Response(JSON.stringify(data), {
      headers: { 'Content-Type': 'application/json' }
    });
  };
  ```

### Component Best Practices
- Use `.astro` components for templating
- Frontmatter (code between `---`) runs at build time (or request time in SSR)
- Keep client-side JavaScript minimal and explicit with `<script>` tags
- For interactive components, consider framework integrations or vanilla JS

### File-Based Routing
- `src/pages/` maps to routes automatically
- `[param].astro` or `[param].ts` for dynamic routes
- Access route params via `Astro.params` in `.astro` or `params` in API routes

## Important Notes

- **Ignore `workshop/` directory** — it contains tutorial documentation, not application code
- The main application lives in `src/pages/`
- Public assets go in `public/`
- Documentation HTML files in `docs/` are separate from the Astro app
