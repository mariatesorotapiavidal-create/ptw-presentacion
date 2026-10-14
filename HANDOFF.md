# Handoff · Web "IA en Acción · Panel" (NXTEP en Perú Tech Week 2026)

Actualizado: 2026-10-13 (noche: + DMC y encuesta)

## Qué es
Web de pantallas que se proyecta durante el panel y networking de **IA en Acción** (14 de octubre). Es un solo archivo HTML sin dependencias. Las pantallas encajan con scroll-snap y se manejan con clic, flechas o clicker.

- Archivo: `outputs/fondo-preguntas/index.html`
- Imágenes: `outputs/fondo-preguntas/img/`
- Ver en local: `python -m http.server 8080`, ejecutado dentro de `outputs/fondo-preguntas`, y luego abrir http://localhost:8080/
- Captura de una sola pantalla: `?solo=N&step=K`, por ejemplo `?solo=5&step=7` para la pregunta 7. Con Chrome headless: `--window-size=1920,1080 --virtual-time-budget=5000 --screenshot=...`
- Atajos en vivo: → / espacio / clic = siguiente · ← = anterior · 1–9 = ir a pantalla · F = pantalla completa · H = ocultar los puntos de navegación

## Pantallas (en orden)
| # | id | Contenido |
|---|----|-----------|
| 1 | s1 | Hero: "Casos reales de / IA en Acción / en empresas líderes del Perú", fecha, "Panel + Networking", flecha y ticker |
| 2 | s4 | Dinámica 1 (antes de presentar speakers) con **cronómetro 03:00**: botón play/pausa redondo a la derecha (o tecla P). Al llegar a 0 parpadea en rojo 5 s y vuelve a 03:00 en pausa |
| 3 | s2 | Speakers con logros. **Un clic = un speaker**; con los 3 visibles pasa de pantalla |
| 4 | s2b | Speakers resumido |
| 5 | s2c | **Preguntas 1–15**, un clic por pregunta |
| 6 | s3 | "No es solo venir a escuchar. Es venir a conectar." |
| 7 | s5 | Dinámica 2 |
| 8 | s-dmc | **Becas DMC**: "Participa por 3 becas al 100% gracias a DMC Institute" + Línea Data (11) y Línea Dev (6). Fuente: `inputs/cursos-dmc.jpg` |
| 9 | s6 | Dinámica 3 |
| 10 | s7 | Síguenos: QR de WhatsApp, LinkedIn e Instagram |
| 11 | s-enc | Encuesta: "Cuéntanos qué te pareció este evento" + QR `img/qr-encuesta.png` |

Atajos: 1–9 van a esas pantallas, End = última (encuesta).

## Cómo funciona por dentro
- `stepper(id, min, max, render)` en el JS crea pasos dentro de una pantalla (speakers: 0–3, preguntas: 1–15). `next()` y `prev()` avanzan el paso y, en el extremo, cambian de pantalla. Si se vuelve desde una pantalla posterior, la pantalla se abre en su último paso.
- Las preguntas están en `<p class="q" data-cat="...">` dentro de `.q-stage`. Para editarlas, cambia el texto ahí; el contador se calcula solo.
- Datos de speakers: Diego Asmat (BCP), Diego F. Hinojosa (Credicorp) y Marleny Barrueta (Antamina). La foto de Marleny es `img/marleny-barrueta-sp.jpg`. Se renombró para evitar la caché del navegador y usa `object-position:50% 22%`.
- Identidad: negro, degradado azul #2563EB → rojo #EF4B2F, Inter Tight / Lexend Zetta / JetBrains Mono, red de nodos animada en canvas.

## Pendientes / a confirmar con María
- Escanear los 3 QR con el celular. No se pudieron decodificar aquí, y los de LinkedIn e Instagram tienen el mismo diseño.
- El bullet 3 de Diego Hinojosa ("experiencias financieras más simples…") es más un objetivo que un logro. Cambiarlo si llega un dato concreto.
- Se quitó el texto "Los casos que impulsan, el impacto que buscan…" de la pantalla 2. Se puede volver a poner bajo el título.
- Si alguien baja con la rueda del mouse, se saltan los pasos. En vivo, usar clic, flechas o el clicker.
- Las copias de las versiones anteriores quedaron en el scratchpad de la sesión, que es temporal y no va a durar.

## Pendientes nuevos
- Escanear el QR de la encuesta con el celular.
- Busco Chamba se quitó de la web por decisión de María.
- La lista DMC omite ID y tipo (todas son ESPE = especialización). Hay 3 cursos que aparecen en ambas líneas, igual que en la fuente.
