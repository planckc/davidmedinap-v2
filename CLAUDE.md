# Instrucciones para Claude Code - Proyecto DME Web Injection

> **IMPORTANTE**: Lee este archivo completo antes de realizar cualquier acción.

---

## ERRORES CONOCIDOS - LEER PRIMERO

### ERROR CRITICO: Bucle Infinito por Screenshots > 8000px

**PROBLEMA:** El agente entra en bucle infinito al tomar screenshots full-page de páginas altas.

```
API Error: 400 {"type":"error","error":{"type":"invalid_request_error",
"message":"At least one of the image dimensions exceed max allowed size: 8000 pixels"}}
```

**REGLAS OBLIGATORIAS:**

1. **NUNCA** usar `npx playwright screenshot --full-page` sin verificar altura
2. **SIEMPRE** usar viewport limitado por defecto:
   ```bash
   npx playwright screenshot --browser chromium --viewport-size=1920,1080 "URL" "output.png"
   ```
3. Si necesitas ver toda la página, usa screenshots segmentados (scroll + múltiples capturas)
4. Si recibes error 8000px: **NO REINTENTAR** - cambiar estrategia inmediatamente
5. Para páginas one-page (como este proyecto), asumir que exceden 8000px

**Documentación completa:** `docs/AGENT_ERROR_DOCUMENTATION.md`

---

## Sobre Este Proyecto

Sitio web personal multi-idioma para **David Medina P.** - Senior BI Developer & AI Context Engineering Architect.

### Datos del Cliente

| Campo | Valor |
|-------|-------|
| Nombre | David Medina |
| Ubicación | Montreal, Canadá |
| Email | davidmedinap@gmail.com |
| LinkedIn | linkedin.com/in/davidmedinap |
| Experiencia | 20+ años en TI |

### Idiomas del Sitio
- Español (principal)
- Inglés
- Francés

---

## Estructura del Proyecto

```
dme-web-injection/
├── CLAUDE.md              # Este archivo (instrucciones para agentes)
├── README.md              # Documentación del proyecto
├── LICENSE                # MIT License
│
├── input/                 # CONTENIDO FUENTE
│   ├── brandinfo/         # Información de marca estructurada
│   │   ├── analitica-estrategica/   # Frente 1
│   │   ├── ia-proposito/            # Frente 2
│   │   ├── fe-en-accion/            # Frente 3
│   │   ├── transformacion-agil/     # Frente 4
│   │   ├── acerca-de/               # Sección About
│   │   ├── contacto/                # Sección Contacto
│   │   └── compartido/              # Imágenes, CVs, datos comunes
│   └── webTemplate/       # Configuración de templates
│
├── web-template/          # TEMPLATES ORIGINALES
│   └── Seppo/             # Template usado (demo-1)
│
├── web-output/            # SITIOS GENERADOS
│   ├── seppo-davidmedina/ # *** VERSIÓN ACTUAL ***
│   │   ├── index.html     # Landing con selector de idioma
│   │   ├── es/index.html  # Español
│   │   ├── en/index.html  # Inglés
│   │   ├── fr/index.html  # Francés
│   │   └── assets/        # CSS, JS, imágenes, fuentes
│   └── koyta-davidmedina/ # Versión alternativa (no usar)
│
├── docs/                  # DOCUMENTACIÓN
│   ├── AGENT_ERROR_DOCUMENTATION.md
│   ├── screenshots/       # Capturas de prueba
│   └── session-logs/      # Logs de sesiones anteriores
│
└── .claude/               # Configuración Claude Code
```

---

## Los 4 Frentes de Trabajo

| # | Frente | Color | Hex | Contenido |
|---|--------|-------|-----|-----------|
| 1 | Analítica Estratégica | Azul | #2563eb | Power BI, Fabric, DAX |
| 2 | IA con Propósito | Violeta | #7c3aed | LLMs, RAG, Automatización |
| 3 | Fe en Acción | Rojo | #dc2626 | MYSION, FaithTech, SINODE |
| 4 | Transformación Ágil | Verde | #059669 | PMO, Scrum, 100+ proyectos |

---

## Archivos Clave

### Para editar contenido:
- `input/brandinfo/*/es.md` - Textos en español
- `input/brandinfo/*/en.md` - Textos en inglés
- `input/brandinfo/*/fr.md` - Textos en francés
- `input/brandinfo/*/data.json` - Datos estructurados

### Para editar estilos:
- `web-output/seppo-davidmedina/assets/css/style.css` - CSS base
- `web-output/seppo-davidmedina/assets/css/custom-david.css` - CSS personalizado

### Para editar comportamiento:
- `web-output/seppo-davidmedina/assets/js/main.js` - JavaScript principal

---

## Notas Técnicas

### Loader del Template
El template Seppo tiene un loader que requiere ~5 segundos para desaparecer cuando se usa con `file://`. El fix está implementado en `main.js` (líneas 34-42) con un setTimeout fallback.

### Altura de Página
- Altura total: ~10,000px
- **EXCEDE el límite de 8000px para screenshots**
- Usar siempre viewport limitado o screenshots segmentados

### Servidor Local
```bash
cd web-output/seppo-davidmedina
python -m http.server 8080
# Abrir: http://localhost:8080/es/
```

### Verificación con Playwright
```bash
# CORRECTO - Viewport limitado
npx playwright screenshot --browser chromium --viewport-size=1920,1080 \
  "http://localhost:8080/es/" "screenshot.png"

# INCORRECTO - Causa error 8000px
npx playwright screenshot --full-page "http://localhost:8080/es/" "screenshot.png"
```

---

## Historial de Sesiones

| Fecha | Log | Resumen |
|-------|-----|---------|
| 2025-12-02 05:44 | `docs/session-logs/status-02122025-0544.md` | Creación inicial del sitio |
| 2025-12-02 13:32 | `docs/session-logs/status-02122025-1332.md` | Diagnóstico error screenshots |

---

## Tareas Pendientes Conocidas

- [ ] Agregar imágenes reales de proyectos al portfolio
- [ ] Conectar formulario de contacto a backend
- [ ] Optimizar imágenes para web
- [ ] Agregar meta tags SEO
- [ ] Configurar dominio davidmedinap.com

---

## Contacto del Proyecto

Para cambios de contenido o estrategia, consultar con David Medina:
- Email: davidmedinap@gmail.com
- Calendly: zcal.co/i/1mbSU6B9
