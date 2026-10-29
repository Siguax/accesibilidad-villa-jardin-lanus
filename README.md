# 🗺️ Accesibilidad territorial a servicios de salud en Villa Jardín — Partido de Lanús

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Ver%20an%C3%A1lisis-brightgreen)](https://siguax.github.io/accesibilidad-villa-jardin-lanus/Proyecto_Final_Ciencia_Datos_II.html)
[![R](https://img.shields.io/badge/R-4.x-276DC3?logo=r&logoColor=white)](https://www.r-project.org/)
[![sf](https://img.shields.io/badge/sf-geoespacial-blue)](https://r-spatial.github.io/sf/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> Análisis geográfico de la distribución de barrios populares en Argentina y de la accesibilidad a centros de salud en Villa Jardín (Lanús), a partir de datos oficiales del **ReNaBap** y herramientas geoespaciales en R.

## 📌 Contexto y pregunta de investigación

En Argentina, se estima que **uno de cada diez habitantes reside en un barrio popular**. La exclusión social y la segregación territorial incrementan la desigualdad que ha caracterizado al país durante las últimas décadas. Los barrios populares se caracterizan por:

- Altos niveles de hacinamiento.
- Falta de acceso a servicios básicos (agua, electricidad, cloacas y gas), con predominio de conexiones informales.
- Prevalencia de la autoconstrucción habitacional y tenencia irregular de la tierra, frecuentemente en zonas expuestas a riesgos ambientales.

Un cambio crucial ocurrió en **2016** con el inicio del relevamiento del **ReNaBap**, que impulsó un marco normativo para definir y delimitar estos territorios, y sistematizó datos para crear estadísticas públicas sobre estas familias y sus tierras.

Este proyecto identifica y cuantifica los barrios populares a nivel nacional, muestra su distribución y selecciona el **partido de Lanús** para analizar la accesibilidad a servicios de salud en el barrio **Villa Jardín**.

### Preguntas de investigación

1. ¿Cuál es la localidad con mayor predominio de barrios populares y, dentro de ella, cuál es el barrio con mayor cantidad de familias y viviendas?
2. ¿Cuál es el nivel de accesibilidad a los centros de salud del barrio seleccionado?


## 📂 Fuente de datos

- **ReNaBap** (Registro Nacional de Barrios Populares) — datos abiertos en formato GeoPackage.
- **Establecimientos de salud públicos** — datos abiertos del Gobierno de la Provincia de Buenos Aires ([gob.ar](https://www.gba.gob.ar/)).
- **OpenStreetMap** — descarga de información geoespacial vía `osmdata` y mapas base con `ggmap`/`get_stadiamap`.
- **Bases de datos espaciales** para mapas base y ruteo.


## 🎯 Objetivos

- Identificar y cuantificar los barrios populares a nivel nacional.
- Analizar la distribución de barrios populares por provincia y localidad.
- Seleccionar el partido de Lanús y caracterizar sus barrios populares.
- Medir la accesibilidad a centros de salud desde Villa Jardín mediante isócronas y ruteo peatonal.

## 🛠️ Herramientas y técnicas utilizadas


| Categoría | Herramientas |
|---|---|
| **Lenguaje** | R |
| **Manipulación de datos** | `tidyverse`, `dplyr` |
| **Datos espaciales** | `sf` (unión de datasets espaciales y tradicionales, transformación a objetos espaciales) |
| **Descarga de datos geoespaciales** | `osmdata` (OpenStreetMap) |
| **Mapas base** | `ggmap`, `get_stadiamap` |
| **Mapas interactivos** | `leaflet` |
| **Geolocalización** | `tidygeocoder` |
| **Isócronas y ruteo peatonal** | `osrm` (`osrmIsochrone`, `osrmRoute` con perfil `foot`) |
| **Visualización** | `ggplot2` |
| **Documento** | R Markdown (`knitr`/`rmarkdown`) con salida en HTML |

> 💡 El documento incluye **mapas interactivos con Leaflet** para explorar la ubicación de Villa Jardín, los centros de salud, las isócronas y las rutas peatonales.

## 📁 Estructura del repositorio

```text
accesibilidad-villa-jardin-lanus/
├── README.md
├── Proyecto_Final_Ciencia_Datos_II.Rmd     # Código fuente del análisis
├── Proyecto_Final_Ciencia_Datos_II.html    # Documento renderizado (abrir en el navegador)
├── index.html                              # Redirección a la raíz de GitHub Pages
├── Datos/
│   ├── renabap-datos-barrios-gpkg           # Dataset ReNaBap
│   └── establecimientos_salud_publicos-2025.csv
├── LICENSE
└── .gitignore
```

## ▶️ Ver el análisis completo

👉 [Hacé clic acá para ver el trabajo renderizado](https://siguax.github.io/accesibilidad-villa-jardin-lanus/Proyecto_Final_Ciencia_Datos_II.html)

## 🛠️ Cómo visualizar el proyecto

1. Descargá o cloná este repositorio:
   ```bash
   git clone https://github.com/Siguax/accesibilidad-villa-jardin-lanus.git
   cd accesibilidad-villa-jardin-lanus
   ```
2. Abrí el archivo **`Proyecto_Final_Ciencia_Datos_II.html`** en cualquier navegador web (Chrome, Firefox, Edge).
   - No necesitás instalar R para ver los resultados.

3. Si querés reproducir el análisis, abrí el archivo Proyecto_Final_Ciencia_Datos_II.Rmd en RStudio y ejecutá **Knit**.

## 📊 Principales hallazgos

### Distribución nacional de barrios populares
- La mayor distribución de barrios populares se concentra en la provincia de Buenos Aires, seguida por Santa Fe y Chaco. La tipología predominante son los asentamientos informales.

### Provincia de Buenos Aires
- En la Zona Sur se ubican las localidades con mayor cantidad de barrios populares (más de 3.000 familias por barrio): Lomas de Zamora, seguida por Quilmes. En la Zona Oeste destaca General San Martín.

### Partido de Lanús
- Lanús Oeste concentra la mayoría de barrios populares, creados en la década de 1970, con un crecimiento significativo en las décadas de 1980 y 2000.
- Villa Jardín alberga la mayor cantidad de familias (4.950) y viviendas (4.500) del partido. Aunque existen otros barrios con mayor superficie, Villa Jardín presenta la mayor densidad de población (se infiere del cociente superficie/cantidad de viviendas).

### Accesibilidad a centros de salud
- Villa Jardín cuenta con 6 centros o unidades sanitarias a menos de 20 minutos de caminata.
- Más cercano: Unidad de Salud Villa Jardín (Emilio Castro 3823) — 2,82 minutos / 212 metros.
- Más lejano: Centro de Salud Villa Giardino (Armenia 3114) — 1,31 km / ~18 minutos a pie.
- La duración promedio del recorrido es de 10,64 minutos y la distancia promedio de 0,79 km.

## 📚 Temas del curso aplicados

- Información geográfica y mapas.
- Análisis y geoprocesamiento de datos.
- Detección de patrones espaciales y temporales.
- Descarga de datos espaciales de repositorios online.
- Geolocalización de información y análisis de movimientos en la ciudad.

## 📄 Licencia
Distribuido bajo la licencia MIT. Consultá LICENSE para más detalles.

## 👩‍💻 Autora
**Silvia Prevettoni**
- GitHub: [@Siguax](https://github.com/Siguax)
- LinkedIn: [silvia-prevettoni](https://www.linkedin.com/in/silvia-prevettoni)
- Email: [silvia.prevettoni@gmail.com](mailto:silvia.prevettoni@gmail.com)