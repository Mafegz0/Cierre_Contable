# 03 – Data Preparation

## Propósito de esta fase

Esta fase documenta las transformaciones aplicadas sobre las fuentes financieras utilizadas en el modelo BI de Cierre Contable.

Aquí se realizan procesos de:
- limpieza,
- normalización,
- homologación,
- enriquecimiento,
- consolidación
- y estructuración analítica

con el fin de garantizar consistencia, trazabilidad y calidad de los datos antes del modelado en Power BI.

---

## Documentos incluidos

### PowerQuery_Transformations.md

Documentación técnica de las transformaciones implementadas en Power Query.

Incluye:
- Conexiones a SharePoint
- Limpieza y normalización de datos
- Conversión de tipos
- Estandarización de columnas
- Reglas de homologación financiera
- Construcción de campos temporales
- Consolidación de tablas
- Creación de dimensiones derivadas

Aplicado a:
- Estados Financieros
- Presupuesto
- Balance General
- Centros de costo
- Dimensiones financieras

---

### Reglas_Transformacion.xlsx

Matriz funcional de reglas de transformación del modelo financiero.

Documenta:
- Tabla origen
- Campo origen
- Campo destino
- Tipo de transformación
- Regla aplicada
- Justificación funcional
- Resultado esperado
- Impacto analítico

Incluye reglas relacionadas con:
- Limpieza de texto
- Homologación financiera
- Conversión de estructura wide → long
- Construcción de periodos
- Ajustes de signo financiero
- Clasificaciones macro
- Normalización de dimensiones
- Consolidación de hechos

---