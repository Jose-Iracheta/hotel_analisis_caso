# Análisis de Datos Hoteleros – Caso Técnico TCA Software Solutions
Este proyecto forma parte de la evaluación para la vacante Data Enginner JR.
El objetivo es demostrar el dominio de Python para la limpieza, transformación e integración de datos, así como la capacidad de extraer hallazgos de negocio a partir de información hotelera.

# Objetivo
Realizar un análisis exploratorio y analítico utilizando cinco archivos en formato .parquet:

Archivo	                              Descripción
iar_empresas.parquet	                  Catálogo de hoteles del grupo hotelero.
iar_agencias.parquet	                  Catálogo de agencias de viaje.
iar_segmentos_Mercados.parquet	      Catálogo de mercados atendidos.
iar_reservaciones.parquet	            Información de reservaciones hoteleras.
iar_Ocupaciones.parquet	               Métricas de ingresos, ADR y cuartos noche.

# Requisitos de instalacion
1-Clonar o descargar este repositorio.
2-Crear un entorno virtual (opcional, pero recomendado):
   python -m venv venv
   source venv/bin/activate   # En Mac/Linux
   venv\Scripts\activate      # En Windows
3-Instalar dependencias
   pip install -r requirements.txt
4-Ejecutar el notebook principal:
   jupyter notebook notebooks/01_eda_y_analisis.ipynb

# Etapas del proyecto
1. Limpieza y perfilado de datos
Se analizaron los cinco datasets para identificar valores nulos, duplicados y tipos de dato.
Se estandarizaron formatos de fecha y se corrigieron errores de tipo.
Se detectaron duplicados en el catálogo de agencias (por nombre).
Se verificó la integridad referencial entre empresas, agencias y ocupaciones.

2. Exploración de datos (EDA)
Se revisaron registros con fechas inválidas o incoherentes.
Se validó la existencia de empresas sin reservas.
Se identificaron inconsistencias entre los catálogos y las tablas transaccionales.
Se documentaron problemas de calidad de datos y posibles causas.

3. Visualizaciones y hallazgos
*Top 5 agencias por ingresos
 Las agencias más rentables concentran la mayoría de ingresos, lo que sugiere dependencia de pocos socios estratégicos.

*Empresas con más reservas
 Dos hoteles no registran reservas durante el periodo analizado. Esto podría deberse a falta de integración de datos o baja actividad operativa.

*Tendencia de ingresos y crecimiento anual
 Se observa una tendencia general positiva con variaciones anuales que podrían asociarse a estacionalidad o cambios en la demanda.

 # Hallazgos de calidad de datos
Durante el análisis exploratorio se identificaron diversas oportunidades de mejora en la calidad de la información, particularmente en las tablas de reservaciones y catálogos maestros. A continuación se detallan los principales hallazgos:

Datos faltantes en reservaciones canceladas: se detectó ausencia de información en campos clave como estatus o indicadores de cancelación, lo que dificulta distinguir reservas efectivas de canceladas.

Falta de captura en fechas: se observaron registros con valores no capturados en campos como fecha_registro y fecha_salida, afectando la trazabilidad completa del ciclo de reservación.

Inconsistencias en tipos de datos de fecha: algunos campos presentan formatos incorrectos, lo que requirió forzar la conversión mediante errors='coerce' para su análisis.

Valores negativos en tarifas: existen registros con valores negativos en campos de tarifas o ingresos. Dado que no se dispone de una columna de estatus que permita distinguir cancelaciones o ajustes contables, no fue posible inferir su naturaleza.

Duplicados en el catálogo maestro de agencias: se identificaron registros repetidos en el campo Agencia_nombre. Se decidió conservar el primer registro de cada duplicado como referencia principal.

# Recursos adicionales

Se desarrolló un diagrama relacional que muestra las relaciones entre los catálogos (empresas, agencias, mercados) y las tablas transaccionales (reservaciones, ocupaciones).

Se construyó un dashboard básico en Power BI que presenta las métricas de ingresos, reservas y rentabilidad por agencia, complementando el análisis realizado en Python.


# Conclusiones de negocio

El análisis permitió entender mejor el comportamiento de las reservaciones y los ingresos del grupo hotelero. Se observó que una parte importante de los ingresos proviene de pocas agencias, lo que representa una oportunidad para diversificar alianzas y reducir riesgos. Algunos hoteles presentan baja o nula actividad, lo que podría indicar problemas de integración de datos o baja demanda. Además, la información muestra una tendencia positiva en ingresos a lo largo del tiempo. Mejorar la calidad de los datos y la captura de información permitirá obtener reportes más precisos y apoyar una mejor toma de decisiones comerciales.

**Dashboard Power BI**  
El dashboard basico que muestra métricas de ingresos, reservas y rentabilidad por agencia está disponible en Google Drive:  
https://drive.google.com/file/d/19TTAI3L9fC2EXmRaVNQQrXjrMwl73qom/view?usp=drive_link