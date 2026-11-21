# Mantenimiento predictivo en manufactura con datos abiertos — AI4I 2020

Proyecto de curso **Gestión Industrial con Datos Abiertos** · Analítica de Datos Grupo-o1 · Maestría en Gestión Industrial · Universidad de Ibagué, 2026.

**Autoras:** Juriana Cardona Bonilla (2320201096) · Yajaira Barrero Gualtero (2320211056)

**Docente:** Alexandra La Cruz Puente

## Problema

Las fallas de máquina no planificadas detienen la línea, generan piezas defectuosas y obligan a reparaciones correctivas. Este proyecto busca **anticipar la falla de una máquina-herramienta** (`Machine failure`) a partir de variables de proceso que ya registra el sistema de control (temperaturas, velocidad, torque y desgaste de herramienta), e identificar las condiciones de operación que concentran el riesgo.

## Contenido del notebook

| Fase | Contenido |
|---|---|
| 1. Contexto | Ficha técnica del dataset, problema, valor del dato abierto, entorno y declaración de uso de IA |
| 2. ETL | Ingesta, diccionario de datos antes/después, formatos, outliers (IQR), variables derivadas y KPIs, reporte de calidad, modelo de datos por capas |
| 3. EDA | Estadística descriptiva, 6 visualizaciones interpretadas e hipótesis H1–H5 |
| 4. Modelado | K-means (codo, silueta y perfiles), clasificación (Naive Bayes, Regresión Logística, LDA, kNN, Árbol, Random Forest), PCA, LDA como reducción, validación cruzada, ajuste de umbral por costo del error y comparación final |

**Resultado principal:** un Random Forest con umbral de decisión 0,17 detecta el 85 % de las fallas del conjunto de prueba (ROC-AUC 0,978) con el menor costo de error. El árbol de decisión de profundidad 5 es una alternativa interpretable casi equivalente (F1 = 0,88).

## Estructura del repositorio

```
mantenimiento-predictivo-ai4i/
├── datasets/
│   ├── ai4i2020.csv          # capa RAW: dato original de UCI, sin modificar
│   └── datos_limpios.csv     # capa CLEAN: generado por el notebook
├── notebooks/
│   └── mantenimiento_predictivo_ai4i.ipynb
├── requirements.txt
└── README.md
```

## Cómo ejecutarlo

Requiere Python 3.12.

```bash
python -m venv .venv
.venv\Scripts\activate            # Windows  (macOS/Linux: source .venv/bin/activate)
pip install -r requirements.txt
```

Abre `notebooks/mantenimiento_predictivo_ai4i.ipynb` en VS Code o Jupyter, selecciona el entorno `.venv` y ejecuta todas las celdas en orden. El notebook lee los datos con rutas relativas (`../datasets/`), así que debe ejecutarse desde la carpeta `notebooks/`. La ejecución completa tarda unos 2 minutos.

**Reproducibilidad:** todas las particiones, búsquedas de hiperparámetros y modelos usan `RANDOM_STATE = 42`.

## Datos

| Campo | Detalle |
|---|---|
| Dataset | AI4I 2020 Predictive Maintenance Dataset |
| Fuente | UCI Machine Learning Repository — https://doi.org/10.24432/C5HS5C |
| Autor | Stephan Matzka, HTW Berlin (2020) |
| Licencia | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) |
| Tamaño | 10 000 filas × 14 columnas |
| Naturaleza | **Sintético**: generado por el autor para reflejar datos reales de mantenimiento predictivo |

El archivo `datasets/ai4i2020.csv` se redistribuye sin modificaciones bajo los términos de su licencia.

## Uso de inteligencia artificial

Se usó un asistente de IA (Claude, de Anthropic) como apoyo para revisar el notebook frente a los requerimientos del curso y proponer celdas de EDA, tratamiento de outliers, KPIs y métricas. Las autoras revisaron el contenido y pueden explicar cada decisión.

## Referencias

- Matzka, S. (2020a). *AI4I 2020 predictive maintenance dataset* [Conjunto de datos]. UCI Machine Learning Repository. https://doi.org/10.24432/C5HS5C
- Matzka, S. (2020b). Explainable artificial intelligence for predictive maintenance applications. En *2020 Third International Conference on Artificial Intelligence for Industries (AI4I)* (pp. 69–74). IEEE. https://doi.org/10.1109/AI4I49448.2020.00023
- Pedregosa, F., et al. (2011). Scikit-learn: Machine learning in Python. *Journal of Machine Learning Research, 12*, 2825–2830.
