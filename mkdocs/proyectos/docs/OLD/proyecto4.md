---
hide:
  - navigation
---
# **Proyecto 4: Testing en producción**
## **1. Descripción del proyecto**
### Introducción
En este proyecto, aplicarás tus conocimientos sobre usabilidad y optimización para analizar y mejorar un sitio web existente. A través de pruebas manuales y automáticas, identificarás problemas en el rendimiento, navegación y experiencia de usuario, implementando mejoras justificadas para optimizar la interfaz web.

#### Testing de Usabilidad de una Web
Una vez desarrollado el proyecto web, se realizará un **testing de usabilidad** para evaluar la interfaz. La prueba debe ser visible a través de una **URL** (por ejemplo, **GitHub Pages** o servidor propio).


## 2. Objetivos
- Reconocer la **importancia del uso de estándares** en la creación de documentos.
- Verificar la **facilidad de navegación** y **usabilidad** de una página web.
- Utilizar herramientas y técnicas para realizar **tests de usabilidad** en diferentes dispositivos y navegadores.
- Evaluar la **usabilidad** y accesibilidad del interfaz web en entornos de producción.

---

## 3. Resultados de aprendizaje y Criterios de evaluación
**RA6**: Desarrolla interfaces web amigables analizando y aplicando las pautas de usabilidad.

- **CE.c)** Se ha valorado la importancia del uso de estándares en la creación de documentos Web.
- **CE.d)** Se ha verificado la facilidad de navegación de un documento Web mediante distintos periféricos.
- **CE.f)** Se ha verificado la usabilidad del interfaz Web creado en diferentes navegadores y tecnologías.

---

## 4. Prueba

### Proceso de la Práctica

1. **Evaluación inicial de estándares y navegación**
    - Elige el proyecto de un/a compañero/a.
    - Analiza los **estándares empleados** en el desarrollo:
        - ¿Qué estándares se han aplicado correctamente?
        - ¿Cuáles no cumplen con las pautas de usabilidad?
    - Evalúa la **facilidad de navegación** del sitio web con diferentes periféricos (ratón, teclado, pantalla táctil).
    - Realiza una reflexión final sobre la importancia de los estándares y la navegación intuitiva.
2. **Pruebas de usabilidad y velocidad con herramientas automáticas**: Utiliza las siguientes herramientas para evaluar la **usabilidad y rendimiento** del sitio web:
   - **[WebPageTest](https://webpagetest.org)**:
      - Realiza el test en al menos **2 navegadores diferentes** (home).
      - Evalúa la **navegación** en al menos **2 dispositivos** (listado y producto). 
   - **[PageSpeed Insights](https://pagespeed.web.dev/)**:  
      - Analiza al menos **3 páginas clave**: home, listado y producto.
      - Identifica los **elementos de mejora** y explica las recomendaciones.
   - **Optimización con Lighthouse**:
      - Evalúa el rendimiento del sitio web utilizando **Lighthouse** en Chrome DevTools. Mide y analiza los siguientes parámetros:
         - **Largest Contentful Paint (LCP):** tiempo que tarda en renderizarse el elemento más grande visible.
         - **Interaction to Next Paint (INP):** latencia en la interacción con elementos interactivos.
         - **Cumulative Layout Shift (CLS):** estabilidad visual del contenido durante la carga.
         - **First Contentful Paint (FCP):** tiempo hasta que se muestra el primer elemento visual.
         - **First Input Delay (FID):** tiempo de respuesta a la primera interacción del usuario.
         - **Time to First Byte (TTFB):** tiempo hasta recibir el primer byte del servidor. 
     - Documenta los resultados obtenidos y realiza recomendaciones específicas para optimizar cada parámetro medido. 
   - **Evaluación con Ghost Inspector**
      - Realiza un testeo automatizado con **Ghost Inspector** para comprobar la navegación general y los procesos críticos del sitio web. 
      - Adjunta el **video generado** y analiza los resultados. Por ejemplo, presta atención a posibles fallos como botones inactivos, enlaces rotos o tiempos de carga excesivos. 
      - Una guía visual sencilla podría consistir en comparar la salida del testeo con el comportamiento esperado (por ejemplo, verificar si los pasos automatizados coinciden con el flujo de navegación diseñado).
---

## 5.Entrega Final
Debéis entregar en un repositorío de GitHub:

- **Documento** con el informe completo, que incluya:
    - Evaluación de estándares y navegación.
    - Resultados y explicación de los tests automáticos.
    - Resultados y explicación del test con Ghost Inspector.
    - Reflexiones finales sobre la **usabilidad** y navegación del sitio web.
- **Archivos generados** necesarios para la justificación.

**¡Ánimo! 🖖**

---

### Anexo: Herramientas Recomendadas
- **WebPageTest**: [https://webpagetest.org](https://webpagetest.org)
- **PageSpeed Insights**: [https://pagespeed.web.dev/](https://pagespeed.web.dev/)
- **WAVE**: [https://wave.webaim.org](https://wave.webaim.org)
- **Lighthouse**: Disponible en Chrome DevTools.
- **Ghost Inspector**: [https://ghostinspector.com](https://ghostinspector.com)  

## 6.Rúbrica de Evaluación.

### **Criterio CE.c: Valoración de estándares en la creación de documentos Web**
| Nivel | Descripción                                                                |
|-------|----------------------------------------------------------------------------|
| 10    | Identifica y aplica correctamente todos los estándares de la web.          |
| 8     | Identifica la mayoría de los estándares con algunas aplicaciones erróneas. |
| 6     | Reconoce algunos estándares, pero con errores frecuentes en su aplicación. |
| 4     | Muestra un conocimiento muy limitado de los estándares aplicados.          |
| 0     | No identifica ni aplica los estándares requeridos.                         |

### **Criterio CE.d: Verificación de la facilidad de navegación con distintos periféricos**
| Nivel | Descripción                                                                 |
|-------|-----------------------------------------------------------------------------|
| 10    | Comprueba exhaustivamente la navegación con distintos periféricos y reporta resultados claros. |
| 8     | Realiza pruebas en la mayoría de periféricos, con resultados satisfactorios. |
| 6     | Pruebas parciales y con documentación limitada.                             |
| 4     | Pruebas mínimas y resultados poco documentados.                             |
| 0     | No realiza pruebas con periféricos.                                         |


