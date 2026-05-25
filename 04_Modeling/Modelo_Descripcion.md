# Modelo Dimensional – Cierre Contable

## Propósito del modelo

El modelo dimensional fue diseñado para soportar el análisis financiero institucional del proceso de Cierre Contable mediante visualizaciones analíticas en Power BI.

El modelo permite:
- análisis de estados financieros,
- seguimiento presupuestal,
- comparativos históricos,
- análisis por centro de costo,
- consolidación multiempresa,
- y monitoreo de balance general.

---

## Arquitectura del modelo

El modelo sigue un enfoque dimensional tipo estrella híbrida, compuesto por:

### Tablas de hechos
- Real
- Presupuesto
- Balance

### Dimensiones compartidas
- Dim_tiempom
- Dim_clasificacion
- Dim_clas_balance
- Dim_cecos
- Dim_empresa

---

## Granularidad

### Real
1 fila por movimiento contable mensual.

### Presupuesto
1 fila por clasificación presupuestal mensual.

### Balance
1 fila por movimiento o saldo inicial mensual.

---

## Relaciones principales

El modelo utiliza relaciones uno a muchos (1:*) desde dimensiones hacia tablas de hechos.

Las dimensiones compartidas permiten:
- reutilización de filtros,
- consistencia analítica,
- y navegación cruzada entre indicadores financieros.

---

## Estrategia de consolidación

Las fuentes históricas y operativas fueron consolidadas mediante procesos de transformación en Power Query.

Se integraron:
- información financiera real,
- presupuesto,
- balances,
- y empresas relacionadas.

---

## Modelo analítico

El modelo fue optimizado para:
- consumo ejecutivo,
- cálculo de KPIs financieros,
- medidas DAX,
- análisis temporal,
- y comparativos YoY y presupuesto vs real.
