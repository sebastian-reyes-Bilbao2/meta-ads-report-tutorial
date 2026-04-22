# Meta Ads Dashboard - Guía de Replicación Paso a Paso

¡Bienvenido! Este repositorio contiene toda la información necesaria (arquitectura, diseño y reglas lógicas) para replicar nuestro Dashboard de Meta Ads desde cero. Hemos subido el **esqueleto base (index.html)** y los **estilos visuales completos (styles.css)** para que tengas el diseño moderno y profesional garantizado de antemano.

Si no sabes programar o estás utilizando una Inteligencia Artificial (como ChatGPT o Claude) para construir esto, apóyate en esta sencilla guía paso a paso. Simplemente cópiale este README junto con los archivos y el asistente entenderá qué hacer.

---

## 🛠️ Paso 1: Levantar el Diseño Base
En este repositorio incluimos los archivos `index.html` y `styles.css`. 
> **Tu primera tarea (o la de tu IA):** 
1. Crea una carpeta llamada `public` y mete esos dos archivos allí.
2. Inyecta este diseño estático en tu proyecto. Si usas React clásico o herramientas como Babel Standalone, verás que el `index.html` ya viene configurado para jalar librerías modernas de íconos (Lucide) y tipografías. 
El CSS incluye todo: temas Dark/Light, gradientes, animaciones y maquetas para tarjetas.

## ⚙️ Paso 2: Construir el Backend (Servidor Node.js)
El frontend no se puede conectar a Facebook directamente porque expondrías tu contraseña (Token). Necesitas que la IA te cree un backend.
> **Dile a tu IA:** "Por favor, créame un servidor Express.js simple. Necesito que se conecte a la **Graph API de Meta v21.0**."

**¿Qué "Endpoints" (rutas) debe crear la IA?**
* `/api/ads/campaigns`: Para que descargue la Inversión (`spend`), los Clics, las Conversiones (`actions`), el Alcance y el Costo por Resultado de cada campaña.
* Rutas de Desglose (Breakdowns):
   * `/api/breakdown/age-gender`: Para la tabla de Edades y Sexo.
   * `/api/breakdown/country` y `/api/breakdown/region`: Para tablas geográficas.
   * `/api/breakdown/platform`: Para tablas de dispositivos (Facebook vs Instagram).

## 🧠 Paso 3: Lógica Inteligente para Metas (Vital)
Este Dashboard tiene una característica especial: **no mezcla manzanas con peras**.
A nivel de código (ya sea en el Backend o en el Frontend de React), la IA debe crear un sistema automático para interpretar los **Objetivos de tu Campaña** leyendo el nombre de la misma:
* Si la campaña tiene la palabra **"schedule"**, la meta se clasifica como _Agenda_.
* Si contiene **"typeform"**, la meta se clasifica como _Typeform_.
> **Dile a tu IA:** "Crea un componente agregador que escanee las conversiones. Si el usuario filtra "Todas las campañas" y algunas consiguieron Agendas y otras consiguieron Formularios, **separa la inversión y expón tarjetas (Hero Cards) simultáneas** para cada métrica por separado."

## 📊 Paso 4: Las Fórmulas de Marketing Clave
Asegúrate que tu código use estas fórmulas en todas las tablas para que los números cuadren:
- **Click-Through Rate (CTR):** `(Clics / Impresiones) * 100`
- **Costo Por Mil (CPM):** `(Inversión / Impresiones) * 1000`
- **Frecuencia:** `Impresiones / Alcance` (si el alcance es mayor a 0).
- **Costo por Adquisición (CPA):** `Inversión total / Resultados obtenidos`.

## 🎨 Paso 5: Experiencia del Usuario (React Components)
Finalmente, pídele a tu IA que ensamble el cascarón (el `index.html`) con los datos.
* **Componente Header:** Debe tener un "Selector Modular de Campañas" en la esquina superior para elegir si ver "Todas" o una sola. No escondas esto en secciones de configuración profunda.
* **Tablas de Análisis:** Cualquier tabla que la IA construya (ej. Resultados por Edad) DEBE tener estas columnas: Inversión, Clics, Impresiones, Alcance, Frecuencia, CTR, CPC, CPM, Resultados, y CPA. ¡No dejes que omita ninguna!
* **Ajustes:** Implementa una vista sencilla de "Settings" que sólo muestre el ID de la Cuenta de Meta y el ID de la Graph App en "modo de sólo lectura" (Read Only) a manera de transparencia.

---
Con esta guía y los documentos visuales, enviar este branch a tu equipo de desarrollo o cargarlo en un Asistente IA te devolverá un Dashboard de grado empresarial, 100% funcional y dinámico, en cosa de minutos.
