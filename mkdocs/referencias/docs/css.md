# Hoja de Ruta CSS: Explicación Detallada (20 horas totales)

***

## Nivel 1: Fundamentos de CSS (2 horas)

### Sintaxis y selectores básicos

**Qué es CSS**: CSS (Cascading Style Sheets) es el lenguaje que define la apariencia visual de las páginas web [1]. Mientras HTML estructura el contenido, CSS lo decora [1].

**Cómo vincularlo**: Puedes conectar CSS con HTML de tres formas [1]:
- **Inline**: `<p style="color: red;">Texto</p>` (no recomendado)
- **Internal**: `<style>` dentro del `<head>`
- **External**: `<link rel="stylesheet" href="styles.css">` (mejor práctica)

**Selectores básicos**:
- **Tipo**: `p { color: blue; }` - Afecta a todos los párrafos
- **Clase**: `.destacado { font-weight: bold; }` - Reutilizable en múltiples elementos
- **ID**: `#cabecera { background: gray; }` - Solo un elemento único por página
- **Pseudo-clases**: `:hover` (al pasar el ratón), `:focus` (al hacer clic), `:active` (al presionar)

### Modelo de caja (Box Model)

El **modelo de caja** es fundamental: cada elemento HTML se comporta como una caja rectangular con 4 capas [2][3][4]:

**Content (contenido)**: Donde aparece el texto, imágenes, etc. Se controla con `width` y `height` [2][5].

**Padding (relleno)**: Espacio **interior** entre el contenido y el borde. Crea "aire" dentro de la caja [2][5]:
```css
padding: 20px; /* Todos los lados */
padding: 10px 20px; /* Vertical | Horizontal */
```

**Border (borde)**: Línea que rodea el padding y el contenido [2][4]:
```css
border: 2px solid black;
border-radius: 8px; /* Bordes redondeados */
```

**Margin (margen)**: Espacio **exterior** que separa el elemento de otros elementos [2][5]:
```css
margin: 20px;
margin-top: 10px;
```

**Box-sizing**: Propiedad crucial que define cómo se calcula el tamaño total [6][4][7]:
- `content-box` (default): width/height solo cuenta el contenido. Padding y border se suman extra
- `border-box`: width/height incluye contenido + padding + border (más predecible)

```css
* { box-sizing: border-box; } /* Buena práctica global */
```

### Propiedades de texto y color

- `color`: Color del texto
- `font-size`: Tamaño de fuente (16px, 1rem, 100%)
- `font-family`: Tipo de letra ('Arial', sans-serif)
- `line-height`: Espacio entre líneas (1.5 = 150%)
- `text-align`: Alineación (left, center, right, justify)
- `background`: Color o imagen de fondo

***

## Nivel 2: La Cascada y Especificidad (2 horas)

### Cómo funciona la cascada

La **cascada** es el mecanismo que resuelve conflictos cuando varias reglas afectan al mismo elemento [8]. CSS aplica estilos según tres factores:

**Orden de declaración**: Si dos reglas tienen la misma especificidad, gana la última declarada [8]:
```css
p { color: blue; }
p { color: red; } /* Gana esta */
```

**Herencia**: Algunas propiedades se heredan de padre a hijo automáticamente [8]:
- Se heredan: `color`, `font-family`, `line-height`
- No se heredan: `margin`, `padding`, `border`, `width`

**Especificidad**: Sistema de puntos que determina qué regla es más específica [9][8]:

### Cálculo de especificidad

Se calcula con tres números (A, B, C) [9]:
- **A**: Número de IDs
- **B**: Número de clases, atributos y pseudo-clases
- **C**: Número de elementos y pseudo-elementos

Ejemplos:
```css
p { color: blue; }                    /* (0,0,1) */
.clase { color: red; }                /* (0,1,0) - GANA */
#id { color: green; }                 /* (1,0,0) - GANA */
.clase p { color: purple; }           /* (0,1,1) */
#id .clase p { color: orange; }       /* (1,1,1) - MÁS ESPECÍFICO */
```

Mayor especificidad siempre gana. `!important` sobrescribe todo (evítalo) [9][8].

***

## Nivel 3: Layout Moderno (3 horas)

### Flexbox

**Para qué sirve**: Alinear elementos en **una dimensión** (fila o columna) de forma flexible [10][11]. Perfecto para menús, botones, centrar contenido [10].

**Conceptos clave**:
```css
.contenedor {
  display: flex;
  flex-direction: row; /* row | column */
  justify-content: center; /* Alineación horizontal */
  align-items: center; /* Alineación vertical */
  gap: 1rem; /* Espacio entre elementos */
}
```

**Cuándo usar**: Para alinear elementos en una sola dirección, componentes pequeños, navegación [10][11].

### CSS Grid

**Para qué sirve**: Crear layouts **bidimensionales** (filas Y columnas simultáneamente) [10][11]. Ideal para estructuras completas de páginas [10].

**Conceptos clave**:
```css
.contenedor {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr; /* 3 columnas */
  grid-template-rows: auto 1fr auto; /* 3 filas */
  gap: 20px;
}
```

**Cuándo usar**: Para layouts complejos de página completa, galerías de imágenes, dashboards [10][11].

**Diferencia clave**: Flexbox = una dimensión a la vez; Grid = dos dimensiones simultáneas [10][11].

### Responsive Design

**Media queries**: Aplican estilos según el tamaño de pantalla [12]:
```css
/* Móvil por defecto */
.contenedor { flex-direction: column; }

/* Tablet y superior */
@media (min-width: 768px) {
  .contenedor { flex-direction: row; }
}
```

**Unidades relativas**:
- `rem`: Relativo al tamaño de fuente raíz (html)
- `em`: Relativo al tamaño de fuente del padre
- `%`: Porcentaje del contenedor padre
- `vw`/`vh`: Porcentaje del viewport (ventana del navegador)

***

## Nivel 4: Metodologías CSS (2 horas)

### Por qué necesitas metodologías

En proyectos grandes sin metodología surgen problemas [13][14]:
- Nombres de clases conflictivas (`.button` usado 10 veces diferente)
- Especificidad descontrolada (abusar de `!important`)
- Código difícil de mantener y escalar

### BEM (Block Element Modifier)

**Filosofía**: Nombrar clases de forma clara y consistente [13][15]:

**Block (Bloque)**: Componente independiente reutilizable [15]:
```css
.card { }
.menu { }
.button { }
```

**Element (Elemento)**: Parte del bloque, usa `__` [15]:
```css
.card__title { }
.card__image { }
.menu__item { }
```

**Modifier (Modificador)**: Variante del bloque o elemento, usa `--` [15]:
```css
.card--featured { }
.button--primary { }
.button--large { }
```

Ejemplo completo:
```html
<div class="card card--featured">
  <h2 class="card__title">Título</h2>
  <img class="card__image" src="...">
  <button class="card__button card__button--primary">Click</button>
</div>
```

**Ventajas**: Nombres autoexplicativos, baja especificidad, fácil de mantener [13][15].

### Utility-First CSS

**Filosofía**: Clases pequeñas de un solo propósito [13]:
```css
.u-text-center { text-align: center; }
.u-mt-2 { margin-top: 2rem; }
.u-hidden { display: none; }
```

Se combinan con BEM para casos donde crear un modificador sería excesivo [16][17].

***

## Nivel 5: Custom Properties y Sistemas de Diseño (2 horas)

### Variables CSS (Custom Properties)

**Qué son**: Variables nativas en CSS que almacenan valores reutilizables [18][19].

**Sintaxis**:
```css
:root {
  --color-primary: #3f51b5;
  --spacing-unit: 1rem;
  --font-main: 'Helvetica', sans-serif;
}

.button {
  background: var(--color-primary);
  padding: var(--spacing-unit);
  font-family: var(--font-main);
}
```

**Ventajas** [18][19]:
- Cambias un valor y se actualiza en toda la hoja de estilos
- Respetan la cascada (pueden tener valores diferentes en puntos distintos)
- Permiten cálculos con `calc()`
- Facilitan temas (modo oscuro/claro)

**Ejemplo de cascada**:
```css
:root { --color: blue; }
.card { color: var(--color); } /* azul */
.card--special { --color: red; } /* rojo solo aquí */
```

### Sistema de diseño con tokens

**Design Tokens**: Variables que definen tu sistema visual [18]:
```css
:root {
  /* Colores */
  --color-primary: #3f51b5;
  --color-secondary: #f50057;
  --color-text: #333;
  --color-bg: #fff;
  
  /* Espaciado */
  --spacing-xs: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 2rem;
  
  /* Tipografía */
  --font-size-base: 1rem;
  --font-size-lg: 1.5rem;
}
```

### Uso de calc() - Casos prácticos habituales

**1. Layouts responsivos con márgenes fijos** [20][21]:
El caso más común es cuando quieres que un elemento ocupe el 100% del ancho pero tenga márgenes en píxeles:

```css
.contenedor {
  width: calc(100% - 30px); /* 100% menos los márgenes laterales */
  margin: 0 15px;
}
```

Sin `calc()`, el elemento se desborda porque el 100% más el margen supera el ancho disponible [20].

**2. Dividir el espacio en columnas con márgenes** [20][21]:
Crear un grid de 3 columnas iguales con espaciado entre ellas:

```css
.columna {
  width: calc((100% / 3) - 20px); /* Un tercio menos el margen */
  margin: 0 10px;
  float: left;
}
```

Esto mantiene las columnas perfectamente alineadas sin romper el layout [20][21].

**3. Combinar con variables CSS para sistemas escalables** [22][23]:
```css
:root {
  --espaciado-base: 8px;
}

.card {
  padding: calc(var(--espaciado-base) * 2); /* 16px */
  margin: calc(var(--espaciado-base) * 3); /* 24px */
}
```

Cambias `--espaciado-base` y todo el sistema de espaciado se adapta proporcionalmente [23].

**4. Tipografía fluida responsive** [24]:
```css
h1 {
  font-size: calc(16px + 2vw); /* Tamaño base + porcentaje del viewport */
}
```

El texto crece y decrece automáticamente según el ancho de pantalla [24].

**5. Centrar elementos con position** [25]:
```css
.modal {
  position: absolute;
  width: 300px;
  left: calc(50% - 150px); /* Centro menos mitad del ancho */
}
```

***

## Nivel 6: @layer (2 horas)

### Qué es @layer

Nueva característica CSS que permite **organizar estilos en capas con prioridad explícita** [26][27]. Resuelve conflictos sin depender de especificidad o `!important` [26].

**Problema que resuelve**: En proyectos grandes, controlar el orden de prioridad es caótico [27]. ¿Ganan los estilos del reset? ¿Los del componente? ¿Las utilidades?

**Solución con @layer**: Defines el orden una vez y CSS lo respeta siempre [26][27]:

```css
/* Declaras el orden de prioridad */
@layer reset, base, components, utilities;

/* Los estilos en 'utilities' siempre ganan sobre 'components' */
@layer reset {
  * { margin: 0; padding: 0; }
}

@layer components {
  .button { padding: 1rem; } /* Especificidad (0,1,0) */
}

@layer utilities {
  .u-p-2 { padding: 2rem; } /* Ya no necesitas !important */
}
```

**Ventajas** [26][28]:
- Control total sobre la cascada
- Eliminas `!important`
- Código más mantenible y predecible
- Perfecto para sistemas de diseño

***

## Nivel 7: @scope (2 horas)

### Qué es @scope

Regla CSS que **delimita estilos a una sección específica del DOM** sin JavaScript [29][30]. Los estilos solo se aplican dentro del scope definido.

**Sintaxis**:
```css
@scope (.producto) {
  :scope {
    display: flex;
    padding: 1rem;
  }
  
  .titulo { color: blue; }
  .precio { font-weight: bold; }
}
```

Solo los `.titulo` y `.precio` **dentro de `.producto`** se estilizan [30].

**Diferencia con Shadow DOM**: `@scope` mantiene la cascada activa (estilos globales pueden entrar), mientras Shadow DOM aísla completamente [29].

**Cuándo usar**: Para delimitar estilos a secciones temáticas, evitar conflictos en equipos grandes, migrar código legacy [30].

***

## Nivel 8: Web Components (3 horas)

### Qué son Web Components

**Estándar del W3C** para crear elementos HTML personalizados y reutilizables [31][32][33]. Puedes inventar tus propias etiquetas: `<mi-boton>`, `<galeria-fotos>`, `<menu-desplegable>` [32][34].

**Por qué existen**: Antes necesitabas frameworks (React, Angular) para crear componentes. Web Components son **nativos del navegador** y funcionan en cualquier contexto [32][35].

### Las 4 tecnologías

**1. Custom Elements**: API para definir nuevas etiquetas HTML [31][33]:
```javascript
class MiBoton extends HTMLElement {
  constructor() {
    super();
    this.innerHTML = `
      <button style="padding: 1rem;">
        ${this.getAttribute('texto') || 'Click'}
      </button>
    `;
  }
}
customElements.define('mi-boton', MiBoton);
```

Uso: `<mi-boton texto="Comprar"></mi-boton>`

**2. Shadow DOM**: Encapsula HTML y CSS (lo veremos en el siguiente nivel) [31][33].

**3. HTML Templates**: Plantillas reutilizables con `<template>` [36][33]:
```html
<template id="card-template">
  <style>.card { border: 1px solid #ccc; }</style>
  <div class="card">
    <slot name="titulo"></slot>
    <slot name="contenido"></slot>
  </div>
</template>
```

**4. ES Modules**: Sistema de importación de JavaScript [33]:
```javascript
import { MiComponente } from './mi-componente.js';
```

***

## Nivel 9: Shadow DOM (4 horas)

### Qué es Shadow DOM

API del navegador que crea un **árbol DOM aislado** dentro de un elemento [37][38]. Los estilos y HTML dentro están **completamente encapsulados** [38].

**Creación**:
```javascript
const elemento = document.querySelector('#mi-widget');
const shadow = elemento.attachShadow({ mode: 'open' });

shadow.innerHTML = `
  <style>
    :host {
      display: block;
      padding: 1rem;
      background: #f0f0f0;
    }
    .titulo { color: blue; }
  </style>
  <h2 class="titulo">Encapsulado</h2>
`;
```

**Aislamiento total** [38]:
- Estilos globales de la página NO entran al shadow DOM
- Estilos del shadow DOM NO salen fuera
- Un `.titulo` global no afecta al `.titulo` del shadow DOM

### Selector :host

Estiliza el elemento anfitrión (el que contiene el shadow root) desde dentro [39][37]:
```css
:host {
  display: block;
  --color-tema: blue;
}

:host(.activo) {
  background: yellow; /* Si el host tiene clase 'activo' */
}
```

### Slots

Permiten insertar contenido desde fuera del shadow DOM [39]:
```javascript
shadow.innerHTML = `
  <style>.card { padding: 1rem; }</style>
  <div class="card">
    <slot name="header"></slot>
    <slot></slot> <!-- slot por defecto -->
  </div>
`;
```

Uso:
```html
<mi-card>
  <h2 slot="header">Título</h2>
  <p>Contenido que va al slot por defecto</p>
</mi-card>
```

### Shadow DOM en frameworks

**Angular**: Tres modos de encapsulación [40][41]:
```typescript
@Component({
  encapsulation: ViewEncapsulation.ShadowDom // Shadow DOM nativo
})
```

**React**: No tiene soporte nativo, usa Web Components o CSS Modules [42][43].

### Cuándo usar Shadow DOM

**Ideal para** [38][41]:
- Componentes reutilizables en múltiples proyectos
- Widgets embebidos en sitios de terceros
- Bibliotecas de componentes (design systems)
- Cuando necesitas aislamiento total garantizado

**No usar si** [41]:
- Necesitas que estilos globales afecten al componente
- Trabajas con librerías que no soportan Shadow DOM
- El proyecto es simple y no necesitas tanta complejidad

***

## Resumen de progresión

Desde **selectores básicos** → pasando por **Box Model** y **Flexbox/Grid** → organizando con **BEM** → escalando con **custom properties** y **@layer** → delimitando con **@scope** → hasta llegar al **aislamiento total con Shadow DOM** [12][1].

Cada nivel construye sobre el anterior, preparándote para manejar proyectos CSS de cualquier complejidad en solo 20 horas [12].

