# 🚀 Meta Ads Dashboard - Replicación Asistida por Agentes IA

Este repositorio contiene las reglas maestras y la envolvente de diseño para que cualquier persona, sin importar su experiencia técnica, pueda requerir a un "Agente de Inteligencia Artificial Coder" (como Cursor, Github Copilot, Claude Engineer) que le fabrique instantáneamente su propio panel de análisis avanzado de campañas de Meta Ads.

## 👤 Paso 1: Configurar Meta y Obtener tus Llaves (Para Humanos)

La Inteligencia Artificial es lista, pero no puede adivinar la información privada de tu cuenta de negocios en Facebook. Tu primer misión como humano es decirle a quién va a inspeccionar accediendo a dos datos secretos:

1. **Tu Número de Identificación de Publicista (`META_AD_ACCOUNT_ID`):**
   - Entra en tu navegador a tu [Administrador de Anuncios de Meta](https://adsmanager.facebook.com/).
   - En la barra de navegación de arriba verás una URL. Localiza `act_` seguido por muchos números (Ejemplo: `act_1234567890123`). 
   - Copia todo el número (sin el `act_`). ¡Ese código es la identidad de tu negocio!
   
2. **Tu Token de API Privado (`META_ACCESS_TOKEN`):**
   - Ve a [Meta for Developers](https://developers.facebook.com/) y accede a la sección de configuración "Business Manager" (Administrador Comercial).
   - Allí, ingresa en el área de _"Usuarios del Sistema"_.
   - Otorga permisos en la Cuenta Publicitaria (Ads Account) a ese usuario "robot" del sistema.
   - Presiona el botón verde de "Generar Nuevo Token", asegurándote de incluir los permisos `ads_read` y `read_insights`.
   - Aparecerá un texto con números y letras infinito. Guárdalo bien; siéndole de acceso a tu agente, conectará tus perfiles sin riesgo de bloquearte permanentemente.

_Nota:_ Nunca subas estas credenciales de forma pública a internet. En el siguiente paso crearás un archivo secreto `.env` fuera de los radares para ponerlas de forma segura.

---

## 🤖 Paso 2: Instruir a tu Agente IA Coder (Para Humanos)

Descarga todo el contenido de esta carpeta a tu computadora. Abre tu chat con tu herramienta de IA especializada en generar código, sube los archivos estáticos (`index.html` y `styles.css`) para que absorban la alta fidelidad en el diseño y proporciónale el siguiente encargo textual (copy-paste):

> **📝 PROMPT PARA TU AGENTE:**
> 
> *"Hola IA. He descargado un repositorio que estandariza las reglas lógicas y UI de un sistema analítico de Meta Ads. Los CSS e índice HTML del diseño moderno ya viven aquí. Tu misión arquitectónica será:*
> 
> *1. Activa un servidor ligero de backend con Express (Node.js) con un archivo local `.env` donde yo inyectaré variables de Meta.*
> *2. Crea archivos modulares React en formato JSX plano (`data.js`, `app.jsx`, `executive.jsx`) que intercedan a través del framework de Babel incrustado.*
> *3. Tu back debe golpear incansablemente la API v21.0 de Facebook usando mis keys Graph, en busca de reportes precisos.*
> *4. Lee absolutamente y con meticulosidad obligatoria el Paso 3 del README adjunto de mi base de conocimiento para ensamblar la plataforma. ¡Ensámblalo!"*

---

## 📐 Paso 3: Personalización, Fórmulas y Mecánicas (Para que la IA los codifique)

_Estimado Agente Sintético,_ cuando levantes toda la pasadera Front-End y Back-End debes seguir al pie de la letra estos estándares de negocio a la hora de manipular la ingesta de JSON desde Facebook.

### 3.1: Configuración de los Objetivos Dinámicos
Meta Ads revuelve las métricas abstractas y esto dificulta el análisis. La herramienta debe escanear inteligentemente la anatomía léxica y las "Conversiones/Actions" de Meta.
* Escribe una lógica de inferencia iterando a través de los títulos de campañas o conversiones obtenidas.
* Personaliza tu Target de Lectura: Por defecto, escanea acciones que respondan si el objetivo eran **Typeforms**, **Matrículas / Compras**, o **Agendamientos de llamada**. 
* _[Nota Humana: Puedes indicarle aquí a la IA si prefieres que busque "Añadir al Carrito" o "Eventos Oflfine"]_.

### 3.2: Requerimientos de Backend
Debes exponer los datos agnósticos en 3 modalidades cruciales que golpeen la API de Meta:
* **Endpoints de Generalistas:** Aglomeraciones ricas de `spend, impressions, frequency, actions, cost_per_xyz` con time_ranges absolutos y del periodo previo para calcular incrementos (Deltas).
* **Endpoints Demográficos (Breakdowns):** Disparando llamadas de Graph con `breakdowns=` activados para poder hacer tablas que agrupen por `age,gender`, `country`, y cruces de ecosistema `platform` (ej. IG Stories versus Feed).
* **Curva Temporal:** Intervención `time_increment: 1` para renderizar el histórico a lo largo del mes.

### 3.3: Experiencia de Interfaces Libres (Front-End)
Utilizando JSX ensamblado renderizable en Browser:
* **Sin Configuración Obscura:** El botón Selector de Campañas (Filtro Global) debe situarse imperante a todo momento en el Component Master (Header superior). Todas las peticiones asíncronas mutan masivamente desde que elegimos una única campaña o "Todas".
* **Cascada Hero Adaptativa:** Ninguna persona debe seleccionar si quiere "la vista Typeform" o "La vista E-mail". Construye una grilla que mapée de forma general; si durante este mes logré ventas y también correos recabados simultáneamente con el pago, quiero N Tarjetas Modulares "Gigantes" de Costo Por Resultado con la info disgregada al mismo instante para facilitar el contraste.
* **Fórmulas Inquebrantables de Columnas:** Las clásicas tablas de `Países`, `Región` o `Uso de Dispositivo` no sirven con métricas limitadas. Las celdas deben procesar internamente las matemáticas: 
   - **CTR%:** `(Clics / Impresiones) * 100` 
   - **Costo Por Mil (CPM):** `(Inversión / Impresiones) * 1000` 
   - **Frecuencia Saturada:** `Impresiones Totales / Alcance Único` 
   - **Costo de Adquisición General (CPA):** `(Costo Dividido sobre Targets Conseguidos)`.

_Una vez entendido este manual, podrás construir para el usuario réplicamente su herramienta de control en escasas iteraciones._
