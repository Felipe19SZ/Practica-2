
# Projecto: Spotify vs YouTube: análisis de popularidad musical con Power BI

A través de un dashboard interactivo fue posible analizar la relación entre el desempeño de las canciones en Spotify (streams) y YouTube (vistas), así como explorar las características del audio. Además, se determinó si existe una asociación entre estas variables y la popularidad, comparando el rendimiento de los singles frente a los álbumes.

## Objetivo del proyecto

Para poder analizar el comportamiento cruzado de las canciones entre Spotify y YouTube fue necesario responder las siguientes preguntas de negocio:

    1.- ¿Qué artistas dominan cada plataforma y coinciden en ambas?
    2.- ¿Qué características de audio (energy, danceability, acousticness, tempo) están más asociadas a la popularidad?
    3.- ¿Es más rentable en streams lanzar un single o un álbum completo?
    4.- ¿Una canción exitosa en Spotify lo es también en YouTube?
## Fuente de datos

Dataset: *Spotify and YouTube* - Kaggle, por Salvatore Rastelli[^1].

En este dataset contiene estadísticas del Top 10 de canciones de distintos artistas, combinando:

+ Métricas de audio de Spotify (Danceability, Energy, Tempo, Acousticness, entre otras).
+ Métricas de consumo en Spotify (Stream).
+ Metricas de consumo en YouTube (Views, Likes, Comments, Licensed, official_video).

[^1] Nota: Los datos corresponden a un snapshot tomado el **07 de febrero del 2023**.
## Metodología

**1. Limpieza de datos (Power Query)**

+ Eliminación de duplicados por combinación Track + Artist.
+ Estandarización de texto (recorte de espacios, capitalización).
+ Tratamiento de valores nulos en Stream y Views.

**2. Transformación de datos**

+ Conversión de Duration_ms a minutos.
+ Normalización de booleanos (Licensed, official_video) a Sí/No.
+ Creación de columna Plataforma_dominante (comparando Stream vs Views).
+ Categorización de canciones por rango de Tempo, Energy, y Danceability (Alto/Medio/Bajo).

**3. Modelado (DAX)**

+ Medidas de agregación: Total_streams, Total_views, Total_likes, Num_artistas, Num_canciones.
+ Medidas de ratio: Radio_engagement, Radio_cross-platform.
+ Medidas de ranking: RANKX para Top N artistas.
+ Promedios segmentados por nivel de popularidad y tipo de lanzamiento.
    
**4. Visualización (Power BI)**

+ 4 páginas: Resumen ejecutivo, Análisis de audio, Comparativa Spotify vs YouTube, Tooltip personalizado.
+ Segmentadores interactivos por artistas, tipo de lanzamiento y plataforma dominante.
+ Matriz de correlación con formato condicional (hearmap).
+ Gráfico de dispersión con tooltip personalizado por canción.

## Capturas del dashboard

**Pagina 1 - Resumen ejecutivo**

Practica-2/Página 1 — Resumen ejecutivo.png

**Pagina 2 - Análisis de audio**

Página 2 — Análisis de audio.png

[**Página 3 — Comparativa Spotify vs YouTube**]

(Página 3 — Comparativa Spotify vs YouTube.png)

## Insights principales

Con base en el análisis, a continuación se detallaran los principales hallazgos con base en el dashboard interactivo. Estos resultados permiten comprender de mejor manera las relaciones y pratrones identificados entre el desempeño de las canciones, sus características de audio y su popularidad en las plataformas analizadas (YouTube y Spotify):

- **El dominio de plataformas no recae en los mismos artistas.** Solo algunos artistas (Ed Sheeran, Justin Bieber, Coldplay, Bruno Mars) aparecen en las dos plataformas en el Top 10, a partir de esto lo que sugiere audiencia y dinámicas de consumo distintas entre plataformas.
- **Las canciones más populares comparten un patrón sonoro.** Cuanto mayor Energy y Danceability, menor Acousticness, lo que se asocia con un mayor nivel de popularidad.
- **Existe un tempo "óptimo".** La mayoría de las canciones exitosas se concentran entre los 100-140 BPM, el cual es el rango típico del pop/dance comercial.
- **Los álbumes generan más streams promedio que los singles.** Los álbumes alcanzan 150.26M contra los 101.99M de los singles, esto es posiblemente ocasionado por el efecto de playlists o el algoritmo de reproducción.
- **El engagement (likes+comentarios/vistas) es consistentemente bajo,** esto se ve reflejado en el patrón típico de consumo pasivo de las plataformas de video.
## Recomendaciones

Considerando los patrones identificados en el análisis, a continuación se proponen algunas recomendaciones estratégicas que podrían apoyar decisiones relacionadas con la promoción y distribución musical en las distintas plataformas. 

- Evaluar el lanzamiento en formato álbum como estrategia de streams sostenidos, usando singles como adelantos tácticos.
- Diseñar estrategias de marketing diferenciadas por plataforma, dado que el éxito no es intercambiable entre Spotify y YouTube.

## Limitaciones del análisis

Ahora es importante considerar que el presente análisis presenta algunas limitaciones que se deben de tomar en cuenta al momento de interpretar los resultados y las recomendaciones derivadas del mismo.

- El dataset es un snapshot del 07 de febrero del 2023 - lo cual no refleja las tendencias a lo largo del tiempo.
- Solo incluye el Top 10 de canciones por artistas, lo cual no introduce un sesgo de selección.
- Existen valores faltantes en Stream y Views para algunas canciones (marcados como "Sin datos").
- Las relaciones encontradas son correlacionales, no causales - no se controlaron variables como género músical, presupuesto de marketing o fecha de lanzamiento.
- No se incluye un análisis de series temporales ni comparación con charts oficiales externos.
## Herramientas utilizadas

- **Power BI Desktop -** modelado de datos, DAX y visualización.
- **Power Query -** limpieza y transformación de datos.
- **Kaggle -** fuente del dataset.
