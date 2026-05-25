# 02 – Data Understanding

## Propósito de esta fase

Esta fase documenta y analiza las fuentes de información utilizadas en el modelo BI financiero de Cierre Contable.

Aquí se realiza el levantamiento técnico y funcional de los datos, identificando:
- estructura de las fuentes,
- granularidad,
- relaciones,
- reglas de calidad,
- y consideraciones necesarias para el modelado analítico.

Esta documentación garantiza trazabilidad, consistencia y entendimiento técnico de la información utilizada en el visualizador financiero.

---

## Documentos incluidos

### data_inventory.xlsx
Inventario centralizado de las fuentes del modelo.

Incluye:
- Dominio funcional
- Tipo de fuente
- Sistema origen
- Granularidad
- Frecuencia
- Responsables
- Sensibilidad
- Consumidores
- Observaciones técnicas

---

### data_dictionary.xlsx
Diccionario técnico y funcional de datos.

Documenta:
- Tablas y hojas origen
- Columnas
- Tipos de dato
- Descripción funcional
- Ejemplos de valores
- Llaves y relaciones
- Reglas de negocio

---

### data_quality_rules.yaml
Framework de reglas de calidad del modelo financiero.

Incluye validaciones sobre:
- Completitud
- Validez
- Consistencia
- Integridad referencial
- Exactitud
- Unicidad

Aplicado a:
- Estados Financieros
- Presupuesto
- Balance General
- Centros de costo
- Dimensiones financieras

---