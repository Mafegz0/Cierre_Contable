# Tablas_Calculadas

## Objetivo

Documentar las tablas calculadas creadas en Power BI para soportar análisis temporal, presentación ejecutiva y segmentación del modelo financiero.

---

## Dim_Tiempo

Tabla calendario creada en DAX para permitir análisis mensual entre 2024 y 2026.

### Uso
- Relacionar Real, Presupuesto y Balance.
- Habilitar comparativos por año, mes y periodo.
- Soportar medidas de año anterior.

---

## EstadoResultado_Jer

Tabla estructural creada manualmente con `DATATABLE`.

### Motivo
Responde a la decisión DL-02, donde se definió una estructura de presentación financiera alineada con comités ejecutivos.

### Uso
- Ordenar el Estado de Resultados.
- Crear jerarquías personalizadas.
- Mostrar subtotales como EBITDA, Resultado Operacional Neto y Excedentes.
- Soportar medidas específicas de presentación gerencial.

---

## Dim_Empresa

Tabla derivada desde Presupuesto para consolidar empresas del modelo.

### Uso
- Filtrar información por empresa.
- Soportar reglas específicas como el descuento de ingresos para terceros