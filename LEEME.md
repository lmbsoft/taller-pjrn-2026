# Presentación final · Taller de IA generativa · PJRN 2026

Versión autónoma y narrada del taller: las veintidós escenas con su audio, en una
sola página que se puede publicar en internet o abrir desde un pendrive.

## Qué hay acá

```text
index.html     reproductor: navegación entre escenas y control de audio
escenas/       las 10 infografías (.png) y las 12 actividades (.html)
audio/         las 34 pistas .mp3 y su manifiesto
```

Nada de esto pide conexión a internet ni carga recursos de terceros. Se puede
servir desde cualquier servidor estático.

## Cómo funciona

Cada escena tiene su propio audio y no arranca sola: quien mira aprieta *play*
cuando quiere y cambia de escena cuando termina. Al cambiar de escena el audio
se detiene.

- Las **10 escenas de infografía** tienen una sola pista: relata lo que se ve.
- Las **12 actividades** tienen dos: *apertura*, que da la consigna sin
  adelantar la conclusión, y *cierre*, que retoma lo sucedido y fija la idea.
  Entre una y otra, quien mira hace la actividad a su ritmo. Cuando termina la
  apertura, el reproductor deja el cierre preparado pero no lo dispara.

Atajos de teclado: `←` `→` cambian de escena, `espacio` reproduce o pausa,
`J` y `L` saltan quince segundos, `I` abre el índice, `Esc` lo cierra.
En pantalla táctil se puede deslizar sobre las infografías para avanzar.
El enlace admite ancla directa: `index.html#14` abre la escena catorce.

## Publicar

Cualquier hosting estático sirve: GitHub Pages, Netlify, Cloudflare Pages, o un
directorio detrás de un servidor web. No hay backend, base de datos ni cookies.

Peso total: 57 MB, de los cuales 41 MB son audio. El reproductor usa
`preload="metadata"`, así que al abrir la página sólo se descarga la escena en
pantalla, no las 34 pistas.

Para probarlo localmente:

```bash
python3 -m http.server 8781 --directory presentacion-final
```

## De dónde sale el audio

Los guiones de `../guiones/` se sintetizaron con voz en fragmentos, porque el
sintetizador tenía un límite de longitud. Cada fragmento se cortó en un límite
de párrafo. `../sintesis/armar-audio.py` los vuelve a unir en una pista por
bloque de locución, con una pausa de párrafo en cada empalme, descartando
fragmentos repetidos e igualando el volumen de todas las pistas en −16 LUFS.

Para regenerar todo el audio después de volver a sintetizar un guion:

```bash
python3 sintesis/armar-audio.py
```

Los `.mp3` son producto derivado. La fuente editable sigue siendo el texto de
`../guiones/`: si algo suena mal, se corrige el guion, se vuelve a sintetizar y
se rearma la pista. No se editan los audios a mano.

## Escenas y duración

| # | Escena | Tipo | Audio |
|---|---|---|---|
| 001 | Introducción a la IA generativa | infografía | 5:32 |
| 002 | Búsqueda frente a generación | infografía | 6:18 |
| 003 | ¿Busca o genera? | actividad | 1:03 + 2:34 |
| 004 | Cómo se construye un modelo | infografía | 5:31 |
| 005 | Vos sos el modelo | actividad | 0:46 + 2:39 |
| 006 | Tokens, contexto y memoria | infografía | 5:33 |
| 007 | Tokenizador en vivo | actividad | 0:44 + 1:56 |
| 008 | La mesa de trabajo | actividad | 0:47 + 2:08 |
| 009 | Alucinaciones y RAG | infografía | 4:58 |
| 010 | Caza de alucinaciones | actividad | 0:42 + 2:17 |
| 011 | Alucinación frente a RAG | actividad | 0:49 + 2:40 |
| 012 | Tu copiloto, no tu oráculo | infografía | 4:34 |
| 013 | Calibrá tu criterio | actividad | 0:39 + 2:33 |
| 014 | Prompting efectivo | infografía | 3:41 |
| 015 | Constructor de prompts TCREI | actividad | 0:59 + 2:34 |
| 016 | Claves para entender y usar modelos de lenguaje | infografía | 4:20 |
| 017 | Detector de slop | actividad | 0:49 + 2:35 |
| 018 | Del chatbot al agente | infografía | 4:14 |
| 019 | Chatbot frente a agente | actividad | 0:54 + 2:30 |
| 020 | Prompt maestro para un agente | actividad | 1:17 + 2:30 |
| 021 | Seguridad al trabajar con agentes | infografía | 4:15 |
| 022 | El agente pide permiso | actividad | 1:00 + 2:54 |

Total de locución: 89 minutos. Con el tiempo de interacción de las doce
actividades, el recorrido completo ronda las dos horas y media.
