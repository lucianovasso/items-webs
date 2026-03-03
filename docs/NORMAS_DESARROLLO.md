# NORMAS DE DESARROLLO — items-web

## Principios

- Una sola página (`src/pages/index.astro`) hasta que haya necesidad real de más
- CSS inline en el `.astro` — sin preprocesadores
- Sin frameworks JS — Astro vanilla, interactividad con `<script>` nativo
- Visual 100% fiel al prototipo `items-v6.html`

## Commits

Formato convencional en inglés:
- `feat:` nueva funcionalidad
- `fix:` corrección de bug
- `refactor:` cambio sin impacto visual
- `docs:` cambios en documentación
- `chore:` configuración, deps

Ejemplo: `feat: add contact form with whatsapp redirect`

## Branches

- `main` — rama principal, deploy automático a Cloudflare Pages
- Feature branches para cambios grandes: `feat/nueva-seccion`

## Assets

- Logos SVG inline en el HTML (no archivos externos)
- Imágenes en `public/` si se agregan
- Fuentes via Google Fonts CDN

## CSS

- Variables en `:root` y `[data-theme="light"]`
- No cambiar los tokens de color sin actualizar el manual de marca
- Prefijo `--` para todas las variables

## Lo que NO hacer

- No agregar dependencias de UI (Tailwind, Bootstrap, etc.)
- No agregar frameworks JS (React, Vue, etc.) salvo decisión explícita
- No modificar el visual sin validar con el prototipo aprobado
