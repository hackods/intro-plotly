# Plan: Sesión "Contando historias con datos usando Plotly"

## Objetivo
Sesión de 2 horas donde los participantes aprenden a usar Plotly para crear visualizaciones interactivas orientadas a contar historias con datos, partiendo desde los fundamentos de matplotlib.

## Formato de entrega
- **Presentación Quarto** (`presentacion.qmd`) en formato `revealjs`
- Celdas ejecutables de Python dentro de la presentación
- Los participantes pueden seguir la presentación como notebook interactivo

## Estructura de la sesión (2 horas)

### Bloque 1: Fundamentos de una figura (25 min)
**Slide 1** — Título y contexto: ¿Por qué visualizar datos?
**Slide 2** — Anatomía de una figura matplotlib (figure, axes, axis, labels, ticks, legend, title, spines)
  - Usar el ejemplo clásico de `matplotlib.org/stable/gallery/showcase/anatomy.html`
  - Código en vivo que construye una figura pieza por pieza
**Slide 3** — Ejercicio rápido: construir una figura matplotlib paso a paso agregando elementos

### Bloque 2: De matplotlib a Plotly (20 min)
**Slide 4** — Limitaciones de matplotlib para historias interactivas (estático, exportación, web)
**Slide 5** — ¿Qué es Plotly? Filosofía: figuras como datos (JSON), interactividad nativa, web-first
**Slide 6** — Demo: la misma figura en matplotlib vs plotly express — hover, zoom, pan
**Slide 7** — Integración con Quarto: cómo esta misma presentación es un ejemplo vivo

### Bloque 3: La galería como herramienta de aprendizaje (45 min)
**Slide 8** — Cómo navegar la galería de Plotly (`plotly.com/python/`)
**Slide 9** — Patrón de trabajo: ver ejemplo → entender estructura de datos → adaptar
**Slide 10** — Ejemplo 1: Gráfico de barras agrupadas — estructura de datos tipo long vs wide
**Slide 11** — Ejemplo 2: Líneas de tiempo / series temporales — hover personalizado
**Slide 12** — Ejemplo 3: Mapa coroplético o scatter geográfico — datos geoespaciales
**Slide 13** — Ejercicio guiado: elegir un gráfico de la galería, reproducirlo con datos propios

### Bloque 4: Ejemplo integrador — Datos de Agenda 2030 / ODS (30 min)
**Slide 14** — ¿Qué son los ODS? Fuentes de datos: API ONU, Banco Mundial, datos.gob.es
**Slide 15** — Cargar CSV con indicador ODS 3.2.1 (mortalidad infantil <5 años) y explorar estructura
**Slide 16** — Líneas de tiempo por país con línea de meta ODS 2030
**Slide 17** — Dumbbell chart: progreso 1990 → 2020 por país
**Slide 18** — Mapa coroplético de la región (2020)
  - Cada paso aplica lo aprendido: formato long, galería, personalización

### Cierre (10 min)
**Slide 17** — Recursos: galería, documentación, Quarto + Plotly, API ODS de la ONU
**Slide 18** — Recapitulación y preguntas

## Dependencias necesarias
Ya en `pyproject.toml`:
- matplotlib, plotly, pandas, jupyter, notebook

Por agregar:
- `nbformat` (para renderizado Quarto)
- `kaleido` (exportación de figuras estáticas como fallback)

## Estructura de archivos
```
intro-plotly/
├── presentacion.qmd        # Presentación Quarto (revealjs)
├── datos/                   # Datasets de ejemplo
│   └── (gapminder viene incluido en plotly)
├── PLAN.md
├── pyproject.toml
└── .python-version
```

## Comandos para ejecutar
```bash
# Instalar dependencias
uv sync

# Renderizar presentación
quarto preview presentacion.qmd

# O como notebook interactivo
uv run jupyter notebook presentacion.qmd
```

## Notas de diseño
- Usar `gapminder` dataset de plotly.express.data (no requiere archivos externos)
- Cada slide con código debe ser autocontenido para que funcione como referencia después
- Preferir `plotly.express` sobre `plotly.graph_objects` para mantener simplicidad
- Mostrar `graph_objects` solo cuando sea necesario para personalización avanzada
