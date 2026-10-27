# Accesibilidad territorial a servicios de salud en Villa Jardín — Partido de Lanús

Análisis geográfico de la distribución de barrios populares en Argentina y de la accesibilidad a centros de salud en Villa Jardín (Lanús), a partir de datos oficiales del **ReNaBap** y herramientas geoespaciales en R.

## 📌 Contexto y pregunta de investigación

En Argentina, se estima que uno de cada diez habitantes reside en un barrio popular. La exclusión social y la segregación territorial incrementan la desigualdad que ha caracterizado al país durante las últimas décadas. Los barrios populares se caracterizan por:

- Altos niveles de hacinamiento.
- Falta de acceso a servicios básicos (agua, electricidad, cloacas y gas), con predominio de conexiones informales.
- Prevalencia de la autoconstrucción habitacional y tenencia irregular de la tierra, frecuentemente en zonas expuestas a riesgos ambientales.

Un cambio crucial ocurrió en **2016** con el inicio del relevamiento del **ReNaBap**, que impulsó un marco normativo para definir y delimitar estos territorios, y sistematizó datos para crear estadísticas públicas sobre estas familias y sus tierras.

Este proyecto identifica y cuantifica los barrios populares a nivel nacional, muestra su distribución y selecciona el **partido de Lanús** para analizar la accesibilidad a servicios de salud en el barrio **Villa Jardín**.

Las preguntas que guían el trabajo son:

1. ¿Cuál es la localidad con mayor predominio de barrios populares y, dentro de ella, cuál es el barrio con mayor cantidad de familias y viviendas?
2. ¿Cuál es el nivel de accesibilidad a los centros de salud del barrio seleccionado?

## 📂 Fuente de datos

- **ReNaBap** (Registro Nacional de Barrios Populares) — datos abiertos.
- **OpenStreetMap** — descarga de información geoespacial vía `osmdata`.
- **Bases de datos espaciales** para mapas base y ruteo.

## 🎯 Objetivos

- Identificar y cuantificar los barrios populares a nivel nacional.
- Analizar la distribución de barrios populares por provincia y localidad.
- Seleccionar el partido de Lanús y caracterizar sus barrios populares.
- Medir la accesibilidad a centros de salud desde Villa Jardín mediante isócronas y ruteo peatonal.

## 🛠️ Herramientas y técnicas utilizadas

- **Lenguaje:** R
- **Manipulación de datos:** `tidyverse`, `dplyr`, `lubridate`
- **Datos espaciales:** `sf` (unión de datasets espaciales y tradicionales, transformación a objetos espaciales)
- **Descarga de datos geoespaciales:** `osmdata` (OpenStreetMap)
- **Mapas base:** `ggmap`
- **Mapas interactivos:** `leaflet`
- **Geolocalización:** `tidygeocoder`
- **Isócronas y ruteo peatonal:** `osrm`
- **Visualización:** `ggplot2`
- **Documento:** R Markdown con salida en HTML

## 📁 Estructura del repositorio

```
.
├── README.md
├── Proyecto_Final_Ciencia_Datos_II.Rmd # Código fuente del análisis
└── Proyecto_Final_Ciencia_Datos_II.html # Documento renderizado (abrir en el navegador)
```

## ▶️ Ver el análisis completo

👉 [Hacé clic acá para ver el trabajo renderizado](https://siguax.github.io/accesibilidad-villa-jardin-lanus/Proyecto_Final_Ciencia_Datos_II.html)

## 🛠️ Cómo visualizar el proyecto

1. Descargá o cloná este repositorio:
   ```bash
   git clone https://github.com/Siguax/accesibilidad-villa-jardin-lanus.git
   ```
2. Abrí el archivo **`Proyecto_Final_Ciencia_Datos_II.html`** en cualquier navegador web (Chrome, Firefox, Edge).
   - No necesitás instalar R para ver los resultados.

3. Si querés reproducir el análisis, abrí el archivo Proyecto_Final_Ciencia_Datos_II.Rmd en RStudio y ejecutá **Knit**.

## 📊 Principales hallazgos

- La mayor distribución de barrios populares se concentra en la provincia de Buenos Aires, seguida por Santa Fe y Chaco. La tipología predominante son los asentamientos informales.
- En la provincia de Buenos Aires, la Zona Sur alberga las localidades con mayor cantidad de barrios populares (más de 3000 familias por barrio): Lomas de Zamora, seguida por Quilmes. En la Zona Oeste destaca General San Martín.
- Lanús Oeste (partido de Lanús) concentra la mayoría de barrios populares, creados en la década de 1970. Dentro de esa localidad, Villa Jardín alberga la mayor cantidad de familias y viviendas, y presenta la mayor densidad de población aunque no la mayor superficie.
- Villa Jardín cuenta con 6 centros o unidades sanitarias a menos de 20 minutos de caminata. La más cercana es la Unidad de Salud Villa Jardín (2,82 minutos / 212 metros), y la más lejana es el Centro de Salud Villa Giardino (1,31 km / ~18 minutos a pie).

## 📚 Temas del curso aplicados

- Información geográfica y mapas.
- Análisis y geoprocesamiento de datos.
- Detección de patrones espaciales y temporales.
- Descarga de datos espaciales de repositorios online.
- Geolocalización de información y análisis de movimientos en la ciudad.

## 👩‍💻 Autora
**Silvia Prevettoni**
- GitHub: [@Siguax](https://github.com/Siguax)
- LinkedIn: [silvia-prevettoni](https://www.linkedin.com/in/silvia-prevettoni)
- Email: [silvia.prevettoni@gmail.com](mailto:silvia.prevettoni@gmail.com)