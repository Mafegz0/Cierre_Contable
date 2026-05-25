# PowerQuery_Transformations

## Objetivo

Documentar las transformaciones aplicadas en Power Query para preparar las fuentes del modelo BI financiero de Cierre Contable.

Este documento describe la lógica aplicada sobre cada fuente, sin reemplazar el código M original. Su propósito es dejar trazabilidad técnica de los pasos de limpieza, normalización, homologación, enriquecimiento y consolidación utilizados antes del modelado en Power BI.

---

# 1. Estados Financieros Reales

## 1.1 REAL_2026

**Fuente:** `Real_2026.xlsx`  
**Tipo:** Transaccional  
**Resultado:** tabla preparada de reales 2026 para Estado de Resultados.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Filtrado de hojas cuyo nombre inicia con `Real_2026`.
3. Promoción de encabezados en cada hoja.
4. Anexado de hojas para consolidar la fuente en una sola tabla.
5. Cambio de tipos de datos para campos contables, financieros y descriptivos.
6. Renombramiento de columnas para estandarizar nomenclatura:
   - `MES ` → `MES`
   - `Llave` → `LLAVE`
   - `Clasificacion` → `CLASIFICACION`
   - `Cuentas a 6` → `CUENTAS_6`
   - `Cuentas a 4 y Descuentos` → `CUENTAS_4_DESCUENTOS`
   - `CLAF3` → `AREA`
7. Creación de `CLASIFICACION_CLEAN` mediante limpieza de texto.
8. Creación de `CLASIFICACION_3` para separar Personal Comercial, Personal Experiencia del Estudiante y Educación Continua.
9. Creación de `CLASIFICACION_MACRO` para homologar Educación Continuada y Bootcamps.
10. Adición del campo `ANIO` con valor 2026.
11. Creación de `NOMBRE_MES` a partir de año y mes.
12. Creación de `PERIODO` como fecha del primer día del mes.
13. Creación de `NETO_AJUSTADO`, invirtiendo el signo para cuentas de ingreso `N4`.
14. Creación de `AREA_CLEAN`, normalizando valores nulos, ceros y textos del campo `AREA`.
15. Conversión final de tipos de datos.
16. Adición del campo `EMPRESA`.

---

## 1.2 REAL_2025

**Fuente:** `Real_2025.xlsx`  
**Tipo:** Transaccional histórica  
**Resultado:** tabla preparada de reales 2025 para comparativos.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Filtrado de hojas cuyo nombre inicia con `Real_2025`.
3. Promoción de encabezados en cada hoja.
4. Anexado de hojas para consolidar la fuente histórica en una sola tabla.
5. Cambio de tipos de datos para campos contables, financieros y descriptivos.
6. Renombramiento de columnas bajo la misma estructura de `REAL_2026`.
7. Creación de `CLASIFICACION_CLEAN`.
8. Creación de `CLASIFICACION_3` para homologaciones específicas de personal y educación continua.
9. Creación de `CLASIFICACION_MACRO`.
10. Adición del campo `ANIO` con valor 2025.
11. Creación de `NOMBRE_MES`.
12. Creación de `PERIODO`.
13. Creación de `NETO_AJUSTADO`, invirtiendo el signo para cuentas de ingreso `N4`.
14. Creación de `AREA_CLEAN`.
15. Conversión final de tipos de datos.
16. Adición del campo `EMPRESA`.

---

## 1.3 REAL_2024

**Fuente:** `Real_2024.xlsx`  
**Tipo:** Histórica agregada  
**Resultado:** tabla histórica agregada para comparativos de Estado de Resultados.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la hoja `Real_2024`.
3. Promoción de encabezados.
4. Cambio de tipos de datos para `MES`, `CLASIFICACION`, `NETO_AJUSTADO` y `ANIO`.
5. Creación de `NOMBRE_MES`.
6. Creación de `PERIODO`.
7. Creación de `CLASIFICACION_3` a partir de limpieza de `CLASIFICACION`.
8. Creación de `CLASIFICACION_MACRO` a partir de `CLASIFICACION_CLEAN`.
9. Conversión final de tipos de datos.
10. Adición del campo `EMPRESA`.

### Consideración

Esta fuente no contiene detalle transaccional ni centro de costo. Por tanto, su uso se limita a comparativos agregados.

---

# 2. Reales por empresa A y L

## 2.1 REAL_A 2026

**Fuente:** `Real_A.xlsx`  
**Tipo:** Semi-agregado  
**Resultado:** reales 2026 de A normalizados a formato analítico.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la hoja `Real_2026_A`.
3. Promoción de encabezados.
4. Cambio de tipos de datos.
5. Filtrado de registros con `IZQUIERDO` igual a 4 o 5 para Estado de Resultados.
6. Unpivot de columnas mensuales para transformar estructura wide a formato largo.
7. Renombramiento de columnas: `Claf 2` → `CLASIFICACION`, `Codigo` → `CODIGO_CONTABLE`, `Nombre` → `L_PLACON_NOMBRE_CUENTA`.
8. Adición del campo `ANIO` con valor 2026.
9. Conversión de `NOMBRE_MES` a número de mes.
10. Creación del campo `PERIODO`.
11. Creación de `CLASIFICACION_MACRO` mediante limpieza de texto.
12. Adición del campo `EMPRESA`.
13. Creación de `NETO_AJUSTADO`, invirtiendo el signo cuando `IZQUIERDO = 4`.
14. Conversión final de tipos de datos.

---

## 2.2 REAL_L 2026

**Fuente:** `Real_L.xlsx` 
**Tipo:** Semi-agregado  
**Resultado:** reales 2026 normalizados a formato analítico.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la hoja `Real_2026_L`.
3. Promoción de encabezados.
4. Cambio de tipos de datos.
5. Filtrado de registros con `IZQUIERDO` igual a 4 o 5 para Estado de Resultados.
6. Unpivot de columnas mensuales.
7. Renombramiento de columnas: `Claf 2` → `CLASIFICACION`, `Codigo` → `CODIGO_CONTABLE`, `Nombre` → `L_PLACON_NOMBRE_CUENTA`.
8. Adición del campo `ANIO` con valor 2026.
9. Conversión de `NOMBRE_MES` a número de mes.
10. Creación del campo `PERIODO`.
11. Creación de `CLASIFICACION_MACRO`.
12. Adición del campo `EMPRESA`.
13. Creación de `NETO_AJUSTADO`, invirtiendo el signo cuando `IZQUIERDO = 4`.
14. Conversión final de tipos de datos.

---

## 2.3 REAL_2025_A

**Fuente:** `Real_2025_A.xlsx`  
**Tipo:** Agregado histórico  
**Resultado:** reales 2025 normalizados a formato largo.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la hoja `Real_2025_A`.
3. Promoción de encabezados.
4. Cambio de tipos de datos.
5. Unpivot de columnas mensuales, conservando `CLASIFICACION`.
6. Creación del campo `ANIO` con valor 2025.
7. Conversión del nombre del mes a número de mes.
8. Creación del campo `PERIODO`.
9. Creación de `CLASIFICACION_MACRO` mediante limpieza de texto.
10. Adición del campo `EMPRESA`.
11. Conversión final de tipos de datos.

---

## 2.4 REAL_2025_L

**Fuente:** `Real_2025_L.xlsx`  
**Tipo:** Agregado histórico  
**Resultado:** reales 2025 normalizados a formato largo.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la hoja `Real_2025_L`.
3. Promoción de encabezados.
4. Cambio de tipos de datos.
5. Unpivot de columnas mensuales, conservando `CLASIFICACION`.
6. Creación del campo `ANIO` con valor 2025.
7. Conversión del nombre del mes a número de mes.
8. Creación del campo `PERIODO`.
9. Creación de `CLASIFICACION_MACRO`.
10. Adición del campo `EMPRESA`.
11. Conversión final de tipos de datos.

---

# 3. Presupuesto

## 3.1 PRESUPUESTO_2026

**Fuente:** `Presupuesto_2026.xlsx`  
**Tipo:** Planeación presupuestal detallada  
**Resultado:** presupuesto 2026 normalizado a formato analítico.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la hoja `ppto_2026`.
3. Promoción de encabezados.
4. Cambio de tipos de datos para campos de empresa, rubro, cuenta, CECO y meses.
5. Renombramiento de columnas: `Rubro_Local` → `CLASIFICACION`, `EMPRESA ` → `EMPRESA`.
6. Unpivot de columnas mensuales de `Ene` a `Dic`.
7. Creación de `NOMBRE_MES` a partir de abreviaturas mensuales.
8. Adición del campo `ANIO` con valor 2026.
9. Conversión de `NOMBRE_MES` a número de mes.
10. Creación del campo `PERIODO`.
11. Creación de `CLASIFICACION_MACRO` mediante limpieza de texto.
12. Conversión final de tipos de datos.

---

## 3.2 PRESUPUESTO_2025

**Fuente:** `Presupuesto_2025.xlsx`  
**Tipo:** Planeación histórica agregada  
**Resultado:** presupuesto 2025 normalizado a formato largo.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la hoja `Hoja1`.
3. Promoción de encabezados.
4. Cambio de tipos de datos.
5. Renombramiento de `Column1` a `CLASIFICACION`.
6. Unpivot de columnas mensuales.
7. Renombramiento de campos: `Atributo` → `NOMBRE_MES`, `Valor` → `PRESUPUESTO`.
8. Adición del campo `ANIO` con valor 2025.
9. Conversión de `NOMBRE_MES` a número de mes.
10. Creación del campo `PERIODO`.
11. Creación de `CLASIFICACION_MACRO`.
12. Adición del campo `EMPRESA`.
13. Conversión final de tipos de datos.

---

# 4. Balance General

## 4.1 BALANCE_2026

**Fuente:** `Balance_Revisada_2026.xlsx`  
**Tipo:** Snapshot actual de balance  
**Resultado:** balance 2026 preparado para análisis de activos, pasivos y patrimonio.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la hoja `Hoja1`.
3. Promoción de encabezados.
4. Cambio de tipos de datos.
5. Renombramiento de columnas: `Suma de NETO` → `NETO`, `Clasificacion` → `CLASIFICACION`, `Cuentas a 6` → `CUENTAS_6`, `Cuentas a 4 y Descuentos` → `CUENTAS_4_DESCUENTOS`.
6. Adición del campo `ANIO` con valor 2026.
7. Creación de `NUMERO_MES`, asignando mes 1 cuando `MES = 0`.
8. Creación de `TIPO_SALDO`: `Saldo inicial` cuando `MES = 0`, `Movimiento` para los demás casos.
9. Creación del campo `PERIODO`.
10. Creación de `CLASIFICACION_BALANCE` mediante limpieza de texto.
11. Conversión final de tipos de datos.

---

## 4.2 BALANCE_2025

**Fuente:** `Balance_2025.xlsx`  
**Tipo:** Snapshot histórico agregado  
**Resultado:** balance 2025 preparado para comparativo histórico.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la hoja `Hoja1 (2)`.
3. Promoción de encabezados.
4. Cambio de tipos de datos.
5. Renombramiento de columnas: `Suma de NETO` → `NETO`, `Clasificacion` → `CLASIFICACION`.
6. Adición del campo `ANIO` con valor 2025.
7. Creación de `NUMERO_MES`, asignando mes 1 cuando `MES = 0`.
8. Creación de `TIPO_SALDO`.
9. Creación del campo `PERIODO`.
10. Creación de `CLASIFICACION_BALANCE`.
11. Conversión final de tipos de datos.

---

# 5. Dimensiones

## 5.1 TABLA_GRUPOS

**Fuente:** `TABLA_GRUPOS.xlsx`  
**Tipo:** Dimensión financiera del Estado de Resultados  
**Resultado:** dimensión de clasificación financiera homologada.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la tabla `Tabla1`.
3. Cambio de tipos de datos.
4. Creación de `CLASIFICACION_MACRO` mediante limpieza de `CLASIFICACION`.

### Consideración

La columna `GRUPO_MACRO ` conserva un espacio final en el origen. Se recomienda estandarizarla en una versión posterior como `GRUPO_MACRO`.

---

## 5.2 BALANCE_GRUPOS

**Fuente:** `BALANCE_GRUPOS.xlsx`  
**Tipo:** Dimensión financiera de Balance General  
**Resultado:** dimensión homologada para clasificar activos, pasivos y patrimonio.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la tabla `Tabla1`.
3. Cambio de tipos de datos.
4. Renombramiento de columnas: `Clasificacion` → `CLASIFICACION`, `Clasificacion_1` → `CLASIFICACION_1`, `Clasificacion_2` → `CLASIFICACION_2`, `orden` → `ORDEN`.
5. Creación de `CLASIFICACION_BALANCE` mediante limpieza de texto.

---

## 5.3 CECOS

**Fuente:** `CECOS.xlsx`  
**Tipo:** Dimensión de centros de costo  
**Resultado:** dimensión enriquecida para análisis por unidad académica, administrativa, programa, área y modalidad.

### Transformaciones aplicadas

1. Conexión al archivo ubicado en SharePoint.
2. Selección de la tabla `Tabla1`.
3. Cambio de tipos de datos.
4. Creación de `FACULTADES_AREAS` mediante limpieza y conversión a mayúsculas del campo `Área`.
5. Creación de `UNIDADES`, clasificando Unidad Académica o Unidad Administrativa según área.
6. Creación de `PROGRAMAS_AREAS` mediante limpieza y conversión a mayúsculas del campo `Programas`.
7. Renombramiento de columnas: `Clase` → `CLASE`, `Tipo` → `TIPO`, `Modalidad` → `MODALIDAD`.
8. Conversión final de tipos de datos.
9. Creación de `FAC_AREA`, abreviando facultades y homologando Escuela de Derecho como `F. DERECHO`.
10. Conservación de la estructura final para uso en segmentación analítica.

---

# 6. Tablas consolidadas

## 6.1 REAL

**Origen:** combinación de tablas reales.  
**Resultado:** tabla consolidada de hechos reales.

### Tablas combinadas

- `Real_2026`
- `Real_2025`
- `Real_2024`
- `Real_2025_A`
- `Real_2025_L`
- `Real_2026_L`
- `Real_2026_A`

### Transformaciones aplicadas

1. Consolidación mediante `Table.Combine`.
2. Eliminación de columnas no requeridas en fuentes 2026 A y L: `IZQUIERDO`, `Claf 1`, `Saldo Inicial` / `SALDO INICIAL`.
3. Conversión de `CENTRO_COSTO` a texto.
4. Conversión de `EMPRESA` a texto.

---

## 6.2 PRESUPUESTO

**Origen:** combinación de presupuestos 2025 y 2026.  
**Resultado:** tabla consolidada de presupuesto.

### Tablas combinadas

- `Presupuesto_2026`
- `Presupuesto_2025`

### Transformaciones aplicadas

1. Consolidación mediante `Table.Combine`.

---

## 6.3 BALANCE

**Origen:** combinación de balances 2025 y 2026.  
**Resultado:** tabla consolidada de Balance General.

### Tablas combinadas

- `Balance_2026`
- `Balance_2025`

### Transformaciones aplicadas

1. Consolidación mediante `Table.Combine`.

---

# 7. Dimensión Empresa

## DIM_EMPRESA

**Origen:** tabla consolidada `Presupuesto`  
**Tipo:** dimensión derivada  
**Resultado:** dimensión de empresas para relaciones y segmentación.

### Transformaciones aplicadas

1. Selección de la columna `EMPRESA`.
2. Eliminación de duplicados.
3. Creación de `EMPRESA_PL` mediante limpieza, recorte de espacios y conversión a mayúsculas.

---

# Consideraciones generales

- Las columnas mensuales fueron transformadas a formato largo mediante Unpivot para facilitar el modelado dimensional.
- Las fuentes históricas presentan distintos niveles de granularidad, por lo cual se consolidan respetando su nivel de detalle disponible.
- Las clasificaciones financieras fueron limpiadas mediante `Text.Trim` y `Text.Clean`.
- Los valores financieros se transformaron a tipo moneda cuando correspondía.
- Se crearon campos temporales comunes como `ANIO`, `MES`, `NOMBRE_MES` y `PERIODO`.
- Se generaron campos de homologación como `CLASIFICACION_MACRO` y `CLASIFICACION_BALANCE`.
- Se creó la tabla consolidada de hechos reales y tablas consolidadas de presupuesto y balance.
- Se creó una dimensión derivada de empresa para soportar segmentación y relación en el modelo.

---

# Resultado de la fase

La preparación de datos deja las fuentes financieras listas para la fase de modelado, permitiendo construir relaciones, medidas DAX y visualizaciones sobre estructuras limpias, homologadas y consistentes.
