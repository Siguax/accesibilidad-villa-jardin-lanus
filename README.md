# 🗺️ Análisis geoespacial de accesibilidad a salud en un barrio popular: caso Villa Jardín (Lanús)

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Ver%20an%C3%A1lisis-brightgreen)](https://siguax.github.io/accesibilidad-villa-jardin-lanus/Proyecto_Final_Ciencia_Datos_II.html)
[![R](https://img.shields.io/badge/R-4.x-276DC3?logo=r&logoColor=white)](https://www.r-project.org/)
[![sf](https://img.shields.io/badge/sf-geoespacial-blue)](https://r-spatial.github.io/sf/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> Análisis geoespacial aplicado a la planificación sanitaria en barrios populares

## 📌 Problema de negocio

En Argentina, uno de cada diez habitantes reside en un barrio popular. La segregación territorial y la falta de acceso a servicios básicos generan desigualdades que impactan directamente en la salud de la población. La pregunta que guía este análisis es concreta: ¿qué tan accesibles son los centros de salud a pie para los residentes de Villa Jardín, el barrio popular más denso del partido de Lanús?

Responder esta pregunta permite a municipios, organismos de salud pública y organizaciones sociales priorizar intervenciones de accesibilidad peatonal y planificar la apertura de nuevos puntos de atención en territorios donde la distancia a un centro de salud puede ser una barrera crítica.

## 🎯 Objetivos
- Identificar y cuantificar los barrios populares a nivel nacional a partir de datos oficiales.
- Analizar la distribución de barrios populares por provincia y localidad.
- Caracterizar los barrios populares del partido de Lanús y seleccionar el de mayor densidad poblacional.
- Medir la accesibilidad peatonal a centros de salud desde Villa Jardín mediante isócronas y ruteo, cuantificando distancias y tiempos de recorrido.


## 📂 Fuente de datos

- **ReNaBap** (Registro Nacional de Barrios Populares) — datos abiertos en formato GeoPackage.
- **Establecimientos de salud públicos** — datos abiertos del Gobierno de la Provincia de Buenos Aires ([gob.ar](https://www.gba.gob.ar/)).
- **OpenStreetMap** — descarga de información geoespacial vía `osmdata` y mapas base con `ggmap`/`get_stadiamap`.
- **Bases de datos espaciales** para mapas base y ruteo.


## 🛠️ Stack tecnológico

- R · sf · tidyverse · dplyr · osmdata · osrm · leaflet · ggplot2 · ggmap · tidygeocoder · R Markdown
- Manipulación y análisis espacial: sf para unión de datasets espaciales y tabulares, transformación de objetos espaciales y operaciones geométricas.
- Descarga de datos geoespaciales: osmdata para obtener la red peatonal desde OpenStreetMap.
- Ruteo e isócronas: osrm (osrmIsochrone, osrmRoute con perfil foot) para calcular áreas de accesibilidad peatonal y rutas reales.
- Visualización: leaflet para mapas interactivos, ggplot2 y ggmap para mapas estáticos.
- Geolocalización: tidygeocoder para geocodificación de direcciones.
- Reproducibilidad: R Markdown con salida en HTML, análisis documentado de punta a punta.

> 💡 El documento incluye **mapas interactivos con Leaflet** para explorar la ubicación de Villa Jardín, los centros de salud, las isócronas y las rutas peatonales.


## 📊 Principales hallazgos

### Distribución nacional de barrios populares
- La mayor distribución de barrios populares se concentra en la provincia de Buenos Aires, seguida por Santa Fe y Chaco.
- La tipología predominante son los asentamientos informales.

### Provincia de Buenos Aires
- En la Zona Sur se ubican las localidades con mayor cantidad de barrios populares (más de 3.000 familias por barrio): Lomas de Zamora, seguida por Quilmes.
- En la Zona Oeste destaca General San Martín.

### Partido de Lanús
- Lanús Oeste concentra la mayoría de barrios populares, creados en la década de 1970, con un crecimiento significativo en las décadas de 1980 y 2000.
- Villa Jardín alberga la mayor cantidad de familias (4.950) y viviendas (4.500) del partido.
- Aunque existen otros barrios con mayor superficie, Villa Jardín presenta la mayor densidad de población (se infiere del cociente superficie/cantidad de viviendas).

### Accesibilidad a centros de salud
- Villa Jardín cuenta con 6 centros o unidades sanitarias a menos de 20 minutos de caminata.
- Más cercano: Unidad de Salud Villa Jardín (Emilio Castro 3823) — 2,82 minutos / 212 metros.
- Más lejano: Centro de Salud Villa Giardino (Armenia 3114) — 1,31 km / ~18 minutos a pie.
- La duración promedio del recorrido es de 10,64 minutos y la distancia promedio de 0,79 km.

## 💡 Impacto y recomendaciones

- Priorización de intervenciones: los resultados permiten identificar qué sectores de Villa Jardín tienen peor accesibilidad peatonal y priorizar allí mejoras de infraestructura (veredas, cruces, iluminación) o la apertura de nuevos puntos de atención.
- Replicabilidad: la metodología es replicable a otros barrios populares del conurbano y a otros servicios (educación, transporte, seguridad).
- Planificación sanitaria: el análisis cuantifica la barrera de distancia/tiempo a la que se enfrenta la población, insumo directo para decisiones de localización de servicios de salud.

## 🧠 Competencias demostradas

- Integración de datos geoespaciales heterogéneos: ReNaBap (GeoPackage), establecimientos de salud (CSV), OpenStreetMap (API).
- Análisis espacial aplicado: isócronas peatonales, ruteo con OSRM, cálculo de distancias y tiempos reales.
- Visualización interactiva: mapas Leaflet para exploración de resultados.
- Reproducibilidad: análisis documentado en R Markdown, con código y datos disponibles.
- Traducción de resultados a recomendaciones: de hallazgos cuantitativos a insumos para la toma de decisiones.

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

## 🛠️ Cómo reproducir el análisis

1. Descargá o cloná este repositorio:
   ```bash
   git clone https://github.com/Siguax/accesibilidad-villa-jardin-lanus.git
   cd accesibilidad-villa-jardin-lanus
   ```

2. Para ver los resultados: abrí Proyecto_Final_Ciencia_Datos_II.html en cualquier navegador (Chrome, Firefox, Edge). No necesitás instalar R.

3. Para reproducir el análisis: abrí Proyecto_Final_Ciencia_Datos_II.Rmd en RStudio y ejecutá Knit.

## 📄 Licencia
Distribuido bajo la licencia **MIT**. Consultá [`LICENSE`](LICENSE) para más detalles.

## 👩‍💻 Autora
**Silvia Prevettoni**
- GitHub: [@Siguax](https://github.com/Siguax)
- LinkedIn: [silvia-prevettoni](https://www.linkedin.com/in/silvia-prevettoni)
- Email: [silvia.prevettoni@gmail.com](mailto:silvia.prevettoni@gmail.com)
