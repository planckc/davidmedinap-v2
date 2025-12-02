# David Medina - Sitio Web Personal Multi-idioma

Sitio web profesional para **David Medina**, Senior BI Developer & AI Context Engineering Architect, desarrollado con asistencia de Claude Code.

## Vista Previa

| Español | English | Français |
|---------|---------|----------|
| [Ver ES](web-output/seppo-davidmedina/es/index.html) | [Ver EN](web-output/seppo-davidmedina/en/index.html) | [Ver FR](web-output/seppo-davidmedina/fr/index.html) |

## Características

- **Multi-idioma**: Español, Inglés y Francés
- **One-page design**: Navegación fluida entre secciones
- **4 Frentes de Trabajo** con colores distintivos:
  - Analítica Estratégica (azul #2563eb)
  - IA con Propósito (violeta #7c3aed)
  - Fe en Acción (rojo #dc2626)
  - Transformación Ágil (verde #059669)
- **Responsive**: Adaptado a todos los dispositivos
- **Template**: Basado en Seppo (demo-1)

## Estructura del Proyecto

```
dme-web-injection/
│
├── CLAUDE.md                 # Instrucciones para Claude Code
├── README.md                 # Este archivo
├── LICENSE                   # Licencia MIT
│
├── input/                    # Contenido fuente
│   ├── brandinfo/            # Información de marca (4 frentes, about, contacto)
│   │   ├── analitica-estrategica/
│   │   ├── ia-proposito/
│   │   ├── fe-en-accion/
│   │   ├── transformacion-agil/
│   │   ├── acerca-de/
│   │   ├── contacto/
│   │   └── compartido/       # Datos, imágenes, CVs
│   └── webTemplate/          # Configuración de template
│
├── web-template/             # Templates HTML originales
│   └── Seppo/                # Template Seppo (usado)
│
├── web-output/               # Sitios web generados
│   ├── seppo-davidmedina/    # VERSIÓN ACTUAL
│   │   ├── index.html        # Landing con selector de idioma
│   │   ├── es/index.html     # Versión Español
│   │   ├── en/index.html     # Versión Inglés
│   │   ├── fr/index.html     # Versión Francés
│   │   └── assets/           # CSS, JS, imágenes, fuentes
│   └── koyta-davidmedina/    # Versión alternativa (descartada)
│
├── docs/                     # Documentación
│   ├── AGENT_ERROR_DOCUMENTATION.md  # Errores conocidos
│   ├── screenshots/          # Capturas de pantalla
│   └── session-logs/         # Logs de sesiones de desarrollo
│
└── .claude/                  # Configuración de Claude Code
    └── settings.local.json
```

## Secciones del Sitio

| Sección | Descripción |
|---------|-------------|
| **Hero** | Presentación principal con parallax |
| **Expertise** | Los 4 frentes de trabajo con descripciones |
| **Acerca de** | Biografía y foto profesional |
| **Clientes** | Logos y testimoniales |
| **Proyectos** | Portfolio de trabajos destacados |
| **Tecnologías** | Skills técnicos con barras de progreso |
| **Logros** | Métricas clave (20+ años, 100+ proyectos, etc.) |
| **Contacto** | Formulario y datos de contacto |

## Tecnologías Usadas

- **HTML5/CSS3**: Estructura y estilos
- **JavaScript/jQuery**: Interactividad
- **Seppo Template**: Base del diseño
- **FontAwesome**: Iconografía
- **Jarallax**: Efectos parallax
- **Isotope**: Filtros de portfolio
- **Owl Carousel**: Sliders

## Desarrollo

### Requisitos

- Node.js (para Playwright)
- Python 3 (para servidor local)
- Git

### Servidor Local

```bash
cd web-output/seppo-davidmedina
python -m http.server 8080
# Abrir http://localhost:8080/es/
```

### Verificación con Playwright

```bash
# Screenshot con viewport seguro (evita error 8000px)
npx playwright screenshot --browser chromium --viewport-size=1920,1080 \
  "http://localhost:8080/es/" screenshot.png
```

## Información de Contacto

- **Email**: davidmedinap@gmail.com
- **LinkedIn**: [linkedin.com/in/davidmedinap](https://linkedin.com/in/davidmedinap)
- **Ubicación**: Montreal, Canadá
- **Agendar reunión**: [zcal.co/i/1mbSU6B9](https://zcal.co/i/1mbSU6B9)

## Licencia

MIT License - Ver [LICENSE](LICENSE)

---

**Desarrollado con Claude Code** | Diciembre 2024
