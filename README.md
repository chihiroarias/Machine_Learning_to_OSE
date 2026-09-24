# Entrega 1: Priorizar el despacho de una cuadrilla (Machine Learning)

Repositorio oficial para la **Entrega 1** del curso de **Machine Learning** (Universidad Católica del Uruguay, 2026). El proyecto aborda la priorización de cuadrillas operativas y la estimación de tiempos de resolución de reclamos utilizando datos abiertos reales de **OSE (Obras Sanitarias del Estado)** junto con un complemento de cátedra.

---

## 📋 Descripción del Proyecto

El sistema opera en el momento exacto en que ingresa un reclamo operativo para resolver dos problemas clave:
1. **Regresión:** Estimar el tiempo de resolución en horas para planificar la carga de trabajo de los centros técnicos.
2. **Clasificación:** Decidir si el reclamo superará el plazo comprometido de 72 horas para priorizar el despacho preventivo de una cuadrilla.

El desarrollo completo se estructura rigurosamente en un pipeline de **13 secciones** dentro del Jupyter Notebook principal, asegurando trazabilidad metodológica, validación cruzada estricta, análisis de costos operativos y evaluación de impacto de *data leakage*.

---

## 🛠️ Estructura del Notebook (13 Secciones)

1. **Ingesta, unión y auditoría:** Auditoría de fuentes, trazabilidad estricta de la unión de registros, diagnóstico de mecanismos de valores faltantes (MCAR, MAR, MNAR) e informe de hallazgos.
2. **Preparación dentro de un pipeline:** Encapsulamiento de transformaciones en `Pipeline` y `ColumnTransformer`, con justificación detallada de exclusión de variables.
3. **Línea base:** Métodos ingenuos de referencia (media para regresión y prevalencia para clasificación).
4. **Regresión sobre el tiempo de resolución:** Mínimos cuadrados y lectura de coeficientes en unidades de negocio (horas, kilómetros, conexiones).
5. **Regularización (Ridge y Lasso):** Selección de hiperparámetros $\lambda$ mediante validación cruzada en grilla logarítmica e interpretación de variables anuladas.
6. **Clasificación del incumplimiento del plazo:** Regresión logística, selección de métricas acordes a la distribución y análisis de matrices de confusión.
7. **Evaluación con validación cruzada:** Validación cruzada estratificada sobre el pipeline completo reportando media y desvío estándar.
8. **El costo del leakage:** Cuantificación numérica de la brecha de desempeño entre un flujo honesto y uno contaminado con información posterior al ingreso.
9. **Elección del umbral por costos:** Derivación analítica del umbral óptimo basada en costos operativos (USD 45 vs. USD 270) y comparación económica de 4 políticas a escala anual (390k reclamos).
10. **Tres familias bajo el mismo defecto:** Comparación controlada entre Modelos Lineales, $k$-Nearest Neighbors y Árboles de Decisión bajo distintas condiciones de escalado y unidades.
11. **Regresas de decisión:** Extracción de reglas operativas explícitas a partir de un árbol de decisión de baja profundidadinterpretable por un supervisor.
12. **Autocrítica del flujo:** Análisis crítico y fundamentado de la decisión metodológica más frágil del trabajo.
13. **Conclusiones y límites:** Recomendaciones prácticas basadas en costos frente a la línea base y declaración explícita de los límites del modelo y los datos.

---

## 📂 Requisitos y Reproducibilidad

- **Dataset OSE 2024:** Disponible en el portal de datos abiertos de OSE (`datos.ose.com.uy` -> *Solicitudes y reclamos operativos 2024*).
- **Complemento de Cátedra:** `data/entregas_reclamos_complemento.csv`.
- **Ejecución:** El notebook está diseñado para ser ejecutado de punta a punta de manera secuencial. La ruta del archivo descargado de OSE se define de forma centralizada en la celda de configuración inicial.

---
