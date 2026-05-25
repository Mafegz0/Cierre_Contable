# Cierre Contable – Modelo BI Financiero

Repositorio técnico para el diseño e implementación de un modelo analítico de
cierre contable, enfocado en la construcción de:

- Estado de Resultados
- Balance General
- Indicadores financieros estratégicos

El proyecto está orientado a la estandarización de la información contable,
mejorando la calidad del dato, la trazabilidad y la toma de decisiones mediante
un modelo en Power BI.

---

## Objetivos del Proyecto

- Consolidar la información financiera en un modelo único.
- Estandarizar clasificaciones contables (ingresos, egresos, ebitda, excedentes...).
- Garantizar consistencia entre real, presupuesto y año anterior.
- Definir un modelo dimensional financiero.
- Construir un dashboard estratégico en Power BI.
- Documentar reglas de negocio y transformación de datos.

---

## Arquitectura General

El proyecto se estructura en dos capas principales:

### Data Layer
- Fuentes en Excel
- Transformaciones y homologaciones
- Creación de variables calculadas
- Definición de llaves y granularidad

### BI Layer
- Modelo en Power BI
- Medidas DAX financieras
- Estados financieros:
  - Estado de Resultados
  - Balance General
- Indicadores y comparativos:
  - Real vs Presupuesto
  - Año actual vs Año anterior

---

## Metodología

El proyecto sigue el enfoque ASUM-DM estructurado en 6 fases:

1. Business Understanding
2. Data Understanding
3. Data Preparation
4. Modeling
5. Evaluation
6. Deployment

Cada fase cuenta con documentación formal y entregables definidos.
---

## Estructura del Repositorio
```
Credito-y-Cartera/
│
├── 01_Business_Understanding/
│   ├── Project_Charter.xlsx
│   ├── Risk_Register.xlsx
│   ├── Stakeholders_RACI.xlsx
│   ├── Decision_Log.md
│   └── README.md
│
├── 02_Data_Understanding/
│   ├── data_inventory.xlsx
│   ├── data_dictionary.xlsx
│   ├── data_quality_rules.yaml
│   └── README.md
│
├── 03_Data_Preparation/
│   ├── PowerQuery_Transformations.md 
│   ├── Reglas_Transformacion.xlsx
│   └── README.md
│
├── 04_Modeling/
│   ├── Modelo_Dimensional.png
│   ├── Modelo_Descripcion.md
│   └── README.md
│   ├── visualization/      
│         ├── Medidas_DAX.xlsx
│         ├── KPIs_Definicion.md
│         ├── Tablas_Calculadas.md
│
├── 05_Evaluation/
│   ├── validation_report.md
│
├── 06_Deployment/
│   ├── powerbi/
│   ├── Manual_de_usuario.pdf
│
├── Data/
│
├── .gitignore
└── README.md

```

---

## Stack técnico
- Microsoft Excel
- Power BI
- Git & GitHub

## Alcance técnico

Incluye:

- Modelado de datos financiero
- Definición de reglas de negocio
- Construcción de métricas financieras
- Documentación estructurada del modelo

## Publicación y Consumo

El visualizador financiero es publicado en Power BI Service y consumido por áreas financieras y directivas mediante acceso corporativo institucional.


##  Responsable técnico

Coordinadora de Analítica de negocio y riesgos 
