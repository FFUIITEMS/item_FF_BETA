<div align="center">

# 🗄️ item_FF_BETA · Base de Datos de Objetos de Free Fire

**Base de datos buscable de objetos de Free Fire — IDs, nombres, descripciones y assets.**

[![Estado](https://img.shields.io/badge/estado-activo-brightgreen?style=flat-square)](#)
[![Versión](https://img.shields.io/badge/versión-2.0-blue?style=flat-square)](#)
[![Licencia](https://img.shields.io/badge/licencia-MIT-yellow?style=flat-square)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/demo-GitHub%20Pages-222?style=flat-square&logo=github)](https://ffuiitems.github.io/item_FF_BETA/)
[![Hecho con](https://img.shields.io/badge/hecho%20con-HTML%20%2B%20JS%20%2B%20Tailwind-orange?style=flat-square)](#)

[🌐 Demo en vivo](https://ffuiitems.github.io/item_FF_BETA/) · [🐛 Reportar bug](https://github.com/FFUIITEMS/item_FF_BETA/issues) · [💡 Sugerir función](https://github.com/FFUIITEMS/item_FF_BETA/issues)

</div>

---

## 📖 Descripción

**item_FF_BETA** es una aplicación web estática, de código abierto y **sin backend**, que permite buscar cualquier objeto de **Free Fire** (Garena) por:

- 🔑 **ID del objeto** (por ejemplo, `910000001`)
- 📝 **Nombre** (por ejemplo, *"Chrono"*, *"AK47 Dragón"*)
- 📄 **Descripción** o palabra clave del objeto

Además incluye filtros por **rareza**, **tipo de objeto** y **tipo de colección**, junto con un **modo basura** que expone objetos obsoletos o eliminados del juego, útiles para modders y creadores de contenido.

El proyecto también incluye un **visor de caché del navegador** independiente (`/c`) para monitorizar y limpiar los recursos almacenados por la web.

---

## ✨ Características

### 🔍 Búsqueda y filtros
- Búsqueda en tiempo real por **ID, nombre, descripción o palabra clave**
- Filtros combinables: **rareza**, **tipo de objeto** y **tipo de colección**
- Paginación optimizada para grandes volúmenes de resultados

### 🗑️ Modo Basura (Trash Mode)
- Vista alternativa que muestra **objetos obsoletos, eliminados o "basura"** del juego
- Ideal para **modders**, dataminers y creadores de contenido
- Se alimenta de la **misma fuente de datos** (`itemData.json`) pero con un filtro de inclusión

### 🎨 Interfaz
- **Modo claro / oscuro** persistente
- Diseño **responsive** (móvil, tablet, escritorio)
- Tipografía monoespaciada **IBM Plex Mono**
- Animaciones suaves (`fadeIn`, `slideUp`) con GSAP
- Accesibilidad: `aria-label`, roles y navegación por teclado

### 🖼️ Visor de detalles
- Vista previa del objeto en **300×300 px**
- ID, nombre, descripción y rareza
- Botones para **compartir en Telegram** y **buscar en Google Lens**
- **Copiar ID** al portapapeles

### 🗄️ Gestor de Caché (`/c`)
- Lista todas las **Cache Storage** del navegador
- Muestra **tamaño, tipo MIME, estado HTTP, ETag** y `Cache-Control` de cada recurso
- Filtros por tipo (imágenes, JS, CSS, HTML, fuentes)
- **Exportar informe** en JSON
- **Borrar todas las cachés** con confirmación

---

## 🚀 Demo

👉 **https://ffuiitems.github.io/item_FF_BETA/**

| Página | URL |
|--------|-----|
| Base de datos | [`/`](https://ffuiitems.github.io/item_FF_BETA/) |
| Gestor de caché | [`/c`](https://ffuiitems.github.io/item_FF_BETA/c) |
| Cómo buscar | [`/HowToSearch`](https://ffuiitems.github.io/item_FF_BETA/HowToSearch) |

> 💡 **Nota:** Para que la demo funcione, activa **GitHub Pages** en `Settings → Pages → Source: Deploy from branch → main / (root)`.

---

## 🧱 Tecnologías

| Capa | Tecnología |
|------|-----------|
| **Frontend** | HTML5 · JavaScript (ES2020) · CSS3 |
| **Estilos** | Tailwind CSS (CDN) + variables CSS personalizadas |
| **Fuentes** | IBM Plex Mono (Google Fonts) |
| **Animaciones** | GSAP 3.12 |
| **Color** | Chroma.js 2.1 |
| **Hosting** | GitHub Pages |
| **Assets** | Repositorio [`0xme/ff-resources`](https://github.com/0xme/ff-resources) (CDN raw de GitHub) |

> ⚠️ **No hay backend, ni base de datos, ni servidor.** Todo el procesamiento ocurre en el navegador del usuario.

---

## 📂 Estructura del proyecto

```
item_FF_BETA/
├── index.html              # Página principal (base de datos)
├── c/                      # Gestor de caché
│   └── index.html
├── HowToSearch/            # Guía de sintaxis de búsqueda
│   └── index.html
├── src/
│   ├── script.js           # Lógica principal de búsqueda y render
│   ├── Util.js             # Utilidades compartidas
│   ├── CacheManager.js     # Lógica del visor de caché
│   ├── loc.js              # Sistema de localización (i18n)
│   ├── style.css           # Estilos personalizados
│   └── global.css          # Variables y reset
├── assets/
│   ├── itemData.json       # ⭐ Base de datos principal de objetos
│   └── cdn.json            # Mapeo de IDs → URLs de CDN externos
├── icon/                   # Favicons y manifest
├── site.webmanifest
├── LICENSE
└── README.md
```

---

## 🛠️ Instalación local

No requiere build ni dependencias. Solo necesitas servir los archivos estáticos.

### Opción 1: Python (recomendado)

```bash
git clone https://github.com/FFUIITEMS/item_FF_BETA.git
cd item_FF_BETA
python3 -m http.server 8000
```

### Opción 2: Node.js

```bash
npx serve .
```

### Opción 3: VS Code

Instala la extensión **Live Server** y haz clic en "Go Live".

> ⚠️ **No abras `index.html` directamente con `file://`** — la API `fetch` fallará por restricciones CORS. Usa siempre un servidor local.

---

## 🗃️ Fuentes de datos

### `assets/itemData.json`

Contiene la información principal de cada objeto:

```json
{
  "910000001": {
    "id": 910000001,
    "name": "Chrono",
    "description": "Personaje de Free Fire.",
    "icon": "chrono",
    "rare": "Mythic",
    "type": "Character",
    "collection": "Personajes",
    "itemType": "personaje"
  }
}
```

### `assets/cdn.json`

Mapea IDs de objetos a URLs de imágenes alojadas en CDN externos, usado cuando la imagen **no** está disponible en `ff-resources`:

```json
{
  "910000001": "https://cdn.ejemplo.com/chrono.webp"
}
```

### `0xme/ff-resources`

Repositorio externo que contiene las imágenes de los objetos en múltiples resoluciones (`pngs/300x300/`, `pngs/512x512/`, etc.). El script construye URLs como:

```
https://raw.githubusercontent.com/0xme/ff-resources/main/pngs/300x300/{icon}.webp
```

> 💡 Si en el futuro quieres independizarte, puedes hacer un fork de `ff-resources` bajo tu cuenta `FFUIITEMS` y actualizar la URL base en `script.js`.

---

## 🗑️ ¿Cómo funciona el Modo Basura?

El **Modo Basura** no carga desde una fuente distinta. Usa los **mismos archivos** que el modo normal (`itemData.json` + `ff-resources`), pero **filtra y muestra objetos marcados como obsoletos, eliminados o "basura"** que ya no forman parte del juego activo pero cuyos IDs y assets siguen presentes.

Es una vista de **archivo histórico**, útil para:

- 🧑‍💻 **Modders** que necesitan IDs de objetos retirados
- 🎥 **Creadores de contenido** que investigan objetos antiguos
- 🔬 **Dataminers** que analizan cambios entre versiones

---

## 🧭 Uso

### Buscar un objeto

1. Escribe en la barra de búsqueda: un **ID** (`910000001`), un **nombre** (`Chrono`) o una **palabra clave** (`dragón`, `navidad`, `elite`).
2. Combina con los filtros de **rareza**, **tipo** y **colección** para acotar resultados.
3. Haz clic en cualquier tarjeta para ver el detalle completo.

### Cambiar entre modo normal y basura

Usa los botones **`MODO BASURA`** / **`OBJETOS`** en la parte superior de la galería.

### Exportar caché

En `/c`, pulsa **"Exportar Informe"** para descargar un JSON con toda la información de recursos cacheados.

> 📘 Para sintaxis avanzada de búsqueda, consulta la guía en [`/HowToSearch`](https://ffuiitems.github.io/item_FF_BETA/HowToSearch).

---

## 🚀 Despliegue en GitHub Pages

1. Sube todos los archivos a la rama `main` de tu repositorio.
2. Ve a **Settings → Pages**.
3. En **Source**, selecciona **Deploy from a branch**.
4. Elige **Branch: `main`** y **Folder: `/ (root)`**.
5. Guarda y espera 1-2 minutos.
6. Tu sitio estará disponible en `https://ffuiitems.github.io/item_FF_BETA/`.

> ⚠️ **Importante:** El archivo `.nojekyll` debe existir en la raíz del proyecto para que GitHub Pages no intente procesar los archivos con Jekyll. Créalo vacío con `touch .nojekyll`.

---

## 🤝 Contribuir

¡Las contribuciones son bienvenidas! Ya sea un nuevo ID, una corrección de nombre o una mejora de UI.

Consulta [`CONTRIBUTING.md`](CONTRIBUTING.md) para más detalles.

### Reportar bugs

Abre un [issue](https://github.com/FFUIITEMS/item_FF_BETA/issues) con:

- ✅ **Descripción clara** del problema
- ✅ **Pasos para reproducirlo**
- ✅ **Navegador y sistema operativo**
- ✅ **Capturas de pantalla** (si aplica)

### Pull requests

1. Haz un **fork** del repositorio
2. Crea una rama descriptiva: `git checkout -b feat/nueva-funcion`
3. Realiza tus cambios siguiendo el estilo del proyecto
4. Prueba **localmente** con `python3 -m http.server`
5. Abre un **Pull Request** describiendo los cambios

### Agregar objetos

Si detectas un objeto faltante o con datos incorrectos, edita `assets/itemData.json` siguiendo el esquema existente y abre un PR.

---

## 📋 Roadmap

- [x] Búsqueda por ID, nombre y descripción
- [x] Filtros por rareza, tipo y colección
- [x] Modo basura (objetos obsoletos)
- [x] Gestor de caché con exportación JSON
- [x] Modo claro / oscuro
- [x] Localización (i18n)
- [ ] Comparador de objetos lado a lado
- [ ] Historial de cambios entre versiones del juego
- [ ] PWA instalable con soporte offline completo
- [ ] API pública de solo lectura (JSON estático versionado)

---

## ⚖️ Descargo de responsabilidad

> **Este proyecto NO está afiliado, asociado, autorizado ni respaldado por Garena ni por Free Fire.**
>
> Todos los nombres de productos, logotipos y marcas son propiedad de sus respectivos dueños. Los assets (imágenes, nombres, descripciones) son propiedad de **Garena Free Fire** y se proporcionan **únicamente con fines educativos y no comerciales**.
>
> Si eres titular de derechos y consideras que algún contenido infringe tu propiedad intelectual, abre un issue y se tomarán las medidas oportunas.

---

## 📄 Licencia

Distribuido bajo la licencia **MIT**. Consulta [`LICENSE`](LICENSE) para más información.

```
MIT License

Copyright (c) 2025 FFUIITEMS

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

<div align="center">

**Hecho con ☕ y demasiadas horas de datamining por [@FFUIITEMS](https://github.com/FFUIITEMS)**

⭐ Si te resultó útil, deja una estrella en el repo ⭐

</div>
