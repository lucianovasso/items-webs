# items-web

Sitio web de **items.com.ar** — estudio contable automatizado de Jessica Baptista.

## Setup

```bash
npm install
npm run dev      # localhost:4321
npm run build    # genera dist/
npm run preview  # preview del build
```

## Deploy

Cloudflare Pages — deploy automático desde `main` en GitHub.
Build command: `npm run build`
Output directory: `dist`

## Stack

- Astro (SSG)
- CSS vanilla con custom properties
- Chakra Petch (Google Fonts) + Courier New

## Convención de código

Ver `docs/NORMAS_DESARROLLO.md`
