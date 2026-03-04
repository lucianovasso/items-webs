# CONVENCION DE CODIGO — items-web

**Versión:** 1.0  
**Fecha:** Marzo 2026

---

## Regla Principal

> **Código en inglés, comunicación en español.**

---

## Commits

Formato convencional en inglés:

| Tipo | Uso |
|------|-----|
| `feat:` | nueva funcionalidad o sección |
| `fix:` | corrección de bug |
| `refactor:` | cambio sin impacto visual o funcional (incluye copy) |
| `style:` | ajuste visual / CSS |
| `docs:` | cambios en documentación |
| `chore:` | configuración, dependencias |

Ejemplos:
```
feat: add testimonials section
fix: mobile nav not closing on scroll
refactor: update hero headline copy
style: adjust hero title letter-spacing on mobile
docs: update NORMAS_DESARROLLO with commit types
chore: upgrade astro to v4.1
```

---

## HTML / Astro

| Elemento | Idioma | Ejemplo |
|----------|--------|---------|
| IDs y clases CSS | Inglés | `hero-title`, `nav-cta`, `section-label` |
| Variables JS | Inglés | `themeToggle`, `mobileMenu`, `savedTheme` |
| Funciones JS | Inglés | `toggleTheme()`, `closeMobileMenu()` |
| Atributos `data-*` | Inglés | `data-theme="dark"`, `data-section` |
| Comentarios de sección | Español | `<!-- HERO -->`, `<!-- SERVICIOS -->` |
| Comentarios JS | Español | `// cerrar menú al hacer scroll` |
| Texto visible al usuario | Español | `"Escribir por WhatsApp"`, `"Cómo funciona"` |
| Nombres de archivos | Inglés | `index.astro`, `NORMAS_DESARROLLO.md` |

---

## CSS

| Elemento | Idioma | Ejemplo |
|----------|--------|---------|
| Custom properties | Inglés | `--bg`, `--accent`, `--border-2` |
| Nombres de clases | Inglés | `.hero-title`, `.servicio-card`, `.dif-cell` |
| Comentarios de bloque | Español | `/* ── HERO ── */` |
| Valores semánticos | Inglés | `var(--text)`, `var(--muted)` |

---

## JavaScript

| Elemento | Idioma | Ejemplo |
|----------|--------|---------|
| Variables y constantes | Inglés | `const nav`, `const saved` |
| Funciones | Inglés | `toggleTheme()`, `closeMobileMenu()` |
| Event listeners | Inglés | `'click'`, `'scroll'` |
| Keys de localStorage | Inglés | `'items-theme'` |
| Comentarios | Español | `// aplicar tema guardado` |

---

## Ejemplos

### ✅ Correcto

```html
<!-- HERO -->
<section class="hero" id="inicio">
  <h1 class="hero-title">
    Sin carga manual<span>.</span><br>
    Con criterio profesional<span>.</span>
  </h1>
</section>
```

```javascript
// aplicar tema guardado al cargar
const saved = localStorage.getItem('items-theme') || 'dark';
function toggleTheme() {
  const current = root.getAttribute('data-theme');
  const next = current === 'light' ? 'dark' : 'light';
  root.setAttribute('data-theme', next);
  localStorage.setItem('items-theme', next);
}
```

```css
/* ── HERO ── */
.hero-title {
  font-family: var(--mono);
  font-size: clamp(2.7rem, 7.2vw, 6.3rem);
  color: var(--text);
}
```

### ❌ Incorrecto

```html
<!-- seccion hero -->              <!-- ❌ comentario en minúscula y español mezclado -->
<section class="seccion-hero">    <!-- ❌ clase en español -->
```

```javascript
// apply saved theme on load      // ❌ comentario en inglés
const guardado = localStorage.getItem('items-theme');  // ❌ variable en español
function cambiarTema() { ... }    // ❌ función en español
```

---

## Lo que NO hacer

- No usar clases CSS en español
- No nombrar variables o funciones JS en español
- No mezclar idiomas en el mismo nombre (`hero-titulo`, `navCerrar`)
- No escribir comentarios de sección en inglés
- No usar tipos de commit fuera de la tabla

---

*items-web — Documentación Técnica*
