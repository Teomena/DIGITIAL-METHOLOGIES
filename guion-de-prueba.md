# Guion de prueba — SPORTRACK (Guía 3)

> Corregido después de la auditoría de sesgos. Cambia el protocolo, no la hipótesis ni el criterio.
> Criterio sin cambios: **al menos 6 de 10 cuerpos técnicos reportan haber cambiado al menos 1 decisión semanal gracias a la recomendación.**

---

## Perfil del participante (excluyente)

- PF, head coach o analista de un club de rugby del URBA Top 12 o de fútbol formativo / liga de desarrollo.
- El club tiene **al menos un dispositivo de medición** (GPS, reloj, WHOOP) o planilla de carga.
- Toma decisiones de carga o alineación en la semana.

**Denominador:** 10 participantes de este perfil. Quien no cumpla el perfil se registra en una planilla aparte y **no cuenta** para el 6 de 10.

---

## Materiales

- `mvp/index.html` (v2) abierto en el celular del participante o en el nuestro.
- Hoja de **línea de base** impresa: 10 jugadores, una columna en blanco.
- Planilla de registro de la sesión.
- Export CSV del log al terminar (un archivo por participante, con su ID).

---

## Estructura de la sesión (30 min)

| Bloque | Qué se hace | Min |
|---|---|---|
| 0 | Encuadre y consentimiento | 3 |
| 1 | Conducta pasada, **sin mostrar el MVP** | 8 |
| 2 | **Línea de base ciega** | 5 |
| 3 | Uso del MVP en silencio | 8 |
| 4 | Divergencia y cierre | 6 |

---

## Bloque 0 — Encuadre (3 min)

Leer tal cual:

> "Esto es un prototipo con **datos simulados**: los 10 jugadores son inventados y los umbrales de carga **no están validados clínicamente**. No es una herramienta médica. No estamos evaluando tu criterio: estamos probando si la pantalla sirve o no. Si no sirve, nos sirve más que si te gusta."

**Reglas del facilitador:**
- No sugerir acciones. Prohibido decir "probá el override", "fijate el candado", "mirá el semáforo".
- No explicar la pantalla. Si pregunta, responder: "¿qué esperarías que haga?".
- No preguntar nada en futuro condicional ("usarías", "te gustaría", "recomendarías").
- Escenario **asignado por nosotros antes de empezar** y rotado entre participantes. No cambiar de escenario durante la sesión (borra los overrides).

---

## Bloque 1 — Conducta pasada, antes de mostrar nada (8 min)

Las tres preguntas reescritas obligatorias son P1, P2 y P3. P4 y P5 las agregamos.

**P1 — Rutina real del lunes** *(reemplaza: "¿usarías esta app todos los lunes?")*
> Contame el último lunes de temporada: ¿qué abriste primero, qué miraste y a qué hora quedó cerrada la planificación de la semana?
> - Si puede, mostrame en pantalla la planilla, el cuaderno o el chat donde quedó.
> - ¿Quién más la vio antes de que empezara el entrenamiento?

*Registrar:* herramientas que efectivamente abrió, orden, minutos, si existe o no un registro escrito.

**P3 — Arrepentimiento concreto** *(reemplaza: "¿cambiarías una decisión basándote en esto?")*
> En los últimos tres partidos, ¿hubo algún jugador al que hiciste entrenar o jugar y después te arrepentiste?
> - ¿Qué viste que te hizo arrepentirte?
> - ¿En qué momento te diste cuenta: antes, durante o después?

*Registrar:* caso concreto o "no hubo". No aceptar generalidades ("siempre pasa").

**P4 — Dato contra observación** *(reemplaza: "¿confiarías en una recomendación automática?")*
> La última vez que un dato del GPS o del reloj contradijo lo que veías en la cancha, ¿qué hiciste? ¿A quién le avisaste?

*Registrar:* a quién le hizo caso, y si quedó algún registro de la decisión. Esta pregunta ataca el supuesto más riesgoso declarado en §5 del archivo del proyecto.

---

## Bloque 2 — Línea de base ciega (5 min)

**Sin haber mostrado el MVP.** Entregar la hoja con los 10 jugadores (nombre, puesto y los datos crudos del escenario asignado: carga en UA, nivel de contacto de las últimas 48 h, protocolo de conmoción sí/no).

**P2a — Decisión previa escrita** *(primera mitad del reemplazo de "¿te parece útil la recomendación?")*
> Antes de que te muestre nada: escribí acá, para cada uno de estos 10 jugadores, qué harías esta semana. Usá tus palabras.

Fotografiar la hoja antes de abrir la app. **Sin esta hoja la sesión no cuenta:** sin línea de base, "cambió una decisión" es un recuerdo construido después de ver la pantalla.

---

## Bloque 3 — Uso del MVP (8 min)

1. Ingresar el **ID de participante** (P01…P10) en la app.
2. Entregar el dispositivo y callarse. Cronometrar hasta la primera acción.
3. Consigna única: *"Es el lunes a la mañana y tenés que dejar definida la semana."*
4. Anotar sin intervenir: dónde se frena, qué toca primero, qué no toca nunca, si lee las explicaciones, si usa los filtros, si abre el override, si aplica recomendaciones.

---

## Bloque 4 — Divergencia y cierre (6 min)

**P2b — Divergencia jugador por jugador** *(segunda mitad del reemplazo)*
> Comparemos tu hoja con la pantalla. ¿En cuáles no coinciden?
> Para cada uno que no coincide: **¿vas a cambiar lo que escribiste o te quedás con tu decisión? ¿Por qué?**

*Registrar en la planilla:* por jugador → decisión escrita / recomendación del sistema / decisión final / cambió sí-no / motivo en palabras del participante.

**Esta tabla es la medición del criterio.** "Cambió una decisión" = al menos un jugador donde decisión final ≠ decisión escrita, con el motivo atribuido a la recomendación. No es un comentario positivo.

**P5 — Fricción real** *(reemplaza: "¿te gusta el diseño?")*
> ¿En qué momento te frenaste, releíste algo dos veces o buscaste algo que no estaba?

**P6 — Separar el halo de la conmoción** *(agregada por la auditoría, hallazgo E8)*
> De todo lo que viste, ¿qué parte usarías la semana que viene y qué parte no? ¿Por qué esa y no la otra?

*No ofrecer opciones.* Si menciona el protocolo de conmoción y no la traducción de carga, se registra así: el valor percibido está en un módulo clasificado como "Simulable", no en la hipótesis principal.

**P7 — Vocabulario propio** *(agregada por la auditoría, hallazgo E9)*
> Si pudieras escribir la indicación con tus palabras en vez de elegir de una lista, ¿qué le pondrías a este jugador?

**P8 — Cierre de conducta inmediata** *(reemplaza: "¿lo recomendarías?")*
> ¿A quién del club le mandarías esto ahora mismo? Mandáselo si querés.

*Registrar:* si lo manda o no. La conducta, no la intención.

---

## Al terminar cada sesión

1. Exportar el CSV del log con el ID del participante.
2. Limpiar el log antes del siguiente participante (si no, los logs se mezclan).
3. Fotografiar la hoja de línea de base y la planilla de divergencia.
4. Escribir en una línea el hallazgo más incómodo de **esa** sesión, antes de hablar con el resto del equipo.

---

## Codificación de resultados (regla escrita antes de medir)

| Campo | Regla |
|---|---|
| Cumple el criterio | ≥1 jugador con decisión final ≠ decisión escrita en la línea de base, con motivo atribuido por el participante a la recomendación |
| **No** cumple | Comentarios positivos, "me parece útil", "lo usaría", entusiasmo, o divergencia sin cambio de decisión |
| Nulo | Sin hoja de línea de base, o participante fuera de perfil, o facilitador que sugirió acciones |
| Denominador | 10 participantes de perfil. Se reporta "X de 10", nunca "X de los que probaron" |
| Doble codificación | Dos integrantes clasifican por separado y a ciegas; los desacuerdos se resuelven mirando el CSV, no discutiendo |

---

## Lo que no se toca

Hipótesis de valor, criterio (6 de 10), usuario, situación, valor y acción central del MVP Canvas: **sin cambios.** Lo que cambió es cómo medimos y con quién probamos.
