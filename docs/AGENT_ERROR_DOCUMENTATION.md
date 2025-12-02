# Documentación de Error Recurrente: Bucle Infinito por Screenshot

## Resumen del Error

El agente Claude entra en un bucle infinito cuando intenta tomar un screenshot full-page de una página web que excede 8000 píxeles de altura.

## Detalles Técnicos

### Error de la API
```
API Error: 400 {"type":"error","error":{"type":"invalid_request_error",
"message":"messages.7.content.6.image.source.base64.data: At least one of
the image dimensions exceed max allowed size: 8000 pixels"}}
```

### Causa Raíz
1. El comando `npx playwright screenshot --full-page` genera una imagen de la página completa
2. Si la página tiene altura > 8000px (ej: 10,058px en este caso), la imagen excede el límite de la API
3. Cuando el usuario escribe "continua", el agente vuelve a intentar el mismo screenshot
4. El ciclo se repite infinitamente

### Condiciones que Disparan el Bucle
- Página web con contenido extenso (múltiples secciones)
- Uso de `--full-page` en Playwright screenshot
- El agente no detecta el error como bloqueante y reintenta

## Historial de Ocurrencias

| Fecha | Sesión | Página Afectada | Altura |
|-------|--------|-----------------|--------|
| 2025-12-02 05:44 | status-02122025-0544.md | seppo-davidmedina/es | ~10,000px |
| 2025-12-02 13:32 | status-02122025-1332.md | seppo-davidmedina/es | 10,058px |

## Soluciones Implementadas

### Solución 1: Viewport Limitado (Recomendada)
```bash
# En lugar de --full-page, usar viewport fijo
npx playwright screenshot --browser chromium --viewport-size=1920,1080 \
  "URL" "output.png"
```

### Solución 2: Screenshots Segmentados
```javascript
// Tomar screenshots por secciones con scroll
const screenshots = [];
for (let y = 0; y < totalHeight; y += 1080) {
  await page.evaluate(offset => window.scrollTo(0, offset), y);
  screenshots.push(await page.screenshot());
}
```

### Solución 3: Detectar Altura Antes de Screenshot
```javascript
const height = await page.evaluate(() => document.documentElement.scrollHeight);
if (height > 8000) {
  console.log('ADVERTENCIA: Página muy alta, usando viewport limitado');
  // Usar screenshot con viewport fijo
}
```

## Reglas para el Agente

**IMPORTANTE: Antes de tomar screenshots full-page:**

1. **NUNCA** usar `--full-page` sin verificar la altura primero
2. **SIEMPRE** preferir `--viewport-size=1920,1080` para verificaciones rápidas
3. Si se necesita ver toda la página, tomar múltiples screenshots segmentados
4. Si ocurre el error 8000px, **NO reintentar** - cambiar estrategia inmediatamente
5. Documentar en el chat que el screenshot fue limitado por el tamaño

## Checklist de Prevención

- [ ] Verificar altura de página antes de full-page screenshot
- [ ] Usar viewport fijo por defecto
- [ ] Si error ocurre, cambiar a estrategia alternativa (no reintentar)
- [ ] Informar al usuario sobre la limitación

## Notas Adicionales

- El límite de 8000px es de la API de Anthropic para imágenes en mensajes
- Este no es un bug de Playwright, es una limitación del contexto del agente
- Las páginas one-page con múltiples secciones típicamente exceden 8000px
