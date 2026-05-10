<div align="center">

# IG Checker

**Auditor de Instagram que abrís con tu IDE. 100% local. Sin login. Sin tracking.**

[![License: MIT](https://img.shields.io/badge/License-MIT-1a1a2e?style=flat-square)](./LICENSE)
[![Version](https://img.shields.io/badge/version-v1.0.0-ff3030?style=flat-square)](./CHANGELOG.md)
[![Single file](https://img.shields.io/badge/single--file-HTML-000?style=flat-square)](./index.html)
[![Threads](https://img.shields.io/badge/Threads-@ronaldships-000?style=flat-square&logo=threads)](https://www.threads.com/@ronaldships)
[![GitHub stars](https://img.shields.io/github/stars/curetcore/ig-checker?style=flat-square)](https://github.com/curetcore/ig-checker)

[Quick start](#-quick-start) · [Cómo funciona](#-cómo-funciona) · [Modificalo con Claude Code](#-modificalo-con-claude-code) · [FAQ](#-faq)

</div>

---

> **En diciembre de 2024, Meta cerró el acceso público a tu lista de followers de Instagram.** Las apps que prometen "quién no te sigue" hoy hacen una de dos cosas: te piden tu password (= cuenta comprometida) o scrapean Instagram desde tu sesión (= ban garantizado eventualmente).
>
> IG Checker no hace ninguna de las dos. Es un archivo HTML que abrís en tu navegador. Le arrastrás el export oficial que Instagram te da gratis y procesa todo localmente. Sin login, sin servidor, sin que nadie vea tu data.
>
> Open source. Pensado para que lo abras con **Claude Code** (o cualquier IDE con IA) y lo customices.

<br>

## ⚡ Quick Start

### Opción A — Abrílo y usalo (30 segundos)

1. Descargá [`index.html`](./index.html)
2. Doble click → se abre en tu navegador
3. Pedile a Instagram tu export de "Followers and following" (formato JSON)
4. Arrastrá el ZIP al drop zone

Listo. Ves quién no te sigue, quién solo te sigue a ti, y mutuos.

### Opción B — Clonalo y modificalo con Claude Code

```bash
git clone https://github.com/curetcore/ig-checker.git
cd ig-checker
```

Abrílo con Claude Code (o Cursor / Windsurf / cualquier IDE con IA) y pedile lo que quieras:

> *"Agregá un filtro para cuentas verificadas"*
> *"Exportá la lista a CSV"*
> *"Cambiá el tema a oscuro"*
> *"Agregá soporte para TikTok"*

El archivo está estructurado para que un LLM lo entienda en segundos. Hay un banner inicial con el mapa del código y comentarios por sección.

---

## 🎯 Cómo funciona

Después del cierre de la Instagram Basic Display API en diciembre de 2024, la única vía 100% legal para auditar tus followers es **tu propio export oficial**. Instagram te lo da gratis si lo pedís. No requiere API, no requiere login, no requiere automation.

```
1. Vos pedís tu export en instagram.com
2. Instagram te manda un ZIP por email (10 min a 24h)
3. Arrastrás el ZIP a IG Checker
4. Tu navegador lo procesa localmente
5. Ves los resultados — nada sale de tu computadora
```

**Cero APIs prohibidas. Cero scraping. Cero riesgo de ban.** Es tu propia data, procesada por vos, en tu máquina.

---

## ✨ Features

| | |
|---|---|
| **No te siguen** | Cuentas que seguís pero no te siguen de vuelta |
| **Solo te siguen** | Fans (te siguen, vos no a ellos) |
| **Mutuos** | Se siguen entre sí |
| **Whitelist** | Marcá cuentas que querés mantener (familia, marcas) |
| **Detector de nuevos unfollows** | La próxima vez que cargues un export, te marca quién dejó de seguirte |
| **Búsqueda live** | Filtra por username instantáneo |
| **Click directo al perfil** | Abre Instagram en pestaña nueva |
| **Shortcuts** | `/` buscar · `1-4` tabs · `Esc` reset |

---

## 🤖 Modificalo con Claude Code

El archivo está pensado para ser **AI-friendly**. Abrílo y vas a ver:

- **Banner inicial** con el mapa completo del archivo
- **Secciones marcadas** con `/* ============ X ============ */`
- **Estado central** en un objeto `state` (línea ~980)
- **Render functions** desacopladas (línea ~1431)

### Ejemplos de modificaciones que un LLM puede hacer en minutos

**Agregar export a CSV**
> "Agregá un botón en el header que exporte la lista activa a CSV"

**Cambiar el tema**
> "Convertí la paleta a dark mode con negro #0a0a0a de fondo"

**Filtros nuevos**
> "Agregá un filtro para cuentas con menos de 1000 followers (no podemos saberlo desde el export, así que marcalas como ?)"

**Soporte para más plataformas**
> "Adaptá el parsing para procesar también exports de TikTok"

---

## 🔒 Privacidad

- **100% local**. Nada se sube a internet
- **Sin login**, sin auth, sin servidor
- **Sin tracking** (no Google Analytics, no Plausible, nada)
- **Tus snapshots** se guardan en `localStorage` del navegador
- **Para borrar todo**: DevTools → Application → Local Storage → Clear

Podés abrir el archivo sin internet (después de la primera carga). El único network call externo es Google Fonts + JSZip CDN al cargar.

---

## 🛠 Stack

- **HTML + CSS + JavaScript vanilla** — un solo archivo
- [JSZip 3.10](https://stuk.github.io/jszip/) (CDN) — para abrir el `.zip` del export
- [Outfit](https://fonts.google.com/specimen/Outfit) + [Instrument Serif](https://fonts.google.com/specimen/Instrument+Serif) — tipografía

Total: **~1800 líneas** en un solo `index.html`. Sin build step, sin dependencias instalables.

---

## 🌐 Hosting opcional

No necesita hosting. Pero si querés acceder desde cualquier lugar:

```bash
# Vercel
npx vercel

# Netlify
npx netlify-cli deploy --prod

# GitHub Pages
# Subílo a un repo y activá Pages
```

Cualquiera de los 3 es gratis para uso personal.

---

## ❓ FAQ

<details>
<summary><b>¿Cómo descargo mi export de Instagram?</b></summary>

1. Abrí Instagram en navegador o app
2. Settings → Accounts Center → Your information and permissions → Download your information
3. Seleccioná **Some of your information**
4. Marcá solo **Followers and following** (más rápido)
5. Formato: **JSON** (importante: NO HTML)
6. Rango: **All time**
7. Solicitá el export

Instagram te manda un email con un ZIP entre 10 min y 24h.
</details>

<details>
<summary><b>¿Por qué no usa la API de Instagram?</b></summary>

La API oficial no da acceso a tu lista de followers. Las apps que prometen eso son scrapers no oficiales que violan los Términos de Servicio y te exponen a ban de cuenta.

IG Checker usa **tu propio export oficial**, que sí incluye esa data y es 100% legal.
</details>

<details>
<summary><b>¿Puedo unfollowear directo desde IG Checker?</b></summary>

No. Y es a propósito. Automatizar acciones en Instagram viola TOS y te puede banear la cuenta. IG Checker solo te muestra la lista. Vos hacés click en el perfil y decidís si unfollowear manualmente.
</details>

<details>
<summary><b>¿Por qué un solo archivo HTML?</b></summary>

Porque es lo más simple para vos y lo más AI-friendly. Un LLM lee 1800 líneas en segundos y entiende todo el contexto. No hay módulos, no hay build, no hay dependencias que se rompen.
</details>

<details>
<summary><b>¿Funciona offline?</b></summary>

Sí, después de la primera carga. Las fonts y JSZip se cachean. Si querés full offline, podés descargar JSZip y embeberlo en el HTML.
</details>

<details>
<summary><b>¿Quién lo hizo?</b></summary>

[Ronaldo Paulino](https://www.threads.com/@ronaldships). También construí [Linkship](https://linkship.cc) (link in bio SaaS) y [Karrito](https://karrito.shop) (catálogo + WhatsApp). Comparto lo que construyo en Threads.
</details>

---

## 🤝 Contribuir

PRs bienvenidos. Ver [CONTRIBUTING.md](./CONTRIBUTING.md).

Ideas que aceptaría sin pensarlo:
- Export a CSV/JSON de la lista activa
- Soporte para más exports (Twitter/X, TikTok, Threads)
- Modo oscuro
- i18n (inglés, portugués)
- Detección de cuentas inactivas (sin posts)

---

## 📜 Licencia

MIT — ver [LICENSE](./LICENSE).

Hacé fork, adaptalo, vendé tu versión, lo que quieras. Si te sirve, dame ⭐ y mencioname.

---

<div align="center">

**Hecho por [@ronaldships](https://www.threads.com/@ronaldships)** · También construí [Linkship](https://linkship.cc) y [Karrito](https://karrito.shop)

</div>
