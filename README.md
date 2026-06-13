# AST_TPFinal

Trabajo Final de Analisis de Series de Tiempo enfocado en el estudio y pronostico de la volatilidad del S&P 500 usando al ETF `SPY` como proxy operativo.

## Objetivo de esta etapa

Este repositorio contiene la primera parte del trabajo: descarga, limpieza, preparacion, exploracion inicial y guardado de un dataset diario de `SPY` para el periodo `2010-01-01` a `2025-12-31`.

En esta instancia no se implementan modelos. El objetivo es dejar una base consistente para usar mas adelante en enfoques como ARIMA, GARCH, Prophet, LSTM u otros modelos de series temporales.

## Archivo principal

- `01_preparacion_spy_volatilidad.ipynb`: notebook base reproducible con comentarios en espanol.

## Contenido del notebook

El notebook incluye:

- introduccion metodologica,
- descarga de datos desde `yfinance`,
- inspeccion inicial del dataset,
- limpieza y validacion de la serie,
- creacion de variables de retorno y volatilidad movil,
- analisis exploratorio descriptivo,
- division temporal en `train`, `validation` y `test`,
- exportacion de datasets procesados.

## Estructura esperada de salidas

Al ejecutar el notebook se crean estas carpetas:

- `data/raw`: copia cruda descargada desde `yfinance`.
- `data/processed`: dataset final con features y particiones temporales.

## Requisitos

Dependencias principales:

- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `yfinance`
- `ipykernel`

Estan listadas en `requirements.txt`.

## Ejecucion sugerida

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

## Criterios metodologicos ya incorporados

- `SPY` se usa como proxy del S&P 500 por su alta cercania operativa con el indice y por disponibilidad de datos diarios.
- No se rellenan fines de semana ni feriados, porque no hubo negociacion real.
- Se calculan retornos logaritmicos para analizar cambios relativos y construir medidas de volatilidad.
- La volatilidad movil se usa como proxy inicial de la variabilidad diaria.
- La division de datos respeta el orden temporal para evitar `data leakage`.

## Estado actual

Implementado:

- notebook inicial reproducible,
- dependencias declaradas,
- pipeline base de preparacion del dataset.

Pendiente para etapas siguientes:

- definicion de targets de pronostico,
- modelado estadistico,
- comparacion de modelos,
- evaluacion predictiva.
