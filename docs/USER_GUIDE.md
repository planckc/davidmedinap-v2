# Guía de Usuario - Sitio Web David Medina

Esta guía explica cómo modificar imágenes y textos del sitio web.

---

## Estructura de Archivos

```
web-output/seppo-davidmedina/
├── es/index.html       # Contenido en Español
├── en/index.html       # Contenido en Inglés
├── fr/index.html       # Contenido en Francés
└── assets/
    ├── css/
    │   ├── style.css           # CSS principal (NO MODIFICAR)
    │   └── custom-david.css    # TU CSS personalizado
    ├── images/                 # Imágenes del template
    ├── img/david/              # TUS FOTOS PERSONALES
    └── js/                     # JavaScript
```

---

## 1. Cambiar Imágenes

### 1.1 Fotos Personales

**Ubicación:** `assets/img/david/`

| Archivo | Uso | Tamaño Recomendado |
|---------|-----|-------------------|
| `david-circle.png` | Logo header (ya no usado) | 100x100px |
| `david3.jpg` | Sección "Acerca de" | 600x800px |
| `avatarDavid-small.jpg` | Miniaturas | 150x150px |

**Para cambiar tu foto principal:**
1. Prepara una imagen de 600x800px (vertical)
2. Guárdala como `david3.jpg` en `assets/img/david/`
3. O edita el HTML para usar otro nombre de archivo

### 1.2 Imágenes de los 4 Frentes

**Ubicación:** `assets/images/`

| Archivo | Frente |
|---------|--------|
| `portfolio_item_01.jpg` | Analítica Estratégica |
| `portfolio_item_02.jpg` | IA con Propósito |
| `portfolio_item_03.jpg` | Fe en Acción |
| `portfolio_item_04.jpg` | Transformación Ágil |

**Tamaño recomendado:** 800x600px (horizontal)

**Para cambiar:**
1. Reemplaza el archivo manteniendo el mismo nombre
2. O edita el HTML para cambiar la ruta:
   ```html
   <img src="../assets/images/TU_IMAGEN.jpg" alt="Descripción">
   ```

### 1.3 Imagen de Fondo del Hero

**Archivo:** `assets/images/hero_image_01.jpg`

**Tamaño recomendado:** 1920x1080px mínimo

**Para cambiar:**
1. Reemplaza `hero_image_01.jpg`
2. O edita el HTML:
   ```html
   <div id="home" class="section no-page-title"
        style="background-image: url('../assets/images/TU_FONDO.jpg');">
   ```

---

## 2. Cambiar Textos

### 2.1 Textos del Hero

**Archivo:** `es/index.html` (líneas 89-100)

```html
<h1 class="big-text">
    Transformando<br>
    Datos en <span style="color: #47ea4e;">Decisiones</span>
</h1>
<p style="color: #fff; font-size: 22px;">
    Senior BI Developer & AI Context Engineering Architect<br>
    <span style="color: #b3b3b3;">20+ años de experiencia | Montreal, Canada</span>
</p>
```

### 2.2 Textos de los 4 Frentes

**Archivo:** `es/index.html` (buscar `frente-card`)

```html
<div class="frente-card frente-analitica">
    <h4>Analítica Estratégica</h4>          <!-- Título -->
    <p>Power BI y Business Intelligence...</p>  <!-- Descripción -->
    <div class="frente-tags">
        <span class="frente-tag">Power BI</span>  <!-- Tags -->
        <span class="frente-tag">DAX</span>
    </div>
</div>
```

### 2.3 Sección "Acerca de"

**Archivo:** `es/index.html` (buscar `id="about"`)

```html
<h2>Transformando organizaciones con datos e IA</h2>
<p>Soy David Medina, Senior BI Developer y AI Context Engineering Architect...</p>
```

### 2.4 Estadísticas/Logros

**Archivo:** `es/index.html` (buscar `id="milestones"`)

```html
<div class="milestone-header">20+</div>
<div class="milestone-text">Años de Experiencia</div>
```

---

## 3. Cambiar Colores

### 3.1 Colores de los 4 Frentes

**Archivo:** `assets/css/custom-david.css`

```css
/* Línea ~170 */
.frente-analitica::before { background-color: #2563eb; }  /* Azul */
.frente-ia::before { background-color: #7c3aed; }         /* Violeta */
.frente-fe::before { background-color: #dc2626; }         /* Rojo */
.frente-agil::before { background-color: #059669; }       /* Verde */
```

### 3.2 Color Principal (Verde)

Buscar y reemplazar: `#47ea4e`

---

## 4. Agregar/Quitar Secciones

### Para ocultar una sección:

Agrega `style="display: none;"` al div de la sección:

```html
<div id="milestones" class="section" style="display: none;">
```

### Para quitar del menú:

Edita el `<nav>` y elimina el `<li>` correspondiente:

```html
<ul class="main-menu sm sm-clean">
    <li><a href="#home">Inicio</a></li>
    <!-- <li><a href="#milestones">Logros</a></li>  QUITADO -->
</ul>
```

---

## 5. Traducir a Otros Idiomas

Los 3 archivos son independientes. Cada uno tiene su contenido:

- `es/index.html` - Español
- `en/index.html` - Inglés
- `fr/index.html` - Francés

**Para traducir:**
1. Abre el archivo del idioma
2. Busca el texto a cambiar
3. Tradúcelo manualmente

**Contenido fuente disponible en:** `input/brandinfo/*/`
- `es.md` - Textos en español
- `en.md` - Textos en inglés
- `fr.md` - Textos en francés

---

## 6. Optimización de Imágenes

### Herramientas recomendadas:

| Herramienta | Uso |
|-------------|-----|
| [TinyPNG](https://tinypng.com) | Comprimir PNG/JPG |
| [Squoosh](https://squoosh.app) | Optimizar con control |
| [Remove.bg](https://remove.bg) | Quitar fondos |

### Formatos recomendados:

| Tipo | Formato | Calidad |
|------|---------|---------|
| Fotos | JPG | 80% |
| Logos/iconos | PNG | - |
| Fondos | JPG | 70% |

---

## 7. Verificar Cambios

### Abrir localmente:

```bash
cd web-output/seppo-davidmedina
python -m http.server 8080
# Abrir: http://localhost:8080/es/
```

### O simplemente:

1. Doble clic en `web-output/seppo-davidmedina/es/index.html`
2. Se abre en tu navegador predeterminado

---

## 8. Estructura de Directorios para Imágenes Personalizadas

Si quieres organizar mejor tus imágenes:

```
assets/img/
├── david/              # Fotos personales
│   ├── profile.jpg
│   └── about.jpg
├── projects/           # Imágenes de proyectos
│   ├── proyecto1.jpg
│   └── proyecto2.jpg
├── clients/            # Logos de clientes
│   ├── desjardins.png
│   └── hydro.png
└── frentes/            # Imágenes de los 4 frentes
    ├── analitica.jpg
    ├── ia.jpg
    ├── fe.jpg
    └── agil.jpg
```

---

## Checklist de Cambios Comunes

- [ ] Cambiar foto de perfil → `assets/img/david/david3.jpg`
- [ ] Cambiar fondo del hero → `assets/images/hero_image_01.jpg`
- [ ] Actualizar título principal → Buscar `big-text` en HTML
- [ ] Cambiar estadísticas → Buscar `milestone-header`
- [ ] Agregar/quitar cliente → Buscar `client-logo`
- [ ] Cambiar color principal → Buscar `#47ea4e`

---

## Soporte

Si necesitas ayuda técnica o cambios más complejos, contacta a:
- Email: davidmedinap@gmail.com
- O usa Claude Code para asistencia automatizada
