# 🚀 Guía de Ejecución: Simulación Predictiva del Mundial 2026

Este documento detalla los pasos necesarios para configurar el entorno y ejecutar correctamente el notebook de simulación del Mundial 2026.

---

## 📋 Pre-requisitos y Configuración del Entorno

Dado que el código está diseñado para ejecutarse en **Google Colab** y utiliza rutas específicas, es fundamental preparar tu entorno de Google Drive antes de ejecutar cualquier celda.

1. **Estructura de Carpetas:** Crea la siguiente ruta exacta en tu Google Drive:
   `Mi unidad/Simulaciones_Mundial/Data/`
2. **Archivos Base:** Sube los siguientes archivos CSV originales a la carpeta `Data/`:
   * `datos_historicos.csv`
   * `ranking_fifa.csv`
   * `transfermarkt.csv`
3. **Montar Drive en Colab:** Asegúrate de ejecutar la celda estándar de Colab para montar tu Drive (`from google.colab import drive; drive.mount('/content/drive')`) antes de iniciar el notebook.

---

## ⚙️ Pasos para Ejecutar el Notebook

El notebook está dividido en módulos lógicos. Debes ejecutar las celdas **en orden secuencial** para garantizar que los datos fluyan correctamente de un paso a otro.

### Paso 1: Limpieza y Normalización de Datos
Ejecuta las primeras tres celdas de código. Estas celdas se encargarán de:
* Convertir fechas y normalizar los nombres de los países (ej. 'EEUU' a 'Estados Unidos').
* Filtrar el ranking de la FIFA para mantener solo la puntuación más reciente de cada país.
* Ordenar y limpiar los valores de mercado.
* **Resultado:** Se generarán y guardarán tres nuevos archivos limpios (`_limpio.csv`) en tu carpeta de Drive.

### Paso 2: Pipeline y Entrenamiento del Modelo
Ejecuta la celda titulada "PIPELINE FINAL - CORREGIDO Y OPTIMIZADO".
* Este paso une todos los datos limpios y calcula las variables dinámicas (features) como la forma reciente y las rachas.
* Se entrenarán los modelos `XGBRegressor` para el equipo local y visitante.
* **Nota:** Para que los pasos siguientes funcionen, asegúrate de añadir una línea de código en esta celda que guarde los modelos entrenados usando `joblib
