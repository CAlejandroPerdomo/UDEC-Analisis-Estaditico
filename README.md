# Proyecto: Análisis Estadístico de Temperatura Ambiente — Cundinamarca

## Propósito

Notebook reproducible para el análisis estadístico del dataset
`Temperatura_Ambiente_del_Aire_Cundinamarca_desde_01012024`, que contiene
registros de temperatura ambiente (°C) reportados por sensores en distintos
municipios del departamento de Cundinamarca (Colombia) desde el 1 de enero de 2024.

El objetivo es extraer conclusiones técnicas útiles para la gestión ambiental,
agrícola y territorial a nivel municipal. En concreto, el notebook:

1. Importa y valida el dataset (tipos de datos, nulos, duplicados y outliers por
   error de sensor), generando un resumen de calidad de datos.
2. Calcula estadísticas descriptivas (media, mediana, moda) y de dispersión
   (varianza, desviación estándar, rango, IQR, coeficiente de variación) por
   municipio y por periodo temporal (mes y estación climatológica).
3. Evalúa la normalidad de la temperatura por municipio (Shapiro-Wilk) para elegir
   entre ANOVA y Kruskal-Wallis.
4. Aplica la prueba de comparación de grupos elegida para determinar si existen
   diferencias significativas de temperatura entre municipios.
5. Analiza la tendencia temporal (media diaria/mensual, media móvil y
   descomposición estacional aditiva).
6. Genera visualizaciones (histogramas, boxplots, dispersión temperatura–tiempo y
   serie temporal) exportadas a `outputs/figures/`.

## Librerías

- `pandas`, `numpy`
- `matplotlib`, `seaborn`
- `scipy.stats`
- `statsmodels`

(Versión mínima y lista completa en `requirements.txt`.)

## Estructura del proyecto

```
proyecto-temperatura-cundinamarca/
├── data/
│   ├── raw/                # CSV original (sin modificar)
│   └── processed/          # CSV limpio generado por el notebook
├── notebooks/
│   └── analisis_temperatura_cundinamarca.ipynb
├── outputs/
│   └── figures/            # Figuras exportadas (PNG)
├── README.md
└── requirements.txt
```

## Instrucciones de ejecución

1. Colocar el archivo CSV original dentro de `data/raw/` (el notebook detecta
   automáticamente el primer `.csv` de esa carpeta).

2. Crear un entorno virtual e instalar dependencias:

   ```bash
   python -m venv venv
   source venv/bin/activate        # Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. Lanzar Jupyter y abrir el notebook:

   ```bash
   jupyter notebook
   ```

4. Abrir `notebooks/analisis_temperatura_cundinamarca.ipynb` y ejecutar todas las
   celdas de principio a fin (Kernel > Restart & Run All). No requiere intervención
   manual.

## Notas

- El notebook resuelve las rutas del proyecto automáticamente: funciona tanto si se
  ejecuta desde la raíz del proyecto como desde la carpeta `notebooks/`.
- Los resultados intermedios (dataset limpio) se guardan en `data/processed/` y las
  figuras en `outputs/figures/`.
- El alcance temporal incluye todos los registros disponibles desde 01/01/2024
  (el dataset contiene observaciones hasta 2026).
- La detección de outliers se realiza con el método estadístico del rango
  intercuartílico (IQR, factor 1.5) calculado por municipio.
