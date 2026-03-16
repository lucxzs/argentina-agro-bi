# 🌾 Commodities Dashboard — Soja, Maíz y Trigo

Dashboard de precios de commodities agrícolas con actualización automática diaria y visualización en Power BI.

![GitHub Actions](https://github.com/lucxzs/argentina-agro-bi/actions/workflows/actualizar_datos.yml/badge.svg)

---

## ¿Qué hace este proyecto?

Un script de Python extrae precios de mercado de Soja, Maíz y Trigo desde Yahoo Finance todos los días hábiles a las 10:00 AM (Argentina). Los datos se procesan, se calculan KPIs clave y se almacenan como CSV en este repositorio. Power BI lee esos archivos y actualiza el dashboard automáticamente.

## Arquitectura

```
Yahoo Finance API
      │
      ▼
commodities_etl.py       ← extracción + cálculo de KPIs
      │
      ▼
data/soja.csv
data/maiz.csv            ← historial acumulado
data/trigo.csv
      │
      ▼
GitHub Actions           ← cron job diario (lunes a viernes)
      │
      ▼
Power BI Dashboard       ← visualización de precios y KPIs
```

## KPIs calculados

| KPI | Descripción |
|-----|-------------|
| Variación % diaria | Retorno del precio respecto al día anterior |
| Promedio móvil 30d | Media de los últimos 30 días de cotización |
| Promedio móvil 90d | Media de los últimos 90 días de cotización |
| Volatilidad histórica 30d | Desviación estándar de retornos diarios (ventana 30 días) |
| Máximo del mes | Precio máximo registrado en el mes en curso |
| Mínimo del mes | Precio mínimo registrado en el mes en curso |

## Stack tecnológico

- **Python 3.11** — extracción y transformación de datos
- **yfinance** — conexión a Yahoo Finance
- **pandas** — procesamiento y cálculo de KPIs
- **GitHub Actions** — automatización del pipeline diario
- **Power BI** — visualización e interactividad

## Estructura del repositorio

```
commodities-dashboard/
│
├── .github/
│   └── workflows/
│       └── actualizar_datos.yml   ← pipeline de automatización
│
├── data/
│   ├── soja.csv
│   ├── maiz.csv
│   └── trigo.csv
│
├── commodities_etl.py             ← script principal
├── requirements.txt
└── README.md
```



