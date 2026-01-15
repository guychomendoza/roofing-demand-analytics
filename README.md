# Miami-Dade Roofing Intelligence Engine 🏠🔍

Un motor de inteligencia de mercado que utiliza datos públicos y análisis espacial para identificar techos residenciales en riesgo estructural y detectar oportunidades comerciales ("Océanos Azules").

## 📌 Descripción
Este proyecto integra datos dispersos del condado de Miami-Dade (Catastro, Permisos, Violaciones y Contratistas) para calcular un **Índice de Demanda de Techos (RDI)**. El modelo prioriza propiedades con alta obsolescencia técnica y baja competencia de mercado.

**Resultados Clave:**
* Procesamiento de **642,539 parcelas**.
* Identificación de zonas críticas con baja oferta de contratistas.

## 📂 Estructura del Repositorio
* `data/`: Contiene una muestra de los datos procesados (`sample_miami_roofing_data.csv`).
* `notebooks/`: Scripts de Python para ETL, cálculo del índice y visualización.
* `docs/`: Reporte técnico (Whitepaper) y Presentación ejecutiva.

## 🛠️ Tecnologías
* Python 3.9+
* Pandas & GeoPandas (ETL Espacial)
* Scikit-learn (Validación Logística)
* Matplotlib & Seaborn (Visualización)

## 🚀 Cómo usar
1. Clona este repositorio.
2. Instala las dependencias: `pip install -r requirements.txt`
3. Descarga los datasets públicos de Miami-Dade (ver enlaces abajo) y colócalos en `data/raw/`.
4. Ejecuta los notebooks en orden numérico.

## 📄 Fuentes de Datos (Data Sources)
Este proyecto utiliza datos públicos oficiales:
* **Parcelas (Catastro):** [Miami-Dade GIS](https://gis-mdc.opendata.arcgis.com/datasets/MDC::parcel-boundary/about)
* **Permisos de Construcción:** [Miami-Dade Open Data](https://opendata.miamidade.gov/Building-and-Construction/Building-Permits/8y7s-h866)
* **Violaciones de Código:** [Miami-Dade Open Data](https://opendata.miamidade.gov/Code-Enforcement/Code-Violations/857z-837k)
* **Contratistas (Competencia):** [Florida DBPR - Construction Industry Licensing Board](http://www.myfloridalicense.com/dbpr/sto/file_download/)

## 📊 Metodología y Resultados

### 1. Arquitectura de Datos (ETL)
Se diseñó un pipeline en Python para normalizar y vincular 4 fuentes heterogéneas:
<img width="2816" height="1082" alt="Gemini_Generated_Image_6tg6896tg6896tg6" src="https://github.com/user-attachments/assets/61073ed1-8160-49e2-acf9-3550d1c603ff" />


### 2. Validación del Modelo
El algoritmo discrimina exitosamente entre propiedades prioritarias y el resto del mercado, con una separación clara en la antigüedad física de los techos:

<img width="584" height="384" alt="edad_techos" src="https://github.com/user-attachments/assets/55dea4a6-f775-4793-b702-343922d998b2" />


### 3. Matriz de Confusión
Validación estadística con 99.7% de exactitud en la detección de patrones de renovación:

<img width="680" height="490" alt="matriz_confusion" src="https://github.com/user-attachments/assets/4c827856-1c0f-400b-a742-d60a2faedcf3" />


### 4. Análisis Geoespacial
Visualización de las parcelas prioritarias (Rojo) vs. el resto del mercado (Azul). Se observa cómo el riesgo no es aleatorio, sino que afecta manzanas enteras:

<img width="432" height="584" alt="mapa2" src="https://github.com/user-attachments/assets/c077779e-1410-4b35-a693-507383b60564" />


### 5. Estrategia Comercial (Océanos Azules)
Identificación de zonas con alta demanda técnica (Riesgo) y baja competencia de contratistas:

<img width="583" height="384" alt="demandaVsOferta" src="https://github.com/user-attachments/assets/14ee07ee-a900-412c-9d12-d7c38bcf2f36" />

## 🔮 Limitaciones y Trabajo Futuro (Roadmap)
Aunque el modelo actual es funcional para la detección temprana, se han identificado áreas clave para iteraciones futuras:

### 1. Ajuste de Umbrales de Seguro
* **Estado Actual:** El modelo utiliza un corte de 20 años como proxy de "no asegurabilidad".
* **Mejora:** Ajustar el umbral a **15 años** para alinearse con las políticas más estrictas que las aseguradoras en Florida han comenzado a implementar post-2024 debido a la crisis de reaseguros.

### 2. Integración de Datos Climáticos
* Incorporar capas de datos históricos de la **NOAA** para correlacionar la ubicación de la parcela con las trayectorias de huracanes recientes (Ian, Nicole), permitiendo un cálculo de riesgo por "fatiga de tormenta".

### 3. Escalabilidad a la Nube
* Migrar el almacenamiento de CSV/Parquet local a una base de datos **PostgreSQL/PostGIS** en AWS para permitir consultas en tiempo real y soportar la carga de todo el estado de Florida.

### 4. Machine Learning Supervisado
* Actualmente, el sistema utiliza un sistema experto (reglas lógicas). El siguiente paso es entrenar un modelo de clasificación (XGBoost o Random Forest) utilizando datos de ventas reales como variable objetivo (labels) para predecir la probabilidad de conversión de venta.

---
*Autor: Luis Mendoza Michel - 2025*
