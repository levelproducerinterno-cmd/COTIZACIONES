# Level Cotizaciones

Generador de cotizaciones en PDF para Level Producer. Sistema estático (un solo `index.html`), sin backend propio — el registro de cada cotización se guarda directo en Google Sheets vía Apps Script.

## Cómo subirlo a GitHub + Vercel (igual que Level Recibos y Level Renta)

1. Crea un repo nuevo en GitHub, por ejemplo `LEVEL-COTIZACIONES` (bajo tu mismo usuario/organización `levelproducerinterno-cmd`).
2. Sube el archivo `index.html` de este zip a la raíz del repo (puedes arrastrarlo directo en la interfaz web de GitHub con "Add file → Upload files", o por línea de comandos con git).
3. Entra a [vercel.com](https://vercel.com), dale "Add New... → Project", elige el repo `LEVEL-COTIZACIONES`.
4. Vercel detecta automáticamente que es un sitio estático (no necesita Build Command ni Framework Preset — puedes dejar todo en blanco/"Other"). Dale "Deploy".
5. En unos segundos te da una URL tipo `level-cotizaciones.vercel.app` — esa es la que usarás para generar tus cotizaciones desde cualquier dispositivo.

## Notas

- Todo el logo, tipografías y las slides fijas (portada, "somos una butique", logos de clientes, estrategia/metodología, repost strategy, slides finales) están incrustadas en base64 dentro del `index.html` — no dependen de ningún archivo externo aparte de las fuentes de Google Fonts y las librerías jsPDF/html2canvas (cargadas por CDN).
- El registro de cada cotización se manda a tu Google Sheet mediante el Apps Script ya configurado (mismo proyecto que usa Recibos, con una implementación separada para esta parte). Si algún día cambias esa URL, búscala en el archivo como `const SHEETS_URL = '...'` cerca del final del `<script>`.
- La columna "Cierre (sí/no)" en la pestaña "Cotizaciones" del Sheet la llenas tú manualmente cuando sepas si el prospecto cerró o no — es tu KPI de conversión.
