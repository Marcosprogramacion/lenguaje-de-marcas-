# All Anime - Catálogo de Anime y Manga

Proyecto web dedicado a presentar un catálogo estructurado de series de anime y mangas destacados, extrayendo y organizando datos desde la API oficial de **MyAnimeList**.

---

## 1. Integración con la API y Estructura de Datos (JSON)

Los datos mostrados en la plataforma han sido obtenidos utilizando la **API de MyAnimeList**. Para facilitar su consumo en la interfaz web, los datos se han estructurado en un archivo JSON siguiendo el esquema que se describe a continuación.

### Tabla de Campos del JSON

| Campo | Tipo de Dato | Descripción | Ejemplo / Valores posibles |
| :--- | :--- | :--- | :--- |
| `titulo` | `String` | Nombre principal del anime o manga. | `"Fullmetal Alchemist: Brotherhood"` |
| `puntuacion` | `Float` | Calificación media del título en MyAnimeList (sobre 10). | `9.10` |
| `episodios` | `Integer` | Número total de episodios (exclusivo de anime). | `64` |
| `capitulos` | `Integer` / `String` | Número total de capítulos publicados (exclusivo de manga). | `162` o `"380+"` |
| `estado` | `String` | Estado de emisión o publicación del título. | `"Finalizado"`, `"En publicación"`, `"Pausado"` |
| `imagen` | `String` | Ruta local o URL hacia la portada del título. | `"assets/imagenes/fullmetal.webp"` |
| `ficha` | `String` / `Null` | Ruta a la página de detalle individual (si está disponible). | `"fichas/fullmetal_Alchemist.html"` o `null` |

---

## 2. Estructura y Contenido del Sitio Web

El proyecto se divide en las siguientes páginas y componentes principales:

*   **Página Principal (`index.html`)**: Página de bienvenida e introducción general al portal.
*   **Catálogo (`catalogo.html`)**: Página principal del catálogo que agrupa:
    *   **Encabezado (`<header>`)**: Navegación principal, enlace a inicio e iconos de perfil, ajustes y contacto.
    *   **Sección Informativa (`<article>`)**: Breve descripción del objetivo del catálogo.
    *   **Sección "Animes Destacados" (`<article>`)**: Tarjetas (`<section>`) con la información resumida de cada serie (puntuación, episodios, estado) y enlaces a fichas detalladas.
    *   **Sección "Mangas Destacados" (`<article>`)**: Tarjetas de obras impresas destacadas (puntuación, capítulos, estado).
    *   **Pie de página (`<footer>`)**: Derechos de autor e información legal.
*   **Fichas de Detalle (`fichas/*.html`)**: Páginas individuales (como `fullmetal_Alchemist.html`, `Frieren.html`, `Berserk.html`) con información ampliada y sinopsis de cada obra.

---

## 3. Decisiones de Marcado HTML

Durante el desarrollo de la estructura semántica se evaluaron distintas alternativas antes de tomar las decisiones finales:

1.  **Agrupación de títulos (`<article>` vs `<section>`)**:
    *   *Duda*: Dudaba entre usar `<section>` para toda la página o `<article>` para los bloques contenedores.
    *   *Elección*: Se optó por usar `<article>` para agrupar las grandes temáticas ("Animes destacados" y "Mangas destacados") ya que cada bloque representa una unidad temática autocontenida, y dentro de ellos usar `<section>` para representar la ficha o tarjeta individual de cada obra.

2.  **Menú de navegación del encabezado (`<ul>` con imágenes vs enlaces directos `<a href>` con iconos)**:
    *   *Duda*: No estaba seguro de si incluir las imágenes del menú dentro de una lista no ordenada `<ul>` o dejarlas como elementos flotantes o enlaces simples.
    *   *Elección*: Se seleccionó `nav > ul > li > img` para cumplir con los estándares semánticos de navegación en HTML5, estructurando las opciones de usuario (perfil, ajustes, contacto) como una lista ordenada de elementos interactivos.

3.  **Encabezados jerárquicos (`<h2>` vs `<h3>`)**:
    *   *Duda*: Existía la duda de si los nombres de cada anime/manga debían llevar `<h2>` o `<h3>`.
    *   *Elección*: Se reservó el `<h2>` para los títulos de sección principal (*"Animes destacados"*, *"Mangas destacados"*) y se asignó `<h3>` a cada obra individual, garantizando un árbol semántico y accesible sin saltos de nivel jerárquico.

---

## 4. Validación del Código

El marcado HTML ha sido verificado mediante el servicio de validación oficial **W3C Markup Validation Service**.

*   **Resultado de la validación**: Aprobado sin errores sintácticos severos.
*   **Correcciones aplicadas durante la validación**:
    *   Inclusión y verificación de atributos `alt` descriptivos en todas las etiquetas `<img>` para garantizar el cumplimiento de las pautas de accesibilidad (WCAG).
    *   Verificación del cierre correcto de etiquetas semánticas y codificación `UTF-8`.

---

## 5. Historial de Commits (Fase 1)

Para asegurar la trazabilidad del desarrollo, se han realizado los siguientes commits mínimos requeridos antes de etiquetar la entrega:

1. `feat: estructura inicial del HTML y encabezado de la pagina`
2. `feat: anadida seccion de animes destacados con datos de la API`
3. `feat: anadida seccion de mangas destacados y enlaces a fichas`
4. `docs: creacion del archivo JSON con los datos extraidos de MyAnimeList`
5. `fix: correccion de semantica HTML y validacion W3C`
6. `docs: finalizacion del archivo README con documentacion completa`

> **Entrega y Etiquetado:**
> El último commit ha sido marcado con la etiqueta **`fase-1`** y subido al repositorio remoto de GitHub:
> ```bash
> git tag fase-1
> git push origin fase-1
> ```