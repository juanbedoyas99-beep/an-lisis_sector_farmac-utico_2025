# ANÁLISIS INTEGRAL DEL SECTOR FARMACÉUTICO EN COLOMBIA

**Bootcamp Análisis de Datos (Talento TECH) — 2025**  
**Universidad de Antioquia, Universidad de Caldas**

## Integrantes
- Johnatan Blandon Morales  
- Juan Pablo Bedoya  
- Daniela Mejía Monsalve  
- Silvana Taborda Lalinde  
- Juliana Valeria Calderón Jaramillo  

## Ejecutores
- Leandro Caseres  
- Alejandro Loaiza  

---

## 1. Introducción
El sector farmacéutico en Colombia es altamente regulado y dinámico, con múltiples fabricantes dentro de un marco normativo complejo. Para comprender el mercado, evaluar el cumplimiento regulatorio y analizar variaciones de precios, es clave contar con información confiable y estructurada.

Este análisis utiliza **Python (Colab)** y **Power BI** para integrar y visualizar información de distintas fuentes del mercado farmacéutico colombiano. A partir de bases asociadas al **CUM**, **precios reportados** y **precios regulados**, se construye una perspectiva que permite comparar fabricantes, identificar riesgos de incumplimiento y examinar diferencias por presentaciones y estructuras de precios.

---

## 2. Planteamiento del problema
El mercado farmacéutico enfrenta retos por **dispersión de datos**, **variabilidad de precios** y **cumplimiento normativo**. Aunque existen bases oficiales (CUM, reportes de precios, precios regulados), la información está distribuida en sistemas distintos y con formatos heterogéneos, sin una herramienta integrada para relacionar aspectos regulatorios, comerciales y técnicos.

Esta falta de integración dificulta:
- Identificar oportunamente incumplimientos normativos por fabricantes.
- Comparar precios reportados vs. precios máximos regulados.
- Analizar variaciones entre fabricantes y formas farmacéuticas.
- Tomar decisiones con información consolidada, actualizada y visualmente interpretable.

Se plantea la necesidad de una herramienta analítica para **unificar, cruzar y visualizar** información clave, reduciendo la fragmentación y fortaleciendo el monitoreo regulatorio.

---

## 3. Objetivo
Desarrollar un análisis integral del mercado farmacéutico colombiano mediante la consolidación, visualización y evaluación de datos sobre **fabricantes**, **formas farmacéuticas**, **precios reportados** y **precios regulados**, para apoyar la toma de decisiones con información confiable y actualizada.

### 3.1 Objetivos específicos
- Integrar y depurar bases provenientes del CUM, precios reportados y precios regulados.
- Analizar cumplimiento normativo de fabricantes y detectar riesgos/inconsistencias.
- Comparar precios reportados frente a precios máximos regulados para identificar variaciones significativas.
- Clasificar y visualizar medicamentos por forma farmacéutica y fabricante.
- Desarrollar visualizaciones interactivas del comportamiento del mercado.
- Generar un tablero en Power BI para análisis dinámico y actualización periódica.

---

## 4. Justificación
Se requieren herramientas que integren información de fuentes oficiales y comerciales. La falta de un sistema unificado dificulta evaluar el cumplimiento normativo, comparar precios e identificar comportamientos relevantes entre fabricantes y presentaciones.

Power BI permite consolidación, limpieza, transformación y visualización de datos dispersos, aportando valor a analistas y áreas de seguimiento regulatorio y planeación estratégica.

---

## 5. Alcance
El análisis integra tres fuentes principales: **CUM**, **precios reportados** y **precios máximos regulados**. Se centra en identificar relaciones, evaluar cumplimiento y comparar precios por presentación comercial y fabricante.

El tablero en Power BI incluye visualizaciones dinámicas para explorar fabricantes, formas farmacéuticas, precios y regulaciones, apoyando la toma de decisiones.

---

## 6. Metodología

### 6.1 Recolección de datos
Se recopilaron tres fuentes principales:

1) **Código Único de Medicamentos Vigentes (CUM) — INVIMA (Datos Abiertos Colombia)**  
- Contiene CUM, nombre, forma farmacéutica, concentración, titular del registro, estado, entre otros.
- Tamaño aproximado: **157.518 filas, 29 columnas**.
- Última actualización: **16 de septiembre de 2025**.

2) **Precios de Medicamentos — MinSalud (SISMED/Clicsalud / Termómetro de Precios)**  
- Precios observados por unidad (tableta, cápsula, etc.), asociado a CUM, fabricante, canal y región.
- Tamaño aproximado: **~12.534 filas, 9 columnas**.
- Última actualización: **29 de enero de 2025**.

3) **Precio máximo de venta por presentación comercial — MinSalud / CNPMDM**  
- Mercados relevantes con PMV regulado, circular, vigencias, y precios por tipo de transacción (institucional, comercial, final, etc.).

### 6.2 Limpieza y depuración (Google Colab / Python)
Proceso general en pandas para cargar, depurar y unificar datasets:

- Importación de librerías y carga de CSV en dataframes.
- Revisión de valores nulos para evaluar completitud.
- Construcción de un campo **CUM** unificado (concatenación expediente + consecutivo) para cruces consistentes.
- Eliminación de CUM duplicados para evitar inconsistencias.
- Unión de bases por CUM (left merge) para añadir precios máximos regulados y medir cobertura.
- Unión adicional por **principio activo** normalizado (minúsculas/trim) para mejorar emparejamiento.
- Selección de columnas relevantes y exportación del dataset consolidado para uso en Power BI.

### 6.3 Importación y exploración inicial (Power BI)
Los tres datasets se cargaron en Power BI mediante Power Query para modelado y visualización.

### 6.4 Transformación e integración (Power BI)
- Relaciones entre tablas (CUM y otras claves).
- Transformaciones: normalización de precios, clasificación de formas farmacéuticas, agrupaciones por fabricante.

### 6.5 Modelado de datos (medidas DAX)
Medidas para alimentar visualizaciones, por ejemplo:
- Precio Máximo por Tableta, Precio Mediano, Precio Mínimo
- Registros Totales
- Total Laboratorios
- Total Principios Activos

### 6.6 Construcción de visualizaciones (Dashboard)
El tablero se divide en 3 secciones:
- **Resumen:** registros por fabricante, histórico por año desde 1989, formas farmacéuticas más comunes, total de principios activos.
- **Principios activos y presentaciones:** análisis por vía de administración, registros, formas farmacéuticas y laboratorios titulares; incluye **filtro de texto** para búsqueda.
- **Regulación y precios:** precios regulados, comparativa entre laboratorios/medicamentos y análisis de margen promedio anual para IPS por medicamento.

---

## 7. Conclusiones y hallazgos
- Desde 1989 se han emitido **66.692 registros** farmacéuticos en Colombia, distribuidos en **1.162 laboratorios** y **5.559 principios activos**.
- El año con más registros fue **1999**, posiblemente asociado a cambios regulatorios y transición al decreto 677 de 1995, además del fortalecimiento institucional del INVIMA.
- El laboratorio con más registros es **Tecnoquímicas** (≈ **5.500**).
- Forma farmacéutica más común: **tableta recubierta (38,56%)**.
- Medicamento con más registros ante INVIMA: **Acetaminofén (844)**.
- Predomina la vía de administración **oral (74,5%)**.
- Aproximadamente **37%** de registros son medicamentos sólidos (tableta / tableta recubierta).
- En regulación de precios: **48.800 registros** tienen precio regulado (**73%**); el **27%** restante no está regulado y el laboratorio define el precio según su margen objetivo.
- Precio medio por tableta: **2.484 COP**.
- Registro de precio más costoso: **Polivy**, con precio máximo registrado de **$41 millones COP**.
- El mercado farmacéutico colombiano ha crecido y fortalecido su marco regulatorio; el INVIMA debe prepararse técnica y tecnológicamente para retos futuros, y Colombia empieza a posicionarse como referente en exportación, impulsando tecnificación y diversificación.

---

## 8. Referencias (fuentes de datos)
- INVIMA. *Código Único de Medicamentos Vigentes (CUM)* — Datos Abiertos Colombia.  
- Ministerio de Salud y Protección Social. *Precios de medicamentos (SISMED / Termómetro de Precios)* — Datos Abiertos Colombia.  
- CNPMDM / Ministerio de Salud. *Precio máximo de venta por presentación comercial* — Datos Abiertos Colombia.


