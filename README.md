# 📞 ConnectaTel - Análisis de Comportamiento de Consumo de Clientes

Este proyecto realiza un análisis exploratorio de datos (EDA) y una segmentación estratégica de la base de clientes de **ConnectaTel** en México y Colombia. El objetivo es identificar patrones de uso, detectar comportamientos atípicos (outliers) y proponer optimizaciones comerciales para la oferta de planes actuales.

---

## 🎯 Objetivo del Proyecto

El propósito principal de este análisis es diagnosticar cómo interactúan los usuarios con los servicios de la compañía para responder a las siguientes preguntas de negocio:
1. ¿Los límites de los planes actuales se alinean con el consumo real de los usuarios?
2. ¿Qué perfiles demográficos e intensidad de uso existen en la base de datos?
3. ¿Existen patrones atípicos o posibles casos de fraude (uso comercial en líneas residenciales)?

---

## 📊 Datasets Utilizados

El análisis se basa en el dataframe consolidado `user_profile`, el cual integra información de las siguientes fuentes:
* **Datos Demográficos:** `age` (Edad del usuario), `city` (Ciudad/País de origen).
* **Métricas de Consumo:** * `cant_mensajes`: Cantidad de SMS enviados al mes.
    * `cant_llamadas`: Total de llamadas realizadas en el periodo.
    * `cant_minutos_llamada`: Duración total acumulada de las llamadas en minutos.
* **Información Comercial:** `plan` (Plan contratado: Básico / Premium).

---

## ⚙️ Etapas del Análisis Realizadas

1.  **Limpieza y Consolidación de Datos:** Fusión de tablas y tratamiento inicial de registros.
2.  **Análisis de Distribución:** Generación de histogramas con curvas de densidad (`KDE`) para evaluar el comportamiento de variables clave (`age`, `cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`).
3.  **Identificación Científica de Outliers:** Aplicación del método del **Rango Intercuartílico (IQR)** para establecer límites técnicos de uso normal y detectar consumos extremos (ej. llamadas de hasta 155 minutos).
4.  **Ingeniería de Características (Segmentation):**
    * Creación de la columna `grupo_edad`: Clasificación en *Joven*, *Adulto* y *Adulto Mayor*.
    * Creación de la columna `grupo_uso`: Clasificación en *Bajo uso*, *Uso medio* y *Alto uso* mediante condiciones lógicas combinadas de llamadas y mensajes.
5.  **Visualización Categórica:** Implementación de gráficos de conteo (`sns.countplot`) para analizar el volumen de cada segmento y exportación de gráficos en alta resolución (`DPI=300`).

---

## 🚀 Cómo Ejecutar el Notebook

Puedes ejecutar este análisis de forma local o directamente en la nube. La opción recomendada para una ejecución rápida es **Google Colab**.

### Opción 1: Google Colab (Recomendado)
1. Ve a [Google Colab](https://colab.research.google.com/).
2. Selecciona la pestaña **File (Archivo)** > **Upload notebook (Subir notebook)**.
3. Sube el archivo `.ipynb` de este proyecto.
4. Sube los archivos `.csv` correspondientes a los datasets en el panel de archivos de la izquierda.
5. Ejecuta las celdas en orden secuencial presionado `Shift + Enter`.

### Opción 2: Entorno Local (Jupyter Notebook / VS Code)
1. Asegúrate de tener instalado Python (versión 3.8 o superior).
2. Clona este repositorio o descarga los archivos.
3. Instala las librerías necesarias ejecutando en tu terminal:
   ```bash
   pip install pandas matplotlib seaborn
