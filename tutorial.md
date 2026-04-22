# Guía de Replicación: Meta Ads Dashboard

Esta guía contiene la información conceptual, lógica de datos y directrices de arquitectura necesarias para reconstruir la lógica del Dashboard de Meta Ads. **No incluye datos propios, código, ni diseño estricto**. Está diseñada como Prompt o Contexto para que un LLM (como Claude) actúe como tu ingeniero.

## 1. Objetivo General
Construir un panel de análisis (Dashboard) frontend/backend que centralice el desempeño de múltiples campañas de pauta publicitaria, con desglose de audiencias y un sistema de lectura inteligente de métricas por "Metas de Conversión".

## 2. Requerimientos de Backend (Intermediario con Meta API)
El servidor actúa como broker hacia la Graph API de Meta. Debe contar con endpoints que devuelvan:
- **Resumen Listado de campañas y Ads:** Extrayendo `spend`, `impressions`, `clicks`, `reach`, `frequency`, y los objetos ricos de `actions` y `conversions`.
- **Desgloses (Breakdowns):** Peticiones hacia la API con `breakdowns` para `age,gender`, `country`, `region`, y `platform,device_platform`.
- **Desglose de Tiempo Diario:** Obtener la curva de gastos con `time_increment: 1`.

## 3. Core Lógico: Reglas de Análisis de Datos (Data layer)
Al recibir las campañas, la aplicación no debe amontonar los "resultados" ciegamente. 
### Inferencia de Metas
El LLM debe escribir una lógica de "Inferencia del Objetivo":
- Ej. Escanear el nombre de una Campaña (`name.includes()`).
- Identificar sub-categorías de meta: **Schedule** (Agendas), **Typeform**, o **Lead Gen**.
- Cada categoría tiene una cadena de eventos API jerárquica (Ej. un objetivo Typeform prioriza buscar la meta de action_type `offsite_conversion.fb_pixel_custom.TypeformSubmit`).

### Cálculo Modular
Todas las vistas o herramientas de agrupación siempre deben contar con:
- **CTR:** (Clics / Impresiones) * 100
- **CPM:** (Inversión / Impresiones) * 1000
- **CPA (Costo por Resultado):** Inversión / Resultados útiles (según Target de meta calculada)
- **Frecuencia:** Impresiones / Alcance (o un promedio heredado).

## 4. Patrones de Interfaz y UI UX
Instruye al LLM para que respete estas mecánicas operativas a la hora de armar el Frontend:
- **Agnosticismo Global:** Incorporar en la zona superior de navegación un Selector para filtrar globalmente los gráficos entre "Todas las Campañas" o una campaña en específico. No esconder esto en submenús de configuración.
- **Dashboard Autómata (Hero dinámico):** La UI nunca le preguntará al usuario "qué objetivo ver hoy". El código debe iterar las métricas activas; si en los datos filtrados localiza >0 Agendas y >0 Formularios Typeform, inyectará dos modulares "Hero" principales en forma de lista vertical (uno por cada meta alcanzada), independizando el CPA y resultados de cada una totalmente.
- **Tablas Analíticas Holísticas:** En cada tabla analítica (Geo, Demografía, Plataformas), proveer un Selector de Columnas que integre el menú completo de opciones (Inv, Impr, Alcance, Clics, Frec, CTR, CPC, CPM, Res, CPA), permitiendo una investigación 360 de cada subconjunto de Data.
