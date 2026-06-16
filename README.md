# AST1 - TP Final

Trabajo Final de Análisis de Series de Tiempo enfocado en el estudio y pronóstico de la volatilidad del S&P 500 usando al ETF `SPY` como proxy operativo.

## Objetivo

Este repositorio contiene el flujo completo desarrollado para el trabajo final de Análisis de Series de Tiempo, incluyendo:

1. preparación y construcción del dataset
2. análisis exploratorio
3. definición del problema predictivo
4. entrenamiento y evaluación de modelos de pronóstico de volatilidad

El objetivo es estudiar la capacidad de distintos enfoques para anticipar la volatilidad futura del ETF `SPY` para el período `2010-01-01` a `2025-12-31`, utilizado como proxy operativo del índice S&P 500.

Se construye un conjunto de variables derivadas de precios históricos y se comparan distintos modelos de complejidad creciente mediante una metodología de validación temporal consistente.

## Archivos principales

### `01_preparacion_spy_volatilidad.ipynb`

- introducción metodológica
- descarga de datos desde `yfinance`
- inspección inicial del dataset
- limpieza y validación de la serie
- creación de variables de retorno y volatilidad móvil
- análisis exploratorio descriptivo
- división temporal en `train`, `validation` y `test`
- exportado de datasets procesados

### `02_modelado.ipynb`

- definición del target predictivo
- construcción de baselines
- entrenamiento de modelos
- selección de variables
- comparación de desempeño
- análisis de resultados

## Estructura esperada de salidas

Al ejecutar el notebook se crean estas carpetas:

- `data/raw`: copia cruda descargada desde `yfinance`
- `data/processed`: dataset final con features y particiones temporales

## Requisitos

Dependencias principales:

- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `yfinance`
- `ipykernel`
- `scikit-learn`
- `keras`

Están listadas en `requirements.txt`.

## Ejecución sugerida

Crear entorno e instalar dependencias:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Abrir el notebook:

```bash
jupyter notebook 01_preparacion_spy_volatilidad.ipynb
```

## Criterios metodológicos ya incorporados

- `SPY` se usa como proxy del S&P 500 por su alta cercanía operativa con el índice y por disponibilidad de datos diarios.
- No se rellenan fines de semana ni feriados, porque no hubo negociación real.
- Se calculan retornos logarítmicos para analizar cambios relativos y construir medidas de volatilidad.
- La volatilidad móvil se usa como proxy de la variabilidad diaria.
- La división de datos respeta el orden temporal para evitar `data leakage`.

## Estado actual

Implementado:

- pipeline reproducible de descarga y preparación de datos
- construcción de variables de volatilidad y retornos
- análisis exploratorio inicial
- definición del problema de predicción de volatilidad a 21 dias
- modelo baseline constante
- modelo de regresión lineal con selección de variables
- modelo Random Forest
- modelo LSTM basado en secuencias temporales
- evaluación comparativa sobre conjuntos de validación y prueba

Posibles extensiones futuras:

- incorporación de variables macroeconomicas o externas
- arquitecturas neuronales del tipo modelo fundacional
- estrategias de ensamble entre modelos