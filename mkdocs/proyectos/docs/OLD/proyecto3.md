---
hide:
  - navigation
---

# **Proyecto 3: Maquetando y desarrollando nuestra aplicación web (API).** 
## **1. Descripción del proyecto** 

En este proyecto desarrollarás una aplicación web de una sola página (SPA) que consuma una API REST pública y muestre sus datos de forma dinámica. 
La navegación entre las distintas secciones de la aplicación se gestionará mediante React Router, permitiendo una experiencia fluida sin recargas de página. 
En nuestro módulo se trabajará la maquetación completa de la aplicación web prototipada y testeada en los proyectos anteriores.
Este proyecto forma parte de una actividad conjunta con el módulo de Desarrollo Web en Entorno Cliente (DWEC), justamente en el [proyecto 4](https://fluffy-adventure-zwwjv7l.pages.github.io/docs/proyectos/proyecto4/#fundamentacion-teorica).


## **2. Objetivos del proyecto** 

* Conocer y crear documentos HTML5 aplicando las buenas prácticas.
* Conocer y Crear estilos CSS.
* Aplicar las buenas prácticas en el diseño de una aplicación web mediante estilos.
* Crear interfaces adaptadas a multidispositivos.
* Crear animaciones en las interfaces web.
* Verificar la adecuación del código a los estándares de calidad.
* Utilizar un workflow de desarrollo frontend moderno, que diferencie entornos de desarrollo y producción, con las diferencias que correspondan a cada uno.
* Utilizar el lenguaje de preprocesado de estilos Sass o PostCSS.

## **3. Resultados de aprendizaje y Criterios de evaluación** {#resultados-de-aprendizaje-y-criterios-de-evaluación}

**RA2** Crea interfaces Web homogéneos definiendo y aplicando estilos.

* CE 2a) Se han reconocido las posibilidades de modificar las etiquetas HTML.
* CE 2b) Se han definido estilos de forma directa.
* CE 2c) Se han definido y asociado estilos globales en hojas externas. 
* CE 2d) Se han definido hojas de estilos alternativas. 
* CE 2e) Se han redefinido estilos. 
* CE 2f) Se han identificado las distintas propiedades de cada elemento. 
* CE 2g) Se han creado clases de estilos. 
* CE 2h) Se han utilizado herramientas de validación de hojas de estilos. 
* CE 2j) Se han analizado y utilizado preprocesadores de estilos para traducir estilos comunes a un código estándar y reconocible por los navegadores.

**RA3** Prepara archivos multimedia para la Web, analizando sus características y manejando herramientas específicas.

* CE 3f) Se han realizado animaciones a partir de imágenes fijas.
* CE 3h) Se ha aplicado la guía de estilo.

## **4. Prueba**

La parte de desarrollo se debe entregar en una carpeta y repositorio de GitHub que contenga exactamente los ficheros y carpetas que se indican a continuación:

* dist/ \-\> compilado para producción con npm run build (si usas otro empaquetador la que por defecto salga)
* src/ \-\> la carpeta de desarrollo (si usas otro empaquetador la que por defecto salga)
* package.json \-\> para ver las dependencias instaladas

Cualquier entrega que contenga la carpeta node\_modules, será rechazada.

Las herramientas que utilizaremos serán un IDE de programación, Git y GitHub y un navegador para el testeo.

El proceso de la parte de desarrollo es el siguiente:

### **4.1 Estructura del proyecto.**

Carpeta con el proyecto (src) y la arquitectura de organización que sea clara y sea legible. 
Es recomendable usar la estructura vista en clase de SASS.

### **4.2 Vistas**

Creamos las vistas de las páginas principales de nuestro proyecto (lo haréis a través de React, pero se comprobará en el navegador. (Las que hayamos creado en el mockup).
* Página de inicio
* Flujo de Registro y Acceso del usuario
* Listado de productos o servicios (ejemplo: listado de los personajes de Marvel)
* Vista de producto
* Página de Contacto
* Página 404
* Página de perfil de usuario …

### **4.3 Estilos**
Creamos uno o varios documentos SASS para incluir nuestro proyecto. Donde tenemos que tener en cuenta los siguientes puntos.**

   - 3.1 El código debe estar documentado con comentarios para que su lectura sea fácil.
   - 3.2 Debemos añadir dos formas de incluir estilos CSS de forma directa y explicar si es recomendable su uso.  (se puede añadir un documento readme.txt en el proyecto, o en un comentario)
   - 3.3 Debemos utilizar la metodología que más nos convenga a la hora de plasmar nuestro CSS o SASS. 
   - 3.4 Debemos usar la guía de estilos del diseño creado en Figma. 
   - 3.5 Creamos las variables necesarias para poder utilizar en el código. 
   - 3.6 Creamos los estilos necesarios para que nuestra aplicación sea 100% responsive. 
   - 3.7 Crear una hoja de estilos alternativa para la página de inicio. (Dark version / Light version)
   - 3.8 Añade transiciones a todos los elementos que puedan tener diferentes eventos. 
   - 3.9 Crea una página 404.html que tenga una animación con transformaciones

### **4.4 Validación**
Tienes que validar tu CSS para ver si cumple la normativa  ([https://jigsaw.w3.org/css-validator/](https://jigsaw.w3.org/css-validator/)), adjunta las evidencias.

### **4.5 Repositorio**
El proyecto debe estar en Github (Debes agregarme al repositorio con mi usuario **envasador** tiene la cara de BMO) y *no debe haber ningún commit después de la fecha de la entrega recogida en Moodle.*

### **4.6 Videotutorial**
Para la entrega del videotutorial, cada estudiante debe realizar una presentación clara y detallada de todo el proceso de desarrollo del proyecto. 
El video debe incluir desde la fase inicial de análisis y planificación hasta la implementación final de la interfaz web. Es fundamental que se expliquen 
las decisiones de diseño tomadas, las herramientas utilizadas, la maquetación con HTML5 y CSS3/SASS, así como los aspectos que sean destacables como la arquitectura. El videotutorial debe tener una duración máxima de 7 minutos y seguir un orden lógico que permita entender fácilmente cada paso del proyecto, destacando los problemas encontrados y las soluciones aplicadas. Además, se recomienda incluir una breve conclusión sobre el resultado final y posibles mejoras.


## **6. Entrega final** 

Debéis entregar:

* Los archivos que correspondan al proyecto completo a través de GitHub y en la tarea asignada agregar el enlace al repositorio. Este repositorio tiene que estar público o si es privado que pueda tener acceso.
* Videotutorial explicando el proyecto. (se puede incluir en los archivos de GitHub)

Revisión.

* Se puede realizar una prueba oral en la que el profesor revisará los proyectos con el alumnado de forma individual, con una duración máxima de 8 min.

Ánimo 🖖


## **7. Calificación**

**RA2**

| CE | 10 excelente                                                                                                                                                                                                                                            | 8 notable                                                                                                                                                                        | 6 bien                                                                                                                                                                          | 4 necesita mejorar | 2 insuficiente | 0 no asiste |
| :---- |:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| :---- | :---- | :---- |
| a) Se han reconocido las posibilidades de modificar las etiquetas HTML. | Se han reconocido las posibilidades de modificar las etiquetas HTML utilizando algunos selectores complejos de forma autónoma, identificando las partes del selector de forma excelente.                                                                | Se han reconocido las posibilidades de modificar las etiquetas HTML utilizando algunos selectores complejos con ayuda, identificando las partes del selector de forma excelente. | Se han reconocido las posibilidades de modificar las etiquetas HTML utilizando algunos selectores complejos con ayuda, identificando las partes del selector de forma correcta. | Se han reconocido las posibilidades de modificar las etiquetas HTML utilizando algunos selectores complejos con ayuda, identificando las partes del selector con algún error. | Se han reconocido las posibilidades de modificar las etiquetas HTML utilizando algunos selectores complejos con ayuda, identificando las partes del selector con varios errores. | No asiste o no es evaluable |
| b) Se han definido estilos de forma directa. | Se han definido de forma autónoma, conociendo su uso de manera excelente                                                                                                                                                                                | Se han definido de forma autónoma, conociendo su uso de manera correcta                                                                                                          | Se han definido con ayuda, conociendo su uso de manera correcta                                                                                                                 | Se han definido con ayuda, conociendo su uso con algún error | Se han definido con ayuda, conociendo su uso con varios errores | No asiste o no es evaluable |
| c) Se han definido y asociado estilos globales en hojas externas. | Se han definido de manera organizada y se ha documentado de forma excelente.                                                                                                                                                                            | Se han definido de manera organizada y se ha documentado de forma correcta.                                                                                                      | Se han definido de manera organizada y se ha documentado de forma escueta.                                                                                                      | Se han definido de manera poco organizada y se ha documentado de forma escueta. | Se han definido de manera poco organizada y no se ha documentado | No asiste o no es evaluable |
| d) Se han definido hojas de estilos alternativas. | Se han definido hojas de estilo alternativas, creando un diseño de forma excelente.                                                                                                                                                                     | Se han definido hojas de estilo alternativas, creando un diseño de forma correcta.                                                                                               | Se han definido hojas de estilo alternativas, creando un diseño con algún fallo.                                                                                                | Se han definido hojas de estilo alternativas, creando un diseño con varios fallos. | Se han definido hojas de estilo alternativas, creando un diseño con muchos fallos. | No asiste o no es evaluable |
| f) Se han identificado las distintas propiedades de cada elemento. | Se han identificado las distintas propiedades de cada elemento de forma autónoma, utilizando opciones avanzadas de manera excelente y conociendo su uso.                                                                                                | Se han identificado las distintas propiedades de cada elemento con ayuda, utilizando opciones avanzadas de manera correcta y conociendo su uso.                                  | Se han identificado las distintas propiedades de cada elemento con ayuda, utilizando distintas opciones de manera correcta y conociendo su uso.                                 | Se han identificado las distintas propiedades de cada elemento con ayuda, utilizando distintas opciones con algún fallo. | Se han identificado las distintas propiedades de cada elemento con ayuda, utilizando distintas opciones con varios fallos. | No asiste o no es evaluable |
| g) Se han creado clases de estilos. | Se han creado estilos avanzados de forma autónoma, con precisión y adaptado a todos los dispositivos de forma excelente.                                                                                                                                | Se han creado estilos avanzados con ayuda, con precisión y adaptado a casi los dispositivos de forma excelente.                                                                  | Se han creado estilos con ayuda, con bastante precisión y adaptado a casi los dispositivos de forma correcta.                                                                   | Se han creado estilos con ayuda, con algunas imprecisiones, y adaptado a casi los dispositivos con pocos fallos. | Se han creado estilos con ayuda, con bastantes imprecisiones y adaptado a casi los dispositivos con varios fallos. | No asiste o no es evaluable |
| h) Se han utilizado herramientas de validación de hojas de estilos. | Se han utilizado herramientas de validación, sin obtener errores y documentado el resultado (salvo variables)                                                                                                                                           | Se han utilizado herramientas de validación, con un error y documentado el resultado (salvo variables)                                                                           | Se han utilizado herramientas de validación, con algunos errores y documentado el resultado (salvo variables)                                                                   | Se han utilizado herramientas de validación, con varios errores y sin documentar el resultado (salvo variables) | Se han utilizado herramientas de validación, con muchos errores y sin documentar el resultado (salvo variables) | No asiste o no es evaluable |
| e) Se han redefinido estilos. | Conoce y ejecuta de forma excelente el cómo y el porqué se usa la redefinición de estilos.                                                                                                                                                              | Conoce y ejecuta de forma correcta el cómo y el porqué se usa la redefinición de estilos.                                                                                        | Conoce levemente el cómo y el porqué se usa la redefinición de estilos.                                                                                                         | Casi no conoce el cómo y el porqué se usa la redefinición de estilos. | No conoce el cómo y el porqué se usa la redefinición de estilos. | No asiste o no es evaluable |
| j) Se han analizado y utilizado preprocesadores de estilos para traducir estilos comunes a un código estándar y reconocible por los navegadores | Implementación eficiente y completa del preprocesador (**SASS**, **LESS**, etc.), utilizando **partials, mixins y/o otras características útiles**. El código es limpio, optimizado y **compatible con navegadores**. El proceso está bien documentado. | Uso correcto del preprocesador con **partials y mixins**. El código es funcional y **compatible con navegadores modernos**, aunque no se aprovechan características avanzadas.   | Implementación parcial del preprocesador. Se usan partials o mixins de forma limitada. El código es funcional pero tiene margen de mejora en optimización.                      | Uso muy básico del preprocesador, con **errores significativos** y sin aprovechar características clave. El código no está optimizado y presenta redundancias. | Se ha intentado usar un preprocesador, pero su implementación es incorrecta, generando errores en los estilos o incompatibilidades en navegadores. | No se ha utilizado un preprocesador de estilos. El código presenta estilos redundantes, errores de compatibilidad y falta de optimización. |


**RA3**

| CE | 10 excelente | 8 notable | 6 bien | 4 necesita mejorar | 2 insuficiente | 0 no asiste |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| f) Se han realizado animaciones a partir de imágenes fijas. | Se han realizado de forma autonoma, adecuandose a las instrucciones del proyecto (transiciones, animaciones y transformaciones) con una animación optimizada y obteniendo un resultado excelente. | Se han realizado de forma autonoma, adecuandose a las instrucciones del proyecto (transiciones, animaciones y transformaciones) con una animación optimizada y obteniendo un resultado correcto. | Se han realizado con algún tipo de ayuda, adecuandose a las instrucciones del proyecto (transiciones, animaciones y transformaciones) con una animación con algún tipo de error y obteniendo un resultado correcto. | Se han realizado con algún tipo de ayuda, sin adecuandose a las instrucciones del proyecto (transiciones, animaciones y transformaciones) con una animación con algún tipo de error y obteniendo un resultado correcto. | Se han realizado con algún tipo de ayuda, sin adecuandose a las instrucciones del proyecto (transiciones, animaciones y transformaciones) con una animación con varios errores y obteniendo un resultado no optimo. | No asiste o no es evaluable |
| h) Se ha aplicado la guía de estilo | Se ha aplicado de forma excelente tanto en transiciones y animaciones | Se ha aplicado de forma correcta tanto en transiciones y animaciones | Se ha aplicado con algún error en transiciones y/o animaciones | Se ha aplicado con varios errores en transiciones y/o animaciones | Se ha aplicado con varios errores en transiciones y/o animaciones | No es evaluable o no asiste |
