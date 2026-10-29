# 🧠 Depresión en Estudiantes Universitarios — Modelo Predictivo

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Ver%20an%C3%A1lisis-brightgreen)](https://siguax.github.io/depresion-estudiantes-ml/)
[![R](https://img.shields.io/badge/R-4.x-276DC3?logo=r&logoColor=white)](https://www.r-project.org/)
[![tidymodels](https://img.shields.io/badge/tidymodels-%E2%9C%94-orange)](https://www.tidymodels.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> Análisis exploratorio y modelo de regresión logística para predecir depresión en estudiantes universitarios a partir de variables académicas, laborales y socioeconómicas.

## 📌 Descripción del proyecto

Este repositorio contiene un flujo completo de **ciencia de datos** aplicado a un problema de salud mental:

1. **Exploración** de un dataset público con ~28 000 estudiantes.
2. **Preprocesamiento** con recetas de `tidymodels` (agrupación de categorías, manejo de desconocidos, *downsampling*).
3. **Modelado** con regresión logística binomial y validación cruzada estratificada.
4. **Evaluación** con métricas de clasificación (accuracy, AUC-ROC, matriz de confusión).

El objetivo es **identificar factores asociados a la depresión** y construir un clasificador con buen poder discriminativo.

> ⚠️ **Aviso:** este proyecto es de carácter **educativo y exploratorio**. No constituye una herramienta de diagnóstico clínico.

## 📊 Dataset

| | |
|---|---|
| **Fuente** | [Student Depression Dataset — Kaggle](https://www.kaggle.com/datasets/adilshamim8/student-depression-dataset/data) |
| **Registros** | 27 901 |
| **Variables** | 18 |
| **Variable objetivo** | `Depression` → `no_depresivo` / `depresivo` |

### Variables principales

| Variable | Tipo | Descripción |
|---|---|---|
| `Gender` | Categórica | Género del estudiante |
| `Age` | Numérica | Edad en años |
| `Profession` | Categórica | Ocupación (agrupada en `Other` si es poco frecuente) |
| `Work Pressure` | Numérica | Presión laboral percibida |
| `CGPA` | Numérica | Promedio acumulado de calificaciones |
| `Study Satisfaction` | Numérica | Satisfacción con los estudios |
| `Job Satisfaction` | Numérica | Satisfacción laboral |
| `Sleep Duration` | Categórica | Horas promedio de sueño |
| `Dietary Habits` | Categórica | Hábitos alimenticios |
| `Degree` | Categórica | Nivel de estudios |
| `Have you ever had suicidal thoughts` | Categórica | Ideación suicida |
| `Work/study hours` | Numérica | Horas de estudio/trabajo |
| `Financial stress` | Numérica | Estrés financiero |
| `Family History of Mental Illness` | Categórica | Antecedentes familiares |

---

## 🛠️ Stack técnico

| Categoría | Herramientas |
|---|---|
| **Lenguaje** | R (≥ 4.2) |
| **Manipulación** | `dplyr`, `tidyr`, `tidyverse` |
| **Modelado** | `tidymodels`, `parsnip`, `recipes`, `workflows`, `rsample` |
| **Balanceo de clases** | `themis` (`step_downsample`) |
| **EDA** | `skimr`, `DataExplorer`, `GGally` |
| **Multicolinealidad** | `car` (`vif`) |
| **Documento** | `knitr`, `rmarkdown` |
| **Paralelización** | `doParallel` |

---

## 🔬 Metodología

### 1️⃣ Análisis exploratorio (EDA)
- Distribución de variables continuas (densidades).
- Matriz de correlación entre variables numéricas.
- Conteo de valores ausentes por variable.
- Revisión de cardinalidad en `Profession` y `Degree`.
- Balance de la variable objetivo (`Depression`).

### 2️⃣ Preprocesamiento
- Agrupación de profesiones poco frecuentes → `Other`.
- Eliminación de `City` (irrelevante para el modelo).
- Recodificación de `Depression` como factor.
- Receta de `tidymodels`:
  - `step_unknown()` — maneja niveles desconocidos en test.
  - `step_downsample()` — corrige el desbalance de clases.
  - `step_other()` — agrupa categorías raras en `Profession`.

### 3️⃣ Modelado
- División estratificada **train/test** (`initial_split`).
- **Validación cruzada de 10 folds** (`vfold_cv`) con estratificación.
- Modelo: **regresión logística binomial** (`logistic_reg`).
- Flujo reproducible con `workflow()` y `fit_resamples()`.
- Ajuste final con `last_fit()` sobre el set de test.

### 4️⃣ Evaluación
- **Accuracy** y **AUC-ROC** por fold.
- Curva ROC superpuesta por fold.
- **Matriz de confusión** sobre el set de test.

---

## 📈 Resultados principales

| Métrica | Valor |
|---|---|
| **Accuracy (train)** | ≈ 84 % |
| **AUC-ROC (train)** | ≈ 0.92 |
| **VIF (multicolinealidad)** | Todos los valores < 1.5 ✅ |

**Hallazgos clave:**
- No se detectó multicolinealidad problemática, a pesar de la alta correlación entre `Job Satisfaction` y `Work Pressure` (r ≈ 0.77).
- El modelo logra una discriminación sólida (AUC ≈ 0.92) gracias al *downsampling* aplicado en la receta.
- La matriz de confusión muestra un buen equilibrio entre verdaderos positivos y verdaderos negativos.

---
### Paquetes utilizados

```r
install.packages(c(
  "tidyverse", "tidymodels", "skimr", "GGally",
  "themis", "DataExplorer", "car", "knitr",
  "rmarkdown", "doParallel"
))
```

## 📁 Estructura del repositorio

```
depresion-estudiantes-ml/
├── README.md
├── index.html          ← acá, en la raíz
├── Trabajo_Practico_Final.Rmd
├── student_depression_dataset.csv
├── LICENSE
└── .gitignore
```

## ▶️ Cómo visualizar el proyecto

1. Descargá o cloná este repositorio:
   ```bash
   git clone https://github.com/siguax/depresion-estudiantes-ml.git
   cd depresion-estudiantes-ml
   ```
2. Abrí el archivo **`index.html`** en cualquier navegador web (Chrome, Firefox, Edge).
   - No necesitás instalar R para ver los resultados.
3. Si querés reproducir el análisis, abrí el archivo **`Trabajo_Practico_Final.Rmd`** en RStudio y ejecutá **Knit**.

## 🌐 Ver el reporte en línea
👉 **[https://siguax.github.io/depresion-estudiantes-ml/](https://siguax.github.io/depresion-estudiantes-ml/)**

## 📚 Referencias
- Kuhn, M. & Silge, J. (2022). *Tidy Modeling with R*. O'Reilly. https://www.tmwr.org/
- Kaggle. *Student Depression Dataset*. https://www.kaggle.com/datasets/adilshamim8/student-depression-dataset
- R Core Team (2024). *R: A Language and Environment for Statistical Computing*.

## 📄 Licencia
Distribuido bajo la licencia MIT. Consultá LICENSE para más detalles.

## ✉️ Contacto
**Silvia Prevettoni**

- 🐙 GitHub: [@Siguax](https://github.com/Siguax)
- 💼 LinkedIn: [silvia-prevettoni](https://www.linkedin.com/in/silvia-prevettoni)
- 📧 Email: [silvia.prevettoni@gmail.com](mailto:silvia.prevettoni@gmail.com)

