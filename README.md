# PYTHON_ROOT

Repositorio de proyectos educativos de **Python** y **Google Colab** orientados al análisis financiero, la gestión de riesgos y el uso responsable de IA como apoyo analítico.

Cada carpeta contiene un proyecto autocontenido. Los notebooks (`.ipynb`) pueden abrirse en Google Colab, mientras que los archivos `.py` permiten ejecutar el mismo análisis en un entorno local de Python.

> **Nota:** Los proyectos tienen fines educativos y de exploración. Sus resultados no constituyen recomendación de inversión, asesoría financiera ni un modelo regulatorio.

## Proyectos

| Carpeta | Sumilla |
| --- | --- |
| [`Analytics_BVL_IA`](./Analytics_BVL_IA) | Análisis de mercado de Compañía de Minas Buenaventura (`BVN`) frente al oro y a referencias del sector minero. Descarga precios con `yfinance`, construye gráficos de velas y series normalizadas, y estudia retornos, drawdowns, correlaciones móviles, RSI, medias móviles, beta y residuales. Su bloque complementario compara BVN con `GC=F`, `GDX`, `GDXJ` y `SIL` para distinguir señales propias de la acción de movimientos sectoriales. |
| [`Motor_VaR_IA`](./Motor_VaR_IA) | Demostración de un motor de riesgo cuantitativo para un portafolio de acciones. Calcula VaR histórico y paramétrico normal, Expected Shortfall, correlaciones, contribuciones al riesgo y escenarios de estrés. Exporta los resultados a JSON y los acompaña con un prompt para que un LLM los transforme en una interpretación ejecutiva, sin sustituir el análisis profesional. |

## Contenido de los proyectos

### `Analytics_BVL_IA`

El proyecto estudia la acción ADR de Buenaventura (`BVN`) usando datos de Yahoo Finance. El análisis principal compara su comportamiento con el futuro del oro (`GC=F`) y posteriormente amplía la mirada con ETFs de mineras grandes (`GDX`), mineras junior (`GDXJ`) y mineras de plata (`SIL`).

Incluye, entre otros, los siguientes elementos:

- gráficos de velas, precios normalizados y ratios relativos;
- rendimiento por distintos horizontes, drawdown y volumen;
- correlaciones móviles de 30, 60 y 90 días;
- RSI y medias móviles de BVN;
- regresiones, beta y residuales para evaluar desempeño relativo;
- una lectura automática orientativa para separar una corrección específica de BVN de un movimiento sectorial.

Archivos principales:

- `Analisis_BVN_v062026.py`: versión ejecutable localmente.
- `Analisis_BVN_v062026.ipynb`: versión para explorar en Google Colab/Jupyter.

### `Motor_VaR_IA`

Este proyecto usa un portafolio demostrativo compuesto por `SPY`, `NVDA`, `MSFT` y `AAPL`, con datos históricos descargados desde Yahoo Finance. El cálculo cubre niveles de confianza de 95 % y 99 % y horizontes de 1 y 10 días.

Su flujo es:

1. Descargar precios y calcular retornos del portafolio.
2. Estimar VaR y Expected Shortfall mediante enfoques histórico y paramétrico normal.
3. Evaluar concentración, correlaciones y contribuciones al riesgo.
4. Aplicar escenarios de estrés predefinidos.
5. Exportar métricas a `Resultados_Motor_VaR.json`.
6. Usar `PROMPT GPT PARA ANALIZAR VAR.txt` para orientar una interpretación narrativa y ejecutiva mediante IA.

Archivos principales:

- `Mini_Demo_VaR_Acciones_IA.py` y `.ipynb`: implementación del motor y visualizaciones.
- `Resultados_Motor_VaR.json`: ejemplo de salida estructurada.
- `PROMPT GPT PARA ANALIZAR VAR.txt`: guía de instrucciones para la capa de IA.

## Requisitos y ejecución local

Se recomienda Python 3.10 o superior. Desde la carpeta de este repositorio, instale las dependencias:

```bash
pip install numpy pandas matplotlib scipy yfinance mplfinance jupyter
```

Ejecute un proyecto con, por ejemplo:

```bash
python Analytics_BVL_IA/Analisis_BVN_v062026.py
python Motor_VaR_IA/Mini_Demo_VaR_Acciones_IA.py
```

Para trabajar en Colab, abra el archivo `.ipynb` correspondiente y ejecute las celdas en orden. Los datos de mercado se consultan en tiempo de ejecución, por lo que los resultados pueden variar según la fecha de consulta y la disponibilidad de la fuente.

## Alcance

Los cálculos y lecturas automáticas son demostrativos. Antes de utilizar resultados en decisiones reales, conviene validar datos, supuestos, periodo de análisis, metodología y restricciones aplicables.
