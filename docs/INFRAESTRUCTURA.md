# INFRAESTRUCTURA WEB — items.com.ar

**Versión:** 1.0
**Fecha:** Marzo 2026

---

## Resumen

| Componente | Servicio | URL |
|------------|----------|-----|
| Web principal | Cloudflare Pages | items.com.ar / www.items.com.ar |
| Documentación / artefactos | Cloudflare Pages | docs.items.com.ar |
| DNS | Cloudflare | luke.ns.cloudflare.com / nena.ns.cloudflare.com |
| Correo | Donweb + Amazon SES | — |
| Registro de dominio | NIC.ar | items.com.ar |

---

## Repositorios

| Proyecto | Repo GitHub | Cloudflare Pages |
|----------|-------------|------------------|
| Web principal | lucianovasso/items-web | items-web |
| Docs / artefactos | lucianovasso/items-docs | items-docs |

---

## DNS — Cloudflare

Nameservers activos en NIC.ar:
```
luke.ns.cloudflare.com
nena.ns.cloudflare.com
```

### Registros críticos

| Tipo | Nombre | Destino | Proxy | Notas |
|------|--------|---------|-------|-------|
| A | items.com.ar | 200.58.112.119 | ON | Donweb (fallback) |
| A | mail | 200.58.112.119 | OFF | Servidor de correo |
| A | mx1 | 200.58.122.206 | OFF | Servidor de correo secundario |
| A | mipanel | 200.58.109.42 | OFF | Panel Donweb |
| MX | items.com.ar | mail.items.com.ar (0) | — | Correo principal |
| MX | items.com.ar | mx1.items.com.ar (20) | — | Correo secundario |
| MX | mail | feedback-smtp.us-east-1.amazonses.com (10) | — | Amazon SES |
| CNAME | www | items.com.ar | ON | Web principal |
| CNAME | docs | items.com.ar | OFF | Docs (ahora → Pages) |
| CNAME | qr | cname.qrcodechimp.com | OFF | QR codes |
| CNAME | 3× _domainkey | →amazonses.com | OFF | DKIM Amazon SES |
| TXT | items.com.ar | v=spf1 include:spf.hostmar.com | — | SPF Donweb |
| TXT | _dmarc | v=DMARC1; p=reject | — | DMARC |
| TXT | _amazonses | f0lqmvd2y… | — | Verificación SES |
| TXT | mail._domainkey | v=DKIM1; g=*; k=rsa | — | DKIM Donweb |

> **Importante:** Los registros de correo (MX, SPF, DKIM, DMARC) no deben modificarse.
> El correo sigue siendo gestionado por Donweb + Amazon SES.

---

## Web principal — items-web

- **Stack:** Astro + CSS vanilla
- **Deploy:** automático en cada push a `main`
- **Dominios:** items.com.ar y www.items.com.ar
- **Repo local:** `E:\drive\proyectos\webs-items\04_desarrollo\items-web`

---

## Docs / artefactos — items-docs

- **Contenido:** HTMLs estáticos y assets de imagen para compartir con clientes
- **Deploy:** automático en cada push a `main`
- **Dominio:** docs.items.com.ar
- **Repo local:** `E:\drive\proyectos\_publicaciones`
- **Excluidos del repo** (ver `.gitignore`): `_respaldo/`, `*.mp4`, `*.xlsx`, `interno/`, archivos de sistema

### Workflow para publicar un artefacto

```bash
cd E:\drive\proyectos\_publicaciones   # o desde WSL: /mnt/e/drive/proyectos/_publicaciones
git add .
git commit -m "feat: add [nombre del artefacto]"
git push
```

Cloudflare Pages despliega automáticamente. El artefacto queda disponible en:
```
https://docs.items.com.ar/[carpeta]/[archivo].html
```

Ejemplo:
```
https://docs.items.com.ar/cte/tienda-cte-v4.html
https://docs.items.com.ar/cth/propuesta-ecosistema-digital.html
```

---

## AI Readiness — LLM Resource

El sitio está configurado para ser citado como fuente primaria por modelos de IA (ChatGPT, Claude, Perplexity).

### Archivos

| Archivo | Ruta | Descripción |
|---------|------|-------------|
| `llms.txt` | `public/llms.txt` | Ficha en texto plano para modelos IA: nombre, servicios, diferencial, contacto |
| `sitemap.xml` | `public/sitemap.xml` | Mapa del sitio para indexación |
| `robots.txt` | `public/robots.txt` | Permite acceso explícito a GPTBot, ClaudeBot, PerplexityBot, anthropic-ai |
| Schema.org | `src/pages/index.astro` `<head>` | JSON-LD tipo `AccountingService` con servicios, empleado y contacto |

### Schema.org implementado

Tipo: `AccountingService` con:
- Nombre, descripción, URL, teléfono, email
- Dirección (CABA, Argentina)
- `hasOfferCatalog` con los 4 servicios (Monotributistas, Autónomos, Empresas, Estudios)
- `employee` → Jessica Baptista, Contadora Pública, matrícula CPCECABA

### URLs públicas

```
https://items.com.ar/llms.txt
https://items.com.ar/sitemap.xml
https://items.com.ar/robots.txt
```

### Para actualizar llms.txt

Editar `public/llms.txt` directamente y hacer push. Sin build necesario.

---

## Donweb — estado

Donweb sigue activo como:
- Servidor de correo (MX, SMTP, IMAP)
- Panel de administración (`mipanel.items.com.ar`)

El hosting web de Donweb ya no se usa para servir contenido de items.com.ar.

---

*items. — Documentación de Infraestructura*
