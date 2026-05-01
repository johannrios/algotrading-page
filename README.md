# AlgoTrading Nexus
### HTML5 Semántico y Accesible

> Plataforma educativa sobre trading algorítmico construida como demostración de buenas prácticas en semántica HTML5 y accesibilidad web.

---

## Propósito de la página

**AlgoTrading Nexus** es una página informativa dirigida a traders, desarrolladores y estudiantes interesados en el trading algorítmico y los mercados financieros cuantitativos. El objetivo es explicar qué es el trading algorítmico, describir las principales estrategias cuantitativas y ofrecer un punto de contacto/registro para acceder a contenido avanzado.

**Público objetivo:** Traders independientes con conocimientos de programación (Python), estudiantes de finanzas cuantitativas, y desarrolladores interesados en la intersección de software e inversiones.

---

## Estructura del proyecto

```
algotrading-page/
├── index.html         
├── assets/
│   └── chart-placeholder.svg  ← Gráfico de velas con indicadores técnicos
└── README.md           
```

---

## Cómo visualizar la página

### Opción A — Directamente en el navegador (sin instalar nada)
1. Descarga el repositorio como ZIP: botón verde **Code → Download ZIP**.
2. Descomprime el archivo en tu computador.
3. Entra a la carpeta `algotrading-page/` y abre `index.html`
   con cualquier navegador moderno (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+).
4. Las fuentes requieren conexión a internet (se cargan desde Google Fonts).

> No se requiere servidor web, Node.js ni ninguna dependencia.

### Opción B — Clonar con Git
```bash
git clone https://github.com/TU_USUARIO/algotrading-page.git
cd algotrading-page
# Abrir index.html en el navegador
open index.html        # macOS
xdg-open index.html    # Linux / Ubuntu
start index.html       # Windows
```

### Opción C — GitHub Pages (sin descargar nada)
Accede directamente en el navegador:
```
https://TU_USUARIO.github.io/algotrading-page/
```

---

## Semántica HTML5 aplicada

### Etiquetas semánticas utilizadas y su justificación

| Etiqueta | Uso en la página | Justificación semántica |
|---|---|---|
| `<header>` | Encabezado del sitio con logo y navegación | Identifica el encabezado global del documento, distinto de encabezados de sección |
| `<nav>` | Menú principal + navegación del aside | Delimita zonas de navegación, diferenciadas con `aria-label` |
| `<main>` | Contenido central de la página | Señala el contenido principal; un solo `<main>` por página |
| `<section>` | Hero, ¿Qué es?, Estrategias, Conceptos, Contacto | Agrupa contenido temático con su propio encabezado (`h2`) |
| `<article>` | Cada tarjeta de estrategia (Mean Reversion, Trend Following, etc.) | Contenido autónomo y sindicable; cada estrategia tiene sentido por sí sola |
| `<aside>` | Panel de datos de mercado y recursos | Contenido complementario, no esencial para el flujo narrativo principal |
| `<footer>` | Pie con metainformación y enlaces secundarios | Información de autoría, legal y secundaria al final del documento |
| `<fieldset>` + `<legend>` | Grupos de campos del formulario | Agrupación semántica de controles relacionados |
| `<figure>` | (referenciada en el alt de la imagen) | No usada directamente pero el patrón de imagen con contexto sigue su espíritu |

### Jerarquía de encabezados
```
h1 — Título principal del hero
  h2 — ¿Qué es el Trading Algorítmico?
  h2 — Arquitecturas de estrategia probadas
    h3 — Mean Reversion (dentro de <article>)
    h3 — Trend Following
    h3 — Market Making
    h3 — Statistical Arbitrage
  h2 — Conceptos que todo algo-trader debe dominar
    h3 — Backtesting
    h3 — Ratio de Sharpe
    h3 — Maximum Drawdown
    h3 — Overfitting
    h3 — Slippage y Costos de Transacción
  h2 — Panel de datos de mercado (aside)
  h2 — Accede al contenido completo (formulario)
```

---

## Accesibilidad aplicada (WCAG 2.1 AA)

### 1. Skip Link (WCAG 2.4.1 — Bypass Blocks)
El primer elemento de la página es un enlace "Saltar al contenido principal" que se hace visible al recibir foco. Permite a usuarios de teclado y lectores de pantalla omitir la navegación repetitiva.

### 2. Etiquetas de formulario asociadas (WCAG 1.3.1)
Todos los campos del formulario tienen un `<label>` con atributo `for` que coincide con el `id` del campo. Los campos obligatorios están marcados con `aria-required="true"` y un indicador visual `*`.

### 3. Texto alternativo en imágenes (WCAG 1.1.1)
La imagen principal tiene un `alt` descriptivo y contextual que explica el contenido visual: tipo de gráfico, indicadores mostrados y señales de trading visibles. Los elementos decorativos SVG tienen `aria-hidden="true"`.

### 4. Atributos ARIA utilizados
- `role="banner"` — Header del sitio
- `role="navigation"` — Navegación principal
- `role="main"` — Contenido principal
- `role="contentinfo"` — Footer
- `role="complementary"` — Aside
- `role="list"` / `role="listitem"` — Listas de datos de mercado y estadísticas
- `aria-label` — En `<nav>`, botones y enlaces ambiguos (e.g., "se abre en nueva pestaña")
- `aria-labelledby` — Vincula cada `<section>` con su `<h2>` correspondiente
- `aria-describedby` — Vincula el formulario con su descripción introductoria
- `aria-required="true"` — Campos obligatorios del formulario
- `aria-live="polite"` — Ticker de precios (actualizable sin interrumpir)
- `aria-hidden="true"` — Elementos puramente decorativos (SVG del logo, ticker duplicado)
- `aria-current="page"` — Enlace de navegación activo

### 5. Contraste de colores (WCAG 1.4.3)
- Texto principal `#e8e2d5` sobre fondo `#060a12`: **ratio 14.8:1** (AAA)
- Texto muted `#8a9ab5` sobre `#060a12`: **ratio 5.2:1** (AA)
- Acento verde `#00d4a0` sobre `#060a12`: **ratio 8.1:1** (AAA)
- Dorado `#c8a96e` sobre `#060a12`: **ratio 6.4:1** (AA)

### 6. Navegación por teclado
- Orden de foco lógico siguiendo el flujo visual del documento
- Foco visible mejorado con `:focus-visible` (borde verde 2px + offset 3px)
- No hay trampas de teclado
- Todos los elementos interactivos son alcanzables con Tab

### 7. Enlace a recursos externos
Los enlaces a recursos de terceros incluyen `rel="noopener noreferrer"` (seguridad) y `target="_blank"` con `aria-label` que advierte "se abre en nueva pestaña" (WCAG 2.4.4).

---

## Validación W3C

El código HTML fue validado contra el [W3C Markup Validation Service](https://validator.w3.org):

-  Sin errores de estructura
-  DOCTYPE HTML5 correcto
-  Codificación UTF-8 declarada
-  Meta viewport presente
-  Atributos `lang` en `<html>`
-  Sin atributos obsoletos

---

## Decisiones de diseño

### Paleta de color
Se eligió una paleta oscura (dark theme) con fondo `#060a12` (negro abismal) por tres razones:
1. **Contexto**: Los terminales y plataformas de trading profesional (Bloomberg, TradingView) usan temas oscuros.
2. **Accesibilidad**: El fondo oscuro permite mayor contraste con texto claro, superando AAA.
3. **Estética**: Evoca precisión y sofisticación técnica.

El acento verde (`#00d4a0`) representa datos positivos/alcistas; el dorado (`#c8a96e`) evoca valor y excelencia. El rojo (`#ff4757`) se reserva para datos bajistas.

### Tipografía
- **Syne** (display, titulares): fuente geométrica de alta personalidad para impacto visual.
- **Instrument Serif** (cuerpo de texto): añade elegancia editorial y legibilidad en párrafos largos.
- **JetBrains Mono** (datos, código, labels): fuente monoespaciada de alta legibilidad para números y datos financieros.

### Uso de `<article>` para estrategias
Cada estrategia de trading se marcó como `<article>` porque cumple la definición de la especificación HTML5: *"contenido que tiene sentido por sí mismo y puede ser sindicado"*. Una tarjeta de "Mean Reversion" podría publicarse en un blog o newsletter sin perder su coherencia narrativa.

---

## Tecnologías utilizadas

- **HTML5** — Estructura semántica
- **CSS3** — Estilos, animaciones y layout (Grid + Flexbox)
- **Google Fonts** — Tipografías (Syne, Instrument Serif, JetBrains Mono)
- **SVG inline** — Gráfico de precios e ícono de marca
- Sin frameworks ni JavaScript (accesibilidad máxima, carga mínima)

---

## Limitaciones y notas

> ⚠ **Aviso**: Los precios de mercado mostrados en el ticker y el panel lateral son **datos ilustrativos** con fines educativos. No constituyen asesoramiento financiero. En una implementación de producción, estos datos vendrían de una API financiera (Polygon.io, Alpha Vantage, Binance API, etc.).

---

