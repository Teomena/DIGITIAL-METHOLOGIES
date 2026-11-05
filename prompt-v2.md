# Prompt de construcción del MVP — SPORTRACK

## Historial de versiones

| Versión | Fecha | Motivo del cambio |
|---|---|---|
| v1 | Guía 2 | Construcción inicial del MVP (`index-v1.html`) |
| **v2** | Guía 2.5 / 3 | Corrección de 3 empujones detectados en `auditoria-de-sesgos.md` (hallazgos E1, E3, E11). No se toca el motor de decisión, ni los umbrales, ni la hipótesis, ni el criterio |

---

## Qué cambia v2 respecto de v1

| # | Hallazgo auditado | Cambio aplicado |
|---|---|---|
| E1 | Los botones de escenario le decían al usuario qué conducta producir ("Acumulación de fatiga, **probar 🔴 override**", "predominio 🟡", "Jugador con protocolo activo 🔒") | Copy neutro y factual: "Escenario 1/2/3/4" + descripción del contexto, sin anticipar el resultado ni sugerir la acción |
| E3 | El acuerdo con el sistema no dejaba ningún registro (se inferría del silencio), mientras disentir costaba 5 pasos y una categoría obligatoria | Botón "✓ Aplico esta recomendación" por jugador, que loguea `apply_recommendation`. La categoría del override pasa a opcional. Acuerdo y desacuerdo cuestan 1 clic y ambos dejan dato |
| E11 | `localStorage` sin identificador: los logs de todos los participantes se mezclaban; `app_init` registraba "uso" con solo cargar la página | Campo de ID de participante + corte de log por sesión; cada fila del CSV lleva `participant_id` y `preset`; `app_init` pasa a `page_load` y se declara explícitamente que no cuenta como uso |
| — | Bug: `logAction('change_preset', ...)` se llamaba con 3 argumentos de 4, dejaba `details` en `undefined` y rompía la exportación del CSV | Corregido (llamada completa + `String(l.details \|\| '')` al exportar) |
| — | Los umbrales no están validados clínicamente (3 `[PENDIENTE]` en el código) y la interfaz los mostraba con autoridad | Se declara en el banner superior y en cada explicación del sistema: "Umbral no validado clínicamente. Es una sugerencia, no una indicación médica" |

**No cambia:** el motor `calculateRecommendation()`, los umbrales, el orden de prioridades, el candado del protocolo de conmoción, el plantel simulado, los filtros, el orden rojo → amarillo → verde, el banner de datos simulados.

---

## Prompt v2 completo

```text
Construí un MVP de una sola página, en un único archivo index.html (HTML + CSS + JS
embebidos, sin dependencias ni backend), mobile-first, en español rioplatense.

PRODUCTO: SPORTRACK — traduce datos de wearables/GPS en una recomendación semanal
por jugador, en lenguaje llano.

USUARIO: preparador físico de un club de rugby del URBA Top 12, el lunes a la mañana,
planificando la semana.

ACCIÓN CENTRAL: ver, para cada jugador, si entrena normal, baja carga, evita contacto
o descansa — y dejar registrada su decisión.

1. DATOS SIMULADOS
   - Plantel fijo de 10 jugadores con nombre, posición (Forward / Back) y subpuesto
     de rugby.
   - 4 escenarios precargados que cambian carga acumulada, nivel de contacto de las
     últimas 48 h y protocolo de conmoción.
   - Banner fijo arriba: "Datos simulados — Prototipo MVP · Umbrales de carga no
     validados clínicamente".
   - Los botones de escenario se llaman "Escenario 1/2/3/4" con una descripción
     puramente factual del contexto (ej.: "Lunes posterior a partido").
     PROHIBIDO: anticipar el resultado ("predominio amarillo") o sugerir la conducta
     esperada ("probar override", "mirá el candado"). La interfaz no le pide al
     usuario que produzca el evento que vamos a medir.

2. MOTOR DE DECISIÓN (sin cambios respecto de v1)
   Prioridad 1: protocolo de conmoción activo -> 🔴 "Sin contacto", protegido,
                no sobrescribible.
   Prioridad 2: carga Crítica -> 🔴 "Descanso".
   Prioridad 3: carga Alta con contacto Alto o Normal -> 🟡 "Bajar carga";
                contacto "Sin contacto" con carga Alta o Normal -> 🟡 "Sin contacto";
                Back con carga Alta -> 🟡 "Bajar carga".
   Prioridad 4: resto -> 🟢 "Entrena normal".
   Cada recomendación muestra una explicación en lenguaje llano, seguida siempre de:
   "Umbral no validado clínicamente. Es una sugerencia, no una indicación médica."
   Dejar los [PENDIENTE] de validación de umbrales visibles como comentarios en el
   código.

3. PANTALLAS
   - Dashboard con 4 contadores: plantel total, entrenan normal, bajan carga,
     restricción.
   - Filtros por estado y por posición.
   - Lista de jugadores ordenada rojo -> amarillo -> verde, con semáforo, carga en UA
     y la recomendación activa.
   - Detalle del jugador en modal: los 4 factores editables (posición, carga,
     contacto, conmoción), la recomendación del sistema con su explicación, y las
     dos acciones del usuario.

4. SIMETRÍA DE LAS DOS ACCIONES (cambio central de v2)
   El usuario tiene exactamente dos caminos y los dos cuestan un clic:
   a) "✓ Aplico esta recomendación" -> loguea apply_recommendation.
   b) "Sobrescribir decisión del sistema" -> elige la nueva recomendación, con
      categoría del cambio OPCIONAL y nota opcional -> loguea override.
   El acuerdo NO se infiere de la ausencia de override: si no hay registro, no hay
   acuerdo, hay silencio.
   Si cambian los factores de un jugador, se invalidan su acuerdo y su override
   previos (se loguea el reset).
   El rojo por protocolo de conmoción no admite ninguna de las dos acciones: muestra
   el candado y el motivo.

5. MEDICIÓN
   - Antes de empezar, el facilitador ingresa un ID de participante. Al iniciar la
     sesión se limpia el log anterior y se avisa si había una sesión abierta.
   - Cada evento guarda: timestamp, participant_id, escenario, player_id,
     player_name, acción y detalle, en localStorage.
   - Eventos: session_start, page_load, change_preset, view_detail, change_factor,
     apply_recommendation, override, reset_override, reset_agreement.
   - "page_load" se registra pero NO cuenta como uso: el uso se mide por
     view_detail, apply_recommendation y override.
   - Botón "Descargar Registro CSV" que exporta todas las columnas y nombra el
     archivo con el ID del participante.

6. ESTILO
   Tema oscuro (fondo #011528, superficie #0d2137, acento #B0DA00, secundario
   #00A3FF), tipografía Inter, semáforo verde/amarillo/rojo, targets de 44 px,
   mobile-first.

NO INCLUIR: login, backend, dashboard histórico de temporada, comparación entre
jugadores del mismo equipo, carga de video ni análisis por IA (todo eso está fuera
de alcance según la sección 6.2 del archivo del proyecto).
```

---

## Archivos

- `index.html` — MVP v2, el que se usa en la prueba de la Guía 3.
- `index-v1.html` — versión auditada, guardada como referencia para poder comparar.
