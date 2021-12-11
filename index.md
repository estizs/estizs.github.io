## Descripción del proyecto

Con este proyecto queremos estudiar el reflejo de la sociedad en las redes sociales y el efecto de las mismas en el caso de las elecciones presidenciales de Estados Unidos de 2016. Además, analizar cómo Twitter se ha consolidado como una herramienta esencial para la campaña electoral. Partimos de la hipótesis de que durante el periodo electoral los tweets son representativos de los resultados finales. Es decir, que un mayor flujo de tweets positivos referentes a un candidato representa el apoyo que luego tendrá en los resultados. Asimismo, un flujo de tweets negativos, significará un menor apoyo hacia un candidato.

### Necesidad de Big Data

En los últimos diez años, el número de usuarios mensuales de Twitter ha aumentado en un 372%. A raíz de esto contamos con un dataset del orden de millones de tweets. Es usual que el tráfico de tweets aumente considerablemente durante sucesos importantes. Esto ocurre también durante el periodo electoral de EEUU. Esto constituye un conjunto de datos tan masivo que es necesario el uso de herramientas de procesamiento de datos más potentes como el Cloud.

![](https://github.com/oscarlparra/USA_Election_Tweet_Analysis/blob/master/datasets/usuarios%20twitter.png)

### Dataset

El dataset lo hemos obtenido de la página data.world, que contiene millones de datasets públicos para que cualquier persona pueda hacer uso de ellos. [Nuestro dataset](https://data.world/alexfilatov/2016-usa-presidential-election-tweets/workspace/project-summary?agentid=alexfilatov&datasetid=2016-usa-presidential-election-tweets) en concreto contiene tweets de las elecciones presidenciales de EEUU de 2016. Hay dos versiones del dataset, uno de 17.3MB y otro de 13.17GB. Para nuestras pruebas en local hemos usado el dataset de 17.3MB, que contiene 100k tweets.

La estructura del dataset es la siguiente: id, candidate_id, tweet_id, polarity, subjectivity, retweet_count, favorite_count, device, retweeted_status_id, lang, state, tweet_text, created_at, inserted_at, updated_at, tw_user_id, latitude, longitude

Para el análisis, hemos prescindido de algunas columnas ya que no aportan información relevante. Así que la estructura que realmente hemos utilizado es la siguiente: candidate_id, polarity, state, created_at. 

**candidate_id:** contiene un número del 1 al 4. Las correspondencias de id-nombre son las siguientes:

* ID 1: Hillary Clinton
* ID 2: Donald Trump
* ID 3: Barack Obama
* ID 4: Bernie Sanders


**polarity:** la polaridad está ya calculada usando [Python NTLK open source server](https://github.com/topics/nltk-python), el que se ha usado es en conctreto un analizador de sentimiento que utiliza TextBlob: [https://github.com/sguignot/textblob-api-server](https://github.com/sguignot/textblob-api-server). La polaridad es un número entre -1 y 1, cuanto más cercana a -1, implica una opinión negativa y 1 positiva.


**state:** contiene abreviaciones tanto de estados de EEUU como de países.


**created_at:** fecha en la que se publicó el tweet.

### Objetivos

El principal objetivo del proyecto es demostrar que el número de tweets referentes a un candidato guarda relación con los resultados obtenidos en las elecciones. Para ello, hemos analizado los tweets en función de su polaridad para hacer un mapa que represente la imagen que tienen los usuarios de Twitter de cada candidato en cada estado. Vamos a comparar estos datos obtenidos con los resultados reales para hacer el análisis estadístico.

Otro de los objetivos de este proyecto es reafirmar que es necesario el uso de un procesamineto de datos más potente. Para ello vamos a realizar pruebas sobre un ordenador de 4 núcleos y sobre un clúster en Google Cloud. 

### Desarrollo

Hemos desarrollado nuestro programa con spark. Para poder ejecutarlo el usuario deberá tener instalado en su ordenador pyspark. Para instalarlo hemos seguido las instrucciones de la siguiente [página](https://medium.com/tinghaochen/how-to-install-pyspark-locally-94501eefe421).

Lo primero que realizamos fue la limpieza de los datos para quedarnos con las columnas que nos interesaban. Estas son: 'candidate_id', 'polarity', 'subjectivity', 'state', 'created_at'. Seguidamente descartamos las filas que contenían valores nulos en las columnas 'state' o 'created_at'. Los datos fueron recogidos entre agosto de 2016 y febrero de 2017 cuando Trump asumió el cargo. Filtramos los tweets que pertenecían a los estados de EEUU, en total 51 estados los cuales son: ['OH', 'AZ', 'MO', 'TN', 'ID', 'MA', 'LA', 'CA', 'SC', 'MN', 'NJ', 'DC', 'OR', 'VA', 'RI', 'KY', 'WY', 'NH', 'MI', 'NV', 'WI', 'CT', 'NE', 'MT', 'NC', 'VT', 'MD', 'DE', 'IL', 'ME', 'WA', 'ND', 'MS', 'AL', 'IN', 'IA', 'NM', 'PA', 'SD', 'NY', 'TX', 'WV', 'GA', 'KS', 'FL', 'CO', 'AK', 'AR', 'OK', 'UT', 'HI'].

```python
df.select('candidate_id', 'polarity', 'subjectivity', 'state', 'created_at').filter(df.state.isNotNull() & df.created_at.isNotNull()).filter(df.state.isin(li))
```
Para visualizar los resultados con un mapa, hemos utilizado la librería Plotly que es una librería gráfica que sirve para hacer mapas. Para instalarlo es necesario ejecutar el siguiente comando:

```console
$ pip install plotly==5.4.0
```

### Resultados

[Mapas, resultados]
<a href="https://www.270towin.com/maps/2016-actual-electoral-map"><img src="https://www.270towin.com/map-images/2016-actual-electoral-map.png" width="800"></a>

### Rendimiento: Local vs Cloud

[Análisis del rendimiento, dataset 13GB]

### Conclusiones

[Aquí las conclusiones]
