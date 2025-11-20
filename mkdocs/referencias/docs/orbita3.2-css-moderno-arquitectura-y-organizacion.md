---
hide:
  - navigation
---

# Órbita 3: Maquetar para dar forma

# Órbita 3: Maquetar para dar forma

## Introducción

La maquetación web ha evolucionado drásticamente en los últimos años. Ya no se trata solo de "hacer que se vea bien", sino de construir interfaces escalables, mantenibles y preparadas para crecer. En esta órbita aprenderás a transformar tus diseños de Figma en código que funciona en el mundo real, utilizando las herramientas y técnicas que se emplean en equipos profesionales de frontend.

El objetivo no es memorizar todas las propiedades CSS que existen, sino entender **cómo pensar en componentes**, **cómo estructurar tu código para que otros lo entiendan**, y **cómo usar las características modernas de la plataforma web** para escribir menos código y más expresivo.

## 1. HTML5 semántico: La base de todo

### ¿Por qué importa la semántica?

Cuando escribes HTML, no solo estás diciéndole al navegador "pon esto en pantalla". Estás comunicando **significado**: qué es cada cosa, cómo se relaciona con lo demás, y cómo debe interpretarse. Esto es crucial para:

- **Accesibilidad**: Los lectores de pantalla navegan por la estructura semántica
- **SEO**: Los buscadores entienden mejor el contenido estructurado
- **Mantenibilidad**: Otro desarrollador (o tú mismo en 6 meses) entiende qué hace cada parte
- **CSS más limpio**: Puedes seleccionar elementos por su significado, no solo por clases arbitrarias

### Elementos estructurales modernos

HTML5 nos dio elementos que describen la función de cada parte de la página:

```html
<header>
  <nav>
    <!-- Navegación principal -->
  </nav>
</header>

<main>
  <section>
    <h1>Título de la sección</h1>
    <p>Contenido de la sección...</p>
  </section>
  
  <aside>
    <!-- Información complementaria -->
  </aside>
</main>

<footer>
  <!-- Pie de página -->
</footer>
```

**`<article>`** → Contenido independiente y reutilizable (blog post, tarjeta de producto):
```html
<article>
  <h2>Cómo aprender CSS</h2>
  <p>Contenido del post...</p>
</article>
```

**`<section>`** → Agrupación temática que contiene varios elementos:
```html
<section>
  <h2>Productos destacados</h2>
  
  <article>
    <h3>Producto A</h3>
    <p>Descripción...</p>
  </article>
  
  <article>
    <h3>Producto B</h3>
    <p>Descripción...</p>
  </article>
</section>
```

**Regla práctica**: Si estás tentado a escribir `<div class="header">`, probablemente existe un elemento semántico más apropiado.

### Patrones comunes que debes dominar

**Listas de navegación:**
```html
<nav aria-label="Navegación principal">
  <ul>
    <li><a href="/">Inicio</a></li>
    <li><a href="/productos">Productos</a></li>
    <li><a href="/contacto">Contacto</a></li>
  </ul>
</nav>
```

**Formularios accesibles:**
```html
<form>
  <fieldset>
    <legend>Datos de contacto</legend>
    
    <label>
      Correo electrónico
      <input 
        type="email" 
        name="email"
        required
        aria-describedby="email-hint"
      >
      <small id="email-hint">Nunca compartiremos tu email</small>
    </label>
    
    <label>
      Teléfono
      <input type="tel" name="phone">
    </label>
  </fieldset>
</form>
```

**Contenido multimedia con fallbacks:**
```html
<picture>
  <source srcset="imagen.webp" type="image/webp">
  <source srcset="imagen.jpg" type="image/jpeg">
  <img src="imagen.jpg" alt="Descripción significativa" loading="lazy">
</picture>
```

### Lo que NO debes hacer

❌ Usar `<div>` y `<span>` para todo  
❌ Escribir HTML que solo tenga sentido visualmente  
❌ Omitir atributos `alt`, `aria-label`, o roles ARIA cuando son necesarios  
❌ Usar elementos por su apariencia predeterminada (`<h1>` porque es grande)

## 2. CSS moderno: Arquitectura y organización

### El problema de CSS a escala

CSS es fácil de empezar pero difícil de mantener. Sin estructura, acabas con:

- Estilos globales que se pisan entre sí
- Especificidad fuera de control
- Código duplicado por todas partes
- Miedo a cambiar algo porque "no sé qué más se romperá"

La solución no es escribir más CSS, sino **organizarlo mejor**.

### Arquitectura: Pensando en capas

El CSS moderno nos da herramientas para organizar estilos en capas explícitas. Piensa en tu CSS como una cebolla con diferentes niveles de especificidad:

**Capa 1: Reset/Normalize**  
Neutraliza las diferencias entre navegadores y establece una base consistente.

**Capa 2: Tokens de diseño**  
Variables que definen tu sistema visual: colores, espaciado, tipografía, sombras.

**Capa 3: Estilos base**  
Estilos aplicados directamente a elementos HTML sin clases.

**Capa 4: Layouts**  
Estructuras de página reutilizables (grids, contenedores, regiones).

**Capa 5: Componentes**  
Bloques de interfaz independientes y reutilizables.

**Capa 6: Utilidades**  
Clases de propósito único para ajustes rápidos.

**Capa 7: Overrides**  
Estados especiales, temas, o excepciones controladas.

### Cascade Layers: Haciendo explícito el orden

CSS Cascade Layers (`@layer`) es una de las características más importantes añadidas a CSS en años. Te permite definir explícitamente el orden de prioridad de tus estilos:

```css
/* Definimos el orden de las capas */
@layer reset, tokens, base, layouts, components, utilities, overrides;

/* Cada capa tiene su archivo */
@layer reset {
  *, *::before, *::after {
    box-sizing: border-box;
    margin: 0;
  }
}

@layer tokens {
  :root {
    --color-primary: oklch(0.6 0.2 250);
    --spacing-sm: 0.5rem;
    --spacing-md: 1rem;
  }
}

@layer components {
  .button {
    padding: var(--spacing-sm) var(--spacing-md);
    background: var(--color-primary);
  }
}

@layer overrides {
  .button.is-disabled {
    opacity: 0.5;
    pointer-events: none;
  }
}
```

**Ventaja clave**: Los estilos en capas superiores SIEMPRE ganan, sin importar la especificidad. Esto elimina gran parte de la guerra de `!important`.

### Variables CSS (Custom Properties): Tu sistema de diseño en código

Las variables CSS son mucho más poderosas que las variables de preprocesadores porque:

1. **Son reactivas**: Puedes cambiarlas con JavaScript
2. **Heredan**: Puedes redefinirlas en contextos específicos
3. **Se inspeccionan en DevTools**: Ves los valores computados en tiempo real

```css
:root {
  /* Colores primitivos */
  --color-blue-50: oklch(0.95 0.02 250);
  --color-blue-500: oklch(0.6 0.2 250);
  --color-blue-900: oklch(0.3 0.15 250);
  
  /* Tokens semánticos */
  --color-primary: var(--color-blue-500);
  --color-surface: var(--color-blue-50);
  
  /* Espaciado con escala */
  --space-unit: 0.5rem;
  --space-1: calc(var(--space-unit) * 1);
  --space-2: calc(var(--space-unit) * 2);
  --space-3: calc(var(--space-unit) * 3);
}

/* Tema oscuro */
@media (prefers-color-scheme: dark) {
  :root {
    --color-surface: var(--color-blue-900);
    --color-primary: var(--color-blue-50);
  }
}

/* Contexto específico */
.card {
  --card-padding: var(--space-2);
  padding: var(--card-padding);
}

.card.is-compact {
  --card-padding: var(--space-1);
}
```

### @scope: CSS que sabe dónde vive

`@scope` te permite limitar el alcance de tus estilos a un contexto específico sin aumentar la especificidad:

```css
/* Sin @scope: colisiones globales */
.card .title { color: blue; }
.modal .title { color: red; }

/* Con @scope: contexto explícito */
@scope (.card) {
  .title {
    color: blue;
  }
}

@scope (.modal) {
  .title {
    color: red;
  }
}

/* Límites de scope: afecta dentro de .card pero no dentro de .nested */
@scope (.card) to (.nested) {
  .title {
    color: blue;
  }
}
```

**Caso de uso real**: Componentes de Angular o React que necesitan estilos aislados sin usar CSS Modules o styled-components.

### Container Queries: Componentes que se adaptan a su contenedor

Durante años, hemos usado media queries que miran el tamaño de la ventana. Pero los componentes realmente necesitan saber **su propio tamaño**, no el tamaño de la pantalla.

```css
/* Definir un contenedor */
.card-container {
  container-type: inline-size;
  container-name: card;
}

/* El componente se adapta a su contenedor */
@container card (min-width: 400px) {
  .card {
    display: grid;
    grid-template-columns: 200px 1fr;
  }
  
  .card__image {
    aspect-ratio: 1;
  }
}

@container card (min-width: 600px) {
  .card {
    grid-template-columns: 300px 1fr;
  }
}
```

**Por qué es revolucionario**: Puedes reutilizar el mismo componente en una barra lateral estrecha y en el contenido principal, y se adaptará automáticamente sin saber dónde está.

### El selector :has() — CSS aprende a mirar hacia adelante

`:has()` es básicamente un "selector padre" que CSS nunca tuvo:

```css
/* Estilizar un formulario que contiene errores */
form:has(.error) {
  border: 2px solid red;
}

/* Card con imagen */
.card:has(img) {
  display: grid;
}

/* Card sin imagen */
.card:not(:has(img)) {
  display: flex;
}

/* Artículo seguido de otro artículo (no el primero) */
article:has(+ article) {
  border-bottom: 1px solid gray;
}

/* Lista con al menos 5 items */
ul:has(> li:nth-child(5)) {
  columns: 2;
}
```

**Caso de uso real**: Adaptar layouts según el contenido que realmente existe, sin JavaScript.

## 3. Sistemas de Layout: Grid y Flexbox

### Cuándo usar cada uno

**Flexbox**: Para layouts **unidimensionales** (fila O columna)
- Barras de navegación
- Botones con iconos
- Centrado de elementos
- Distribución de espacio entre items

**Grid**: Para layouts **bidimensionales** (filas Y columnas)
- Layouts de página completos
- Galerías de imágenes
- Formularios complejos
- Dashboards

### Flexbox: Los patrones que más usarás

```css
/* Centrado perfecto */
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Distribución espaciada */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}

/* Columnas de igual altura */
.card-grid {
  display: flex;
  gap: 1rem;
}

.card {
  flex: 1; /* Todos crecen igual */
}

/* Botón con icono */
.button {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
```

### Grid: Pensando en áreas

```css
/* Layout de página clásico */
.page {
  display: grid;
  grid-template-areas:
    "header header header"
    "sidebar main aside"
    "footer footer footer";
  grid-template-columns: 200px 1fr 200px;
  grid-template-rows: auto 1fr auto;
  min-height: 100vh;
  gap: 1rem;
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.aside { grid-area: aside; }
.footer { grid-area: footer; }

/* Galería responsive sin media queries */
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}
```

**Patrón clave**: `auto-fit` + `minmax()` = Grid responsivo sin breakpoints.

### Subgrid: Alineación entre generaciones

```css
.card-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}

.card {
  display: grid;
  grid-template-rows: subgrid; /* Hereda las filas del padre */
  grid-row: span 3;
}

/* Ahora todos los títulos, contenidos y botones se alinean */
```

## 4. Diseño Responsive: Más allá de los breakpoints

### Mobile-first: Por qué y cómo

Empezar por móvil te obliga a priorizar. Si funciona en una pantalla pequeña, escalar hacia arriba es más fácil que lo contrario.

```css
/* Base: móvil */
.container {
  padding: 1rem;
}

.grid {
  display: grid;
  gap: 1rem;
}

/* Tablet */
@media (min-width: 768px) {
  .container {
    padding: 2rem;
  }
  
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .container {
    max-width: 1200px;
    margin-inline: auto;
  }
  
  .grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
  }
}
```

### Unidades fluidas: Tipografía que escala

```css
:root {
  /* Escala entre 16px y 24px según el viewport */
  --font-size-fluid: clamp(1rem, 0.8rem + 1vw, 1.5rem);
}

h1 {
  font-size: clamp(2rem, 5vw, 4rem);
}

.container {
  /* Padding fluido entre 1rem y 3rem */
  padding-inline: clamp(1rem, 5%, 3rem);
}
```

**Función clave**: `clamp(mínimo, preferido, máximo)` — tu nueva mejor amiga.

### Aspect Ratio: Imágenes que no saltan

```css
.video-container {
  aspect-ratio: 16 / 9;
  width: 100%;
}

.thumbnail {
  aspect-ratio: 1;
  object-fit: cover;
}

/* Fallback para navegadores antiguos */
@supports not (aspect-ratio: 1) {
  .thumbnail {
    padding-bottom: 100%; /* Hack del padding */
  }
}
```

## 5. SCSS y Preprocesadores: Organización a escala

### ¿Necesitas SCSS en 2024?

CSS nativo ha incorporado muchas características que antes requerían preprocesadores (variables, nesting). Sin embargo, SCSS sigue siendo valioso por:

- **Mixins**: Reutilización de bloques de código
- **Funciones**: Lógica en tiempo de compilación
- **Partials**: Organización en archivos
- **Ecosistema**: Herramientas maduras y bien documentadas

### Estructura de archivos escalable

```
styles/
├── abstracts/
│   ├── _variables.scss
│   ├── _functions.scss
│   └── _mixins.scss
├── base/
│   ├── _reset.scss
│   └── _typography.scss
├── layouts/
│   ├── _grid.scss
│   └── _containers.scss
├── components/
│   ├── _buttons.scss
│   ├── _cards.scss
│   └── _forms.scss
├── utilities/
│   └── _helpers.scss
└── main.scss
```

### Mixins útiles para proyectos reales

```scss
// Responsive breakpoints
@mixin respond-to($breakpoint) {
  @if $breakpoint == tablet {
    @media (min-width: 768px) { @content; }
  } @else if $breakpoint == desktop {
    @media (min-width: 1024px) { @content; }
  }
}

// Uso
.card {
  padding: 1rem;
  
  @include respond-to(tablet) {
    padding: 2rem;
  }
}

// Truncate text
@mixin truncate($lines: 1) {
  @if $lines == 1 {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  } @else {
    display: -webkit-box;
    -webkit-line-clamp: $lines;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }
}

// Focus visible accesible
@mixin focus-visible {
  &:focus-visible {
    outline: 2px solid var(--color-primary);
    outline-offset: 2px;
  }
}
```

### Funciones para sistemas de diseño

```scss
// Escala de espaciado
@function spacing($multiplier) {
  @return calc(var(--space-unit) * #{$multiplier});
}

// Uso
.card {
  padding: spacing(2); // 1rem
  margin-bottom: spacing(4); // 2rem
}

// Colores con transparencia
@function alpha($color, $opacity) {
  @return rgba($color, $opacity);
}
```

## 6. CSS en Angular: ViewEncapsulation y arquitectura

### Cómo Angular maneja los estilos

Angular ofrece tres modos de encapsulación de estilos:

**Emulated (por defecto)**: Angular añade atributos únicos a tus elementos y reescribe tus selectores para que sean específicos del componente.

```typescript
@Component({
  selector: 'app-card',
  templateUrl: './card.component.html',
  styleUrls: ['./card.component.scss'],
  encapsulation: ViewEncapsulation.Emulated // Por defecto
})
```

Genera HTML como:
```html
<app-card _ngcontent-abc123>
  <h2 _ngcontent-abc123>Título</h2>
</app-card>
```

Y CSS como:
```css
h2[_ngcontent-abc123] {
  color: blue;
}
```

**ShadowDOM**: Usa Shadow DOM nativo del navegador.

```typescript
encapsulation: ViewEncapsulation.ShadowDom
```

**None**: Sin encapsulación, los estilos son globales.

```typescript
encapsulation: ViewEncapsulation.None
```

### Arquitectura de estilos en Angular

**Opción 1: Estilos globales + tokens**

```scss
// styles.scss (global)
@import 'abstracts/variables';
@import 'base/reset';
@import 'base/typography';

:root {
  --color-primary: #3b82f6;
  --spacing-unit: 0.5rem;
}

// card.component.scss
.card {
  padding: var(--spacing-unit);
  background: var(--color-primary);
}
```

**Opción 2: Biblioteca de utilidades compartidas**

```scss
// _shared.scss
@mixin card-shadow {
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

// card.component.scss
@import 'shared';

.card {
  @include card-shadow;
}
```

**Opción 3: Cascade Layers con Angular**

```scss
// styles.scss
@layer reset, tokens, base, components;

@layer tokens {
  :root {
    --color-primary: #3b82f6;
  }
}

// card.component.scss
@layer components {
  .card {
    background: var(--color-primary);
  }
}
```

### Selectores especiales de Angular

```scss
// :host - El elemento anfitrión del componente
:host {
  display: block;
  padding: 1rem;
}

:host(.compact) {
  padding: 0.5rem;
}

// :host-context - Cuando el componente está dentro de algo
:host-context(.dark-theme) {
  background: black;
  color: white;
}

// ::ng-deep - Penetrar encapsulación (usar con precaución)
:host ::ng-deep .external-library-class {
  color: red;
}
```

### Patrones recomendados para Angular

1. **Usa variables CSS para theming**, no SCSS variables
2. **Define tokens globales**, estilos de componente locales
3. **Evita `::ng-deep`** siempre que sea posible
4. **Usa `@layer` para organizar prioridades**
5. **Considera ViewEncapsulation.None para componentes de librería**

## 7. CSS en React: Estrategias de maquetación

### CSS tradicional en React

React no impone ninguna metodología específica para CSS. Puedes usar CSS tradicional exactamente igual que en HTML puro:

```jsx
// Card.jsx
function Card({ title, highlighted }) {
  return (
    <div className={`card ${highlighted ? 'card--highlighted' : ''}`}>
      <h2 className="card__title">{title}</h2>
    </div>
  );
}
```

```css
/* styles.css */
.card {
  padding: 1rem;
  background: white;
  border-radius: 8px;
}

.card--highlighted {
  border: 2px solid blue;
  background: lightblue;
}

.card__title {
  font-size: 1.5rem;
  margin: 0;
}
```

**Ventajas:**
- CSS estándar, sin curva de aprendizaje
- Compatible con todas las herramientas CSS
- Fácil de migrar de HTML tradicional

**Desventajas:**
- Estilos globales (riesgo de colisiones)
- Necesitas disciplina con nomenclatura (BEM, SMACSS, etc.)

### CSS Modules: Scope local automático

CSS Modules viene integrado en Create React App, Vite y la mayoría de bundlers modernos. **No es un framework**, es una transformación en tiempo de compilación que convierte tus clases en identificadores únicos:

```css
/* Card.module.css */
.card {
  padding: 1rem;
  background: white;
}

.title {
  font-size: 1.5rem;
}

.isHighlighted {
  border: 2px solid blue;
}
```

```jsx
// Card.jsx
import styles from './Card.module.css';

function Card({ title, highlighted }) {
  return (
    <div className={`${styles.card} ${highlighted ? styles.isHighlighted : ''}`}>
      <h2 className={styles.title}>{title}</h2>
    </div>
  );
}
```

El navegador verá algo como:
```html
<div class="Card_card__a8f3k Card_isHighlighted__x7j2p">
  <h2 class="Card_title__k3m9n">Mi título</h2>
</div>
```

**Ventajas:**
- Scope local sin conflictos
- CSS estándar (no aprende sintaxis nueva)
- Sin overhead en runtime
- Composición con `composes`:

```css
/* Button.module.css */
.base {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
}

.primary {
  composes: base;
  background: blue;
  color: white;
}

.secondary {
  composes: base;
  background: gray;
  color: black;
}
```

### Variables CSS + React: Valores dinámicos

La mejor forma de pasar valores dinámicos desde React a CSS es usando custom properties:

```jsx
function Card({ title, spacing, accentColor }) {
  return (
    <div 
      className={styles.card}
      style={{ 
        '--card-spacing': `${spacing}rem`,
        '--accent-color': accentColor
      }}
    >
      <h2 className={styles.title}>{title}</h2>
    </div>
  );
}
```

```css
/* Card.module.css */
.card {
  padding: var(--card-spacing, 1rem);
  border-left: 4px solid var(--accent-color, blue);
  /* Fallback values si no se pasan las variables */
}

.card:hover {
  padding: calc(var(--card-spacing) * 1.2);
}

.title {
  color: var(--accent-color);
}
```

**Ventajas de este enfoque:**
- Estilos dinámicos sin mezclar CSS en JavaScript
- Puedes usar pseudo-clases (`:hover`, `:focus`) y media queries
- CSS puede hacer cálculos con las variables
- Transiciones y animaciones funcionan perfectamente
- El CSS mantiene toda la lógica de presentación

### Organización de estilos en proyectos React

**Opción 1: Archivo CSS global + CSS Modules para componentes**
```
src/
├── styles/
│   ├── reset.css
│   ├── variables.css
│   └── global.css
├── components/
│   ├── Card/
│   │   ├── Card.jsx
│   │   └── Card.module.css
│   └── Button/
│       ├── Button.jsx
│       └── Button.module.css
└── App.jsx
```

```jsx
// App.jsx
import './styles/reset.css';
import './styles/variables.css';
import './styles/global.css';
```

**Opción 2: Todo con CSS Modules**
```
src/
├── styles/
│   ├── tokens.module.css  /* Variables compartidas */
│   └── utils.module.css   /* Utilidades */
└── components/
    └── Card/
        ├── Card.jsx
        └── Card.module.css
```

```css
/* tokens.module.css */
:root {
  --color-primary: #3b82f6;
  --spacing-unit: 0.5rem;
}
```

```css
/* Card.module.css */
@import '../../styles/tokens.module.css';

.card {
  padding: calc(var(--spacing-unit) * 2);
  background: var(--color-primary);
}
```

### Patrones recomendados para React

1. **CSS Modules para componentes**, CSS global para reset y tokens
2. **Variables CSS para theming**, no valores hardcodeados
3. **Inline styles solo para valores calculados dinámicamente**
4. **Nomenclatura consistente** (BEM dentro de módulos si quieres)
5. **Co-locación**: CSS junto al componente que lo usa

### Errores comunes en React

❌ **No aprovechar las variables CSS para valores dinámicos**
```jsx
// Evitar: lógica de estilos mezclada con JSX
<div className={props.isDark ? styles.darkText : styles.lightText}>
```

✅ **Usar variables CSS y data attributes**
```jsx
// Mejor: CSS maneja la lógica visual
<div 
  className={styles.text}
  data-theme={props.isDark ? 'dark' : 'light'}
>
```

```css
.text {
  color: var(--text-color);
}

.text[data-theme="dark"] {
  --text-color: #ffffff;
}

.text[data-theme="light"] {
  --text-color: #000000;
}
```

❌ **Estilos globales que colisionan**
```css
/* styles.css - riesgo de conflictos */
.card { padding: 1rem; }
.title { font-size: 1.5rem; }
```

✅ **CSS Modules para scope local**
```css
/* Card.module.css - sin conflictos */
.card { padding: 1rem; }
.title { font-size: 1.5rem; }
```

## 8. Multimedia para web: Optimización y rendimiento

### Formatos de imagen modernos

**WebP**: 25-35% más pequeño que JPEG con igual calidad
```html
<picture>
  <source srcset="imagen.webp" type="image/webp">
  <img src="imagen.jpg" alt="Descripción">
</picture>
```

**AVIF**: 50% más pequeño que JPEG, pero soporte limitado
```html
<picture>
  <source srcset="imagen.avif" type="image/avif">
  <source srcset="imagen.webp" type="image/webp">
  <img src="imagen.jpg" alt="Descripción">
</picture>
```

**SVG**: Para iconos, logos, ilustraciones
```html
<svg class="icon" aria-hidden="true">
  <use href="/icons.svg#icon-name"></use>
</svg>
```

### Lazy loading y performance

```html
<!-- Imágenes que no están en el viewport inicial -->
<img src="imagen.jpg" loading="lazy" alt="Descripción">

<!-- Imágenes críticas (above the fold) -->
<img src="hero.jpg" loading="eager" fetchpriority="high" alt="Hero">

<!-- Iframes -->
<iframe src="video.html" loading="lazy"></iframe>
```

### Responsive images: Srcset y Sizes

```html
<img
  srcset="
    small.jpg 400w,
    medium.jpg 800w,
    large.jpg 1200w
  "
  sizes="
    (max-width: 600px) 100vw,
    (max-width: 1200px) 50vw,
    33vw
  "
  src="medium.jpg"
  alt="Descripción"
>
```

**Traducción**:
- En pantallas ≤600px: imagen ocupa 100% del viewport
- En pantallas ≤1200px: imagen ocupa 50% del viewport
- En pantallas >1200px: imagen ocupa 33% del viewport

El navegador elige automáticamente el tamaño más apropiado.

### Video optimizado

```html
<video 
  controls 
  preload="metadata"
  poster="thumbnail.jpg"
>
  <source src="video.webm" type="video/webm">
  <source src="video.mp4" type="video/mp4">
  <track kind="subtitles" src="subs.vtt" srclang="es" label="Español">
</video>
```

**Reglas de oro:**
- `preload="none"` para videos no críticos
- `preload="metadata"` para videos probablemente vistos
- `poster` siempre
- Incluye subtítulos (`<track>`) para accesibilidad

## 9. Errores comunes y cómo evitarlos

### ❌ Especificidad fuera de control

```css
/* Mal */
#header .nav ul li a.active { }

/* Bien */
.nav-link.is-active { }
```

**Solución**: Usa clases, evita IDs para estilos, aprovecha `@layer`.

### ❌ Unidades absolutas cuando necesitas fluidez

```css
/* Mal */
.container {
  width: 1200px;
  padding: 20px;
}

/* Bien */
.container {
  max-width: 75rem; /* 1200px con font base 16px */
  padding: clamp(1rem, 3%, 2rem);
}
```

### ❌ No pensar en componentes

```css
/* Mal: Estilos demasiado específicos */
.homepage .section .card .title { }

/* Bien: Componente independiente */
.card__title { }
```

**Mentalidad**: Si lo estás copiando y pegando, debería ser un componente.

### ❌ Ignorar cascada y herencia

```css
/* Mal: Repitiendo font-family en cada elemento */
.button { font-family: sans-serif; }
.card { font-family: sans-serif; }
.input { font-family: sans-serif; }

/* Bien: Definir en la raíz */
:root {
  font-family: system-ui, sans-serif;
}
```

### ❌ Media queries que miran el dispositivo, no el contenido

```css
/* Mal */
@media (min-width: 768px) { /* "tablet" */ }

/* Bien */
@media (min-width: 600px) { /* "cuando el contenido lo necesite" */ }
```

**Regla**: Los breakpoints deben estar determinados por tu diseño, no por dispositivos específicos.

---

## Conclusión

La maquetación moderna no se trata de memorizar propiedades CSS, sino de:

1. **Entender la plataforma web**: HTML semántico, cascada, herencia
2. **Pensar en sistemas**: Tokens, componentes, arquitectura escalable
3. **Usar las herramientas modernas**: Grid, Flexbox, Container Queries, Layers
4. **Optimizar para usuarios reales**: Performance, accesibilidad, responsive

El código que escribes hoy será leído (y maldecido o bendecido) por alguien mañana, posiblemente tú mismo. Escribe CSS como si fueras a volver a él en 6 meses sin recordar nada. Tu yo futuro te lo agradecerá.

Ahora ve y construye interfaces que no solo se vean bien, sino que **funcionen bien**, **se mantengan bien**, y **escalen bien**.
