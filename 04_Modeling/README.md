# 04 – Modeling

## Propósito de esta fase

Esta fase documenta la construcción del modelo dimensional y semántico implementado en Power BI para el visualizador financiero de Cierre Contable.

Aquí se define:
- la estructura analítica del modelo,
- relaciones entre tablas,
- dimensiones compartidas,
- medidas DAX,
- KPIs financieros,
- tablas calculadas
- y lógica de presentación ejecutiva

con el fin de garantizar consistencia analítica, trazabilidad funcional y soporte para la toma de decisiones financieras institucionales.

---

## Documentos incluidos

### Modelo_Dimensional.png

Representación visual del modelo dimensional implementado en Power BI.

Incluye:
- Tablas de hechos
- Dimensiones compartidas
- Relaciones y cardinalidades
- Consolidación multiempresa
- Modelo estrella híbrido
- Estructura analítica financiera

---

### Modelo_Descripcion.md

Documentación funcional y técnica del modelo dimensional.

Incluye:
- Arquitectura del modelo
- Granularidad de tablas
- Estrategia de consolidación
- Relaciones principales
- Modelo analítico
- Optimización para KPIs y análisis financiero

---

## visualization/

Contiene los componentes semánticos y analíticos construidos en Power BI.

---

### Medidas_DAX.xlsx

Inventario técnico de medidas DAX y objetos analíticos utilizados en el modelo financiero.

Documenta:
- Nombre de medida
- Tabla origen
- Fórmula DAX
- Descripción funcional
- Dependencias
- Área de uso
- Tipo de objeto
- Formato sugerido

Incluye:
- KPIs financieros
- Variaciones presupuestales
- Comparativos YoY
- Indicadores porcentuales
- Medidas gerenciales
- Formatos visuales
- Medidas auxiliares

---

### KPIs_Definicion.md

Definición funcional de los principales indicadores financieros utilizados en el visualizador ejecutivo.

Incluye:
- Ingresos operacionales
- EBITDA
- Margen EBITDA
- Resultado operacional neto
- Excedentes
- Variaciones vs presupuesto
- Variaciones vs año anterior

---

### Tablas_Calculadas.md

Documentación de tablas calculadas creadas en DAX para soportar análisis temporal y presentación ejecutiva.

Incluye:
- Dim_Tiempo
- EstadoResultado_Jer
- Dim_Empresa

Documenta:
- Objetivo funcional
- Uso analítico
- Relación con el modelo
- Soporte a KPIs y navegación ejecutiva

---