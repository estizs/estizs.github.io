## Descripción del proyecto

Reflejo de la sociedad en las redes sociales y el efecto de las mismas en el caso de las elecciones presidenciales de Estados Unidos de 2016. Analizar cómo Twitter se ha consolidado como una herramienta esencial para la campaña electoral. Partimos de la hipótesis de que durante el periodo electoral los tweets son representativos de los resultados finales.

### Necesidad de Big Data

[Aquí la descripción del proyecto.]

### Dataset

* De dónde lo hemos sacado (fuente)
* Contenido (formato) --> df en vez de rdd
* Tamaño --> 200Mb vs 13Gb

### Objetivos

* Limpiar dataset --> candidate_id, polarity, subjectivity (just in case), state (quedarnos con los tweets con estado), created_at (nos quedamos desde agosto-nov)
* Para cada estado mirar cuál es candidato con mayor polaridad (el fav)
* Para cada estado mirar cuál es candidato con menor polaridad (menos fav)
* Comparar los resultados de arriba con los resultados reales
* Hacer mapa interactivo

### Desarrollo

[Código, explicación de las herramientas]

### Resultados

[Mapas, resultados]
<a href="https://www.270towin.com/maps/2016-actual-electoral-map"><img src="https://www.270towin.com/map-images/2016-actual-electoral-map.png" width="800"></a>

### Rendimiento: Local vs Cloud

[Análisis del rendimiento, dataset 13GB]

### Conclusiones

[Aquí las conclusiones]
