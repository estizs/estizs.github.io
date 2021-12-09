## Descripción del proyecto

Con este proyecto queremos estudiar el reflejo de la sociedad en las redes sociales y el efecto de las mismas en el caso de las elecciones presidenciales de Estados Unidos de 2016. Además, analizar cómo Twitter se ha consolidado como una herramienta esencial para la campaña electoral. Partimos de la hipótesis de que durante el periodo electoral los tweets son representativos de los resultados finales. Es decir, que un mayor flujo de tweets positivos referentes a un candidato representa el apoyo que luego tendrá en los resultados. Asimismo, un flujo de tweets negativos, significará un menor apoyo hacia un candidato.

### Necesidad de Big Data

En los últimos diez años, el número de usuarios mensuales de Twitter ha aumentado en un 372%. A raíz de esto contamos con un dataset del orden de millones de tweets. Es usual que el tráfico de tweets aumente considerablemente durante sucesos importantes. Esto ocurre también durante el periodo electoral de EEUU. Esto constituye un conjunto de datos tan masivo que es necesario el uso de herramientas de procesamiento de datos más potentes como el Cloud.

### Dataset

* De dónde lo hemos sacado (fuente)
* Contenido (formato) --> df en vez de rdd
* Tamaño --> 200Mb vs 13Gb
El dataset lo hemos obtenido de la página data.world, que contiene millones de datasets públicos para que cualquier persona pueda hacer uso de ellos. [Nuestro dataset](https://data.world/alexfilatov/2016-usa-presidential-election-tweets/workspace/project-summary?agentid=alexfilatov&datasetid=2016-usa-presidential-election-tweets) en concreto contiene tweets de las elecciones presidenciales de EEUU de 2016. Hay dos versiones del dataset, uno de 17.3MB y otro de 13.17GB. Para nuestras pruebas en local hemos usado el dataset de 17.3MB, que contiene 100k tweets.

La estructura del dataset es la siguiente:

| id | candidate_id | tweet_id | polarity | subjectivity | retweet_count | favorite_count | device | retweeted_status_id | lang | state | tweet_text | created_at | inserted_at | updated_at | tw_user_id | latitude | longitude |
--------------------------------------------------------------

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
