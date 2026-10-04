---
language:
  - en
license: cc-by-4.0
task_categories:
  - tabular-classification
  - text-classification
  - text-generation
  - other
task_ids:
  - multi-class-classification
  - topic-classification
pretty_name: Billboard Hot 100 Number Ones (1958-2025)
size_categories:
  - 1K<n<10K
source_datasets:
  - extended|other-tidytuesday
tags:
  - music
  - billboard
  - hot-100
  - charts
  - musicology
  - music-information-retrieval
  - audio-features
  - lyrics
  - cultural-analysis
  - music-history
  - tidytuesday
  - fair-data
  - explicit-content
  - demographics
  - tabular
  - csv
configs:
  - config_name: default
    data_files:
      - split: billboard
        path: data/raw/billboard.csv
      - split: topics
        path: data/raw/topics.csv
---

# Billboard Hot 100 Number Ones (1958 – 2025)

## Dataset Summary

Este dataset reúne **información exhaustiva y estructurada sobre cada canción que alcanzó el puesto #1 en la lista Billboard Hot 100** de Estados Unidos, cubriendo el periodo comprendido entre el **4 de agosto de 1958** (con *"Poor Little Fool"* de Ricky Nelson) y el **11 de enero de 2025**.

El dataset fue compilado originalmente por **Chris Dalla Riva** como parte de la investigación para su libro *"Uncharted Territory: What Numbers Tell Us about the Biggest Hit Songs and Ourselves"* y su newsletter *"Can't Get Much Higher"*. Durante siete años, el autor escuchó y catalogó cada canción número uno, registrando una cantidad extraordinaria de información musical, comercial, demográfica, lírica y de audio features.

Esta versión ha sido **curada por Jen Richmond (R-Ladies Sydney)** y publicada como parte del proyecto **TidyTuesday** del 26 de agosto de 2025. Se distribuye en dos archivos complementarios:

- `billboard.csv`: dataset principal con 103 variables por canción.
- `topics.csv`: diccionario de los temas líricos utilizados en `billboard.csv`.

### Objetivo del análisis

Este proyecto forma parte del curso `Descubrimiento de conocimientos de datos complejos` y busca **estudiar la evolución del contenido explícito (`explicit`) en los hits #1 de Billboard** y su posible relación con:

1.  La **década** en la que la canción alcanzó el #1.
2.  El **perfil demográfico del artista** (sexo: `artist_male`; raza: `artist_white`, `artist_black`).
3.  El **perfil demográfico de los productores** (sexo: `producer_male`; raza: `producer_white`).
4.  El **éxito comercial** medido en semanas en el #1 (`weeks_at_number_one`) y rating crítico (`overall_rating`).

### Preguntas de investigación

Estas son las preguntas concretas que este análisis pretende responder:

1.  **Evolución temporal del contenido explícito:** ¿Cómo ha cambiado la proporción de canciones #1 con contenido explícito (`explicit = 1`) desde 1958 hasta 2025? ¿Se observa un aumento sostenido por década?

2.  **Artistas y explicit:** ¿Existe una diferencia significativa en la proporción de canciones explícitas entre artistas masculinos (`artist_male = 1`), femeninos (`artist_male = 0`) o mixtos (`artist_male = 2`)? ¿Se ha reducido esa brecha con el tiempo?

3.  **Raza del artista y explicit:** ¿Son los artistas negros (`artist_black = 1`) más propensos a tener hits #1 con contenido explícito que los artistas blancos (`artist_white = 1`)? ¿Cómo ha evolucionado esta relación por década?

4.  **Productores y explicit:** ¿Existe una correlación entre el perfil demográfico de los productores (`producer_male`, `producer_white`) y la presencia de contenido explícito en las canciones? ¿El cambio en la composición demográfica de los productores a lo largo del tiempo explica parte del aumento de contenido explícito?

5.  **Explicit y éxito comercial:** ¿Las canciones con contenido explícito tienen un rendimiento distinto en el chart que las no explícitas? Concretamente:
    - ¿Tienen más o menos `weeks_at_number_one`?
    - ¿Tienen mayor o menor `overall_rating`?
    - ¿Son más o menos divisivas (`divisiveness`)?

6.  **Interacción entre variables:** ¿Existe una interacción entre década, demografía (artistas y productores) y contenido explícito a la hora de predecir el éxito comercial de un hit #1?

7.  **Temas líricos y explicit:** ¿Qué temas líricos (`lyrical_topic`) están más asociados con contenido explícito? ¿Han cambiado estos temas por década?

8.  **Artefactos históricos:** ¿Cómo afectan eventos culturales clave (aparición del hip-hop en los 80-90, era del streaming post-2010) al contenido explícito y al perfil demográfico de los artistas y productores #1?

### Detalles clave

| Atributo | Valor |
| :--- | :--- |
| **Autor original** | Chris Dalla Riva |
| **Curaduría TidyTuesday** | Jen Richmond (R-Ladies Sydney) |
| **Fuente** | [TidyTuesday 2025-08-26](https://github.com/rfordatascience/tidytuesday) |
| **Idioma principal** | Inglés (con títulos y letras en otros idiomas) |
| **Tamaño** | 347 canciones × 103 variables |
| **Periodo** | 1958-08-04 → 2025-01-11 |
| **Formato** | CSV (UTF-8) |
| **Licencia** | CC BY 4.0 |
| **Contexto académico** | Proyecto de `Descubrimiento de conocimientos de datos complejos` |

---

## Supported Tasks and Leaderboards

| Tarea | Descripción |
| :--- | :--- |
| **Clasificación de contenido explícito** | Predecir `explicit` a partir de features musicales, demográficas y temporales. |
| **Análisis de tendencias temporales** | Estudiar la evolución de BPM, tonalidad, energía, "happiness", duración y contenido explícito por década. |
| **Predicción de éxito comercial** | Modelar `weeks_at_number_one` o `overall_rating` a partir de metadatos, demografía y features musicales. |
| **Análisis demográfico** | Estudiar la representación de género (`artist_male`, `producer_male`), raza (`artist_white`, `artist_black`, `producer_white`) y su evolución temporal. |
| **Topic modeling sobre letras** | Detectar tópicos recurrentes en `lyrics` y cruzarlos con `lyrical_topic` y `explicit`. |
| **Análisis de sentimiento** | A partir de `happiness`, `lyrical_topic` y `lyrics`. |
| **Análisis de estructura musical** | Estudiar la evolución de `song_structure`, `time_signature`, `length_sec`. |
| **Análisis de instrumentación** | Detectar qué instrumentos han sido más frecuentes en cada década. |
| **Análisis de asociaciones culturales** | Estudiar la relación entre canciones y películas, TV, teatro o Eurovisión. |

No existe un leaderboard oficial asociado, pero se anima a la comunidad a publicar resultados en el Hub.

---

## Languages

El dataset está compuesto principalmente por **textos en inglés** (`song`, `artist`, `lyrics`), reflejando el predominio anglosajón del chart estadounidense. Sin embargo, contiene también:

- **Italiano:** *"Nel Blu Dipinto Di Blu"* (Domenico Modugno, 1958).
- **Español:** *"La Bamba"* (Los Lobos, 1987), *"Macarena"* (Los Del Rio, 1996), *"Despacito"* (Luis Fonsi & Daddy Yankee, 2017).
- **Francés:** *"Dominique"* (The Singing Nun, 1963).
- **Japonés:** *"Sukiyaki"* (Kyu Sakamoto, 1963).
- **Alemán:** *"99 Luftballons"* (Nena).

La columna `foreign_language` permite filtrar los registros con idiomas distintos del inglés.

---

## How to Use

### Carga con `datasets` (Hugging Face)

```python
from datasets import load_dataset

dataset = load_dataset("<<TU_USUARIO_HF>>/billboard-number-one-hits")

billboard = dataset["billboard"]
print(billboard[0])
print(f"Total de canciones: {billboard.num_rows}")

topics = dataset["topics"]
print(topics[0])