# ANÁLISIS INTEGRAL DEL SECTOR FARMACÉUTICO EN COLOMBIA

**Bootcamp Análisis de Datos (Talento TECH) — 2025** :contentReference[oaicite:0]{index=0}  
**Universidad de Antioquia, Universidad de Caldas** :contentReference[oaicite:1]{index=1}  

## Integrantes
- Johnatan Blandon Morales  
- Juan Pablo Bedoya  
- Daniela Mejía Monsalve  
- Silvana Taborda Lalinde  
- Juliana Valeria Calderón Jaramillo :contentReference[oaicite:2]{index=2}  

## Ejecutores
- Leandro Caseres  
- Alejandro Loaiza :contentReference[oaicite:3]{index=3}  

---

## 1. Introducción
El sector farmacéutico en Colombia es altamente regulado y dinámico, con múltiples fabricantes dentro de un marco normativo complejo. Para comprender el mercado, evaluar el cumplimiento regulatorio y analizar variaciones de precios, es clave contar con información confiable y estructurada. :contentReference[oaicite:4]{index=4}  

Este análisis utiliza **Python (Colab)** y **Power BI** para integrar y visualizar información de distintas fuentes del mercado farmacéutico colombiano. A partir de bases asociadas al **CUM**, **precios reportados** y **precios regulados**, se construye una perspectiva que permite comparar fabricantes, identificar riesgos de incumplimiento y examinar diferencias por presentaciones y estructuras de precios. :contentReference[oaicite:5]{index=5}  

---

## 2. Planteamiento del problema
El mercado farmacéutico enfrenta retos por **dispersión de datos**, **variabilidad de precios** y **cumplimiento normativo**. Aunque existen bases oficiales (CUM, reportes de precios, precios regulados), la información está distribuida en sistemas distintos y con formatos heterogéneos, sin una herramienta integrada para relacionar aspectos regulatorios, comerciales y técnicos. :contentReference[oaicite:6]{index=6}  

Esta falta de integración dificulta: :contentReference[oaicite:7]{index=7}  
- Identificar oportunamente incumplimientos normativos por fabricantes. :contentReference[oaicite:8]{index=8}  
- Comparar precios reportados vs. precios máximos regulados. :contentReference[oaicite:9]{index=9}  
- Analizar variaciones entre fabricantes y formas farmacéuticas. :contentReference[oaicite:10]{index=10}  
- Tomar decisiones con información consolidada, actualizada y visualmente interpretable. :contentReference[oaicite:11]{index=11}  

Se plantea la necesidad de una herramienta analítica para **unificar, cruzar y visualizar** información clave, reduciendo la fragmentación y fortaleciendo el monitoreo regulatorio. :contentReference[oaicite:12]{index=12}  

---

## 3. Objetivo
Desarrollar un análisis integral del mercado farmacéutico colombiano mediante la consolidación, visualización y evaluación de datos sobre **fabricantes**, **formas farmacéuticas**, **precios reportados** y **precios regulados**, para apoyar la toma de decisiones con información confiable y actualizada. :contentReference[oaicite:13]{index=13}  

### 3.1 Objetivos específicos
- Integrar y depurar bases provenientes del CUM, precios reportados y precios regulados. :contentReference[oaicite:14]{index=14}  
- Analizar cumplimiento normativo de fabricantes y detectar riesgos/inconsistencias. :contentReference[oaicite:15]{index=15}  
- Comparar precios reportados frente a precios máximos regulados para identificar variaciones significativas. :contentReference[oaicite:16]{index=16}  
- Clasificar y visualizar medicamentos por forma farmacéutica y fabricante. :contentReference[oaicite:17]{index=17}  
- Desarrollar visualizaciones interactivas del comportamiento del mercado. :contentReference[oaicite:18]{index=18}  
- Generar un tablero en Power BI para análisis dinámico y actualización periódica. :contentReference[oaicite:19]{index=19}  

---

## 4. Justificación
Se requieren herramientas que integren información de fuentes oficiales y comerciales. La falta de un sistema unificado dificulta evaluar el cumplimiento normativo, comparar precios e identificar comportamientos relevantes entre fabricantes y presentaciones. :contentReference[oaicite:20]{index=20}  

Power BI permite consolidación, limpieza, transformación y visualización de datos dispersos, aportando valor a analistas y áreas de seguimiento regulatorio y planeación estratégica. :contentReference[oaicite:21]{index=21}  

---

## 5. Alcance
El análisis integra tres fuentes principales: **CUM**, **precios reportados** y **precios máximos regulados**. Se centra en identificar relaciones, evaluar cumplimiento y comparar precios por presentación comercial y fabricante. :contentReference[oaicite:22]{index=22}  

El tablero en Power BI incluye visualizaciones dinámicas para explorar fabricantes, formas farmacéuticas, precios y regulaciones, apoyando la toma de decisiones. :contentReference[oaicite:23]{index=23}  

---

## 6. Metodología

### 6.1 Recolección de datos
Se recopilaron tres fuentes: :contentReference[oaicite:24]{index=24}  

1) **CÓDIGO ÚNICO DE MEDICAMENTOS VIGENTES (CUM) — INVIMA (Datos Abiertos Colombia)**  
- Contiene CUM, nombre, forma farmacéutica, concentración, titular del registro, estado, etc. :contentReference[oaicite:25]{index=25}  
- Tamaño aproximado: **157.518 filas, 29 columnas**. :contentReference[oaicite:26]{index=26}  
- Última actualización: **16 de septiembre de 2025**. :contentReference[oaicite:27]{index=27}  

2) **Precios Medicamentos — MinSalud (SISMED/Clicsalud / Termómetro de Precios)**  
- Precios observados por unidad (tableta, cápsula, etc.), asociado a CUM, fabricante, canal y región. :contentReference[oaicite:28]{index=28}  
- Tamaño aproximado: **~12.534 filas, 9 columnas**. :contentReference[oaicite:29]{index=29}  
- Última actualización: **29 de enero de 2025**. :contentReference[oaicite:30]{index=30}  

3) **Precio máximo de venta por presentación comercial — MinSalud / CNPMDM**  
- Mercados relevantes con PMV regulado, circular, vigencias, y precios por tipo de transacción (institucional, comercial, final, etc.). :contentReference[oaicite:31]{index=31}  

### 6.2 Limpieza y depuración (Google Colab / Python)
Se describe el proceso en pandas para cargar, depurar y unificar datasets. :contentReference[oaicite:32]{index=32}  

Pasos clave (resumen):
- Importación de librerías y carga de CSV en dataframes (df1, df2, df3). :contentReference[oaicite:33]{index=33}  
- Revisión de valores nulos en cada dataframe para evaluar completitud. :contentReference[oaicite:34]{index=34}  
- Construcción de un campo **CUM** unificado (concatenación expediente + consecutivo) para cruces consistentes. :contentReference[oaicite:35]{index=35}  
- Eliminación de CUM duplicados para evitar inconsistencias. :contentReference[oaicite:36]{index=36}  
- Unión df1–df3 por CUM (left merge) para añadir precios máximos regulados y medir cobertura. :contentReference[oaicite:37]{index=37}  
- Unión df2–df1 por **principio activo** normalizado (minúsculas/trim) para mejorar emparejamiento. :contentReference[oaicite:38]{index=38}  
- Selección de columnas relevantes y exportación del dataset consolidado para uso en Power BI. :contentReference[oaicite:39]{index=39}  

### 6.3 Importación y exploración inicial (Power BI)
Los tres datasets se cargaron en Power BI mediante Power Query, para modelado y visualización. :contentReference[oaicite:40]{index=40}  

### 6.4 Transformación e integración (Power BI)
- Relaciones entre tablas (CUM y otras claves). :contentReference[oaicite:41]{index=41}  
- Transformaciones: normalización de precios, clasificación de formas farmacéuticas, agrupaciones por fabricante. :contentReference[oaicite:42]{index=42}  

### 6.5 Modelado de datos (medidas DAX)
Medidas para alimentar visualizaciones, por ejemplo:  
- Precio Máximo por Tableta, Precio Mediano, Precio Mínimo  
- Registros Totales  
- Total Laboratorios  
- Total Principios Activos :contentReference[oaicite:43]{index=43}  

### 6.6 Construcción de visualizaciones (Dashboard)
El tablero se divide en 3 secciones: :contentReference[oaicite:44]{index=44}  
- **Resumen:** registro de medicamentos por fabricante, histórico por año desde 1989, formas farmacéuticas más comunes, total de principios activos. :contentReference[oaicite:45]{index=45}  
- **Principios activos y presentaciones:** análisis detallado por vía de administración, registros, formas farmacéuticas y laboratorios titulares; incluye **filtro de texto** para búsqueda. :contentReference[oaicite:46]{index=46}  
- **Regulación y precios:** precios regulados, comparativa entre laboratorios/medicamentos y análisis de margen promedio anual para IPS por medicamento. :contentReference[oaicite:47]{index=47}  

---

## 7. Conclusiones y hallazgos
- Desde 1989 se han emitido **66.692 registros** farmacéuticos en Colombia, distribuidos en **1.162 laboratorios** y **5.559 principios activos**. :contentReference[oaicite:48]{index=48}  
- El año con más registros fue **1999**, posiblemente asociado a cambios regulatorios y transición al decreto 677 de 1995, además del fortalecimiento institucional del INVIMA. :contentReference[oaicite:49]{index=49}  
- El laboratorio con más registros es **Tecnoquímicas** (≈ **5.500**). :contentReference[oaicite:50]{index=50}  
- Forma farmacéutica más común: **tableta recubierta (38,56%)**. :contentReference[oaicite:51]{index=51}  
- Medicamento con más registros ante INVIMA: **Acetaminofén (844)**. :contentReference[oaicite:52]{index=52}  
- Predomina la vía de administración **oral (74,5%)**. :contentReference[oaicite:53]{index=53}  
- Aproximadamente **37%** de registros son medicamentos sólidos (tableta / tableta recubierta). :contentReference[oaicite:54]{index=54}  
- En regulación de precios: **48.800 registros** tienen precio regulado (**73%**); el **27%** restante no está regulado y el laboratorio define el precio según su margen objetivo. :contentReference[oaicite:55]{index=55}  
- Precio medio por tableta: **2.484 COP**. :contentReference[oaicite:56]{index=56}  
- Registro de precio más costoso: **Polivy**, con precio máximo registrado de **$41 millones COP**. :contentReference[oaicite:57]{index=57}  
- El mercado farmacéutico colombiano ha crecido y fortalecido su marco regulatorio; el INVIMA debe prepararse técnica y tecnológicamente para los retos futuros, y Colombia empieza a posicionarse como referente en exportación, impulsando tecnificación y diversificación. :contentReference[oaicite:58]{index=58}  

---

## 8. Referencias
- INVIMA (2025-09-16). *Código Único de Medicamentos Vigentes* — Datos Abiertos Colombia. :contentReference[oaicite:59]{index=59}  
- Ministerio de Salud y Protección Social (2025-01-29). *Precios de medicamentos* — Datos Abiertos Colombia. :contentReference[oaicite:60]{index=60}  
- CNPMDM / Ministerio de Salud (2025-10-26). *Precio máximo de venta de medicamentos por presentación comercial* — Datos Abiertos Colombia. :contentReference[oaicite:61]{index=61}  

