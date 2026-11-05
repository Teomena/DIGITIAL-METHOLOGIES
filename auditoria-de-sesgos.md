# Auditoría de sesgos — SPORTRACK

> Este archivo registra dónde nuestras decisiones pueden estar sesgadas
> y qué hacemos al respecto. No modifica la hipótesis ni el criterio.

**Equipo:** [Completar nombres]
**Fecha:** Noviembre 2026
**Insumos auditados:**
- `del-research-al-mvp.md` / `Desarrollo del MVP.docx` (secciones 1 a 8 + Anexos A-C)
- `desarrollo-del-mvp.md` (sección 6: MVP Canvas y clasificación de alcance)
- `mvp/index.html` — repo `Teomena/DIGITIAL-METHOLOGIES` (1214 líneas, revisado línea por línea)

---

## 1. Semáforo de evidencia

### 1.1 Clasificación pieza por pieza

| # | Evidencia (origen citado) | Color | Por qué |
|---|---|---|---|
| I1 | "El PF recibe métricas pero no sabe qué acción tomar" — §1.3 I1 | 🔴 Supusimos | El propio archivo la marca "Supuesto a validar". Viene de entrevista simulada (§1.8) |
| I2 | "La intuición no se abandona por miedo sino por confianza" — §1.3 I2 | 🔴 Supusimos | Entrevista simulada. Nadie lo dijo ni lo hizo |
| I3 | "La conmoción es el driver #1 de adopción" — §1.3 I3 | 🟡 Dijo (parcial) | La presión regulatoria World Rugby/UAR es verificable (dato público), pero que sea el driver #1 de adopción es supuesto |
| I4 | "En rugby la decisión es con contacto o sin contacto" — §1.3 I4 | 🟡 Dijo | Es conocimiento de dominio razonable, pero no hay registro de un PF tomándola |
| I5 | "Forwards y backs se miden con los mismos criterios" — §1.3 I5 | 🔴 Supusimos | Es la parte "se miden igual" la que no tiene registro. Que tengan demandas distintas es literatura, no nuestro research |
| I6 | "Video a las 2 AM, notas en cuaderno, sin registro" — §1.3 I6 | 🔴 Supusimos | Suena a conducta observada (verde) pero sale de entrevista simulada. **Es el amarillo-que-parecía-verde más peligroso del archivo** |
| I7 | "La IA genera curiosidad y desconfianza" — §1.3 I7 | 🔴 Supusimos | Entrevista simulada |
| I8 | "El que paga necesita argumentos distintos al que usa" — §1.3 I8 | 🟡 Dijo | Patrón de compra B2B documentado, no evidencia nuestra |
| I9 | "Los padres son stakeholders ocultos" — §1.3 I9 | 🔴 Supusimos | Entrevista simulada |
| I10 | "La barrera no es el precio, es la complejidad" — §1.3 I10 | 🔴 Supusimos | Entrevista simulada |
| I11 | "El jugador que quiere mejorar está solo" — §1.3 I11 | 🔴 Supusimos | Entrevista simulada |
| M1 | Wearables USD 93.810M → 120.050M, CAGR 4,13% — §1.4 | 🟢 Hizo (dato duro) | Desk research verificable. **Pero es conducta de mercado, no de nuestro usuario** |
| M2 | Kit Catapult/STATSports +USD 50.000 + 10-30k anuales — §1.4 | 🟢 Hizo (dato duro) | Precio público verificable |
| M3 | Wyscout Copper €299 / Mercury €399 — §1.4 | 🟢 Hizo (dato duro) | Precio público verificable |
| M4 | Sony compró STATSports; Catapult compró Impect (oct 2025) — §1.4 | 🟢 Hizo (dato duro) | Hecho público |
| M5 | Mapa competitivo: nadie traduce dato → decisión — §1.5 | 🟡 Dijo | Es nuestra **lectura** del feature set de los competidores, no un test de sus productos. Es la evidencia que §4.3 declara "la más fuerte" y en realidad es una interpretación |
| C1 | "Staff reducido: 1 PF, 1 coach, con suerte 1 analista" — §1.2 | 🔴 Supusimos | Caracterización de contexto sin fuente citada |
| C2 | "No conocemos el willingness to pay real" — §1.6 | ✅ Honesto | Supuesto ya declarado por el equipo |
| C3 | "No sabemos qué % de clubes URBA tiene dispositivos" — §1.6 | ✅ Honesto | Supuesto ya declarado. Es el que puede voltear toda la Pata A (§4.3) |

### 1.2 Conteo

Sobre 20 piezas de evidencia clasificadas:

- **Verde (hizo): 20 %** (4 piezas: M1, M2, M3, M4 — todas de mercado, **ninguna de conducta de usuario**)
- **Amarillo (dijo): 20 %** (4 piezas: I3, I4, I8, M5)
- **Rojo (supusimos): 60 %** (12 piezas: I1, I2, I5, I6, I7, I9, I10, I11, C1 + 3 supuestos abiertos declarados)

**Conducta de usuario observada: 0 %.** No existe una sola línea en el archivo en la que un preparador físico real haya *hecho* algo frente a nosotros.

### 1.3 Nuestra decisión más apoyada en amarillo o rojo

**La elección de la Pata A ("El Traductor") como núcleo del producto.** §4.3 dice que la evidencia más fuerte es "el vacío de mercado", que acabamos de clasificar como M5 → 🟡 (nuestra lectura, no un test). Y las 6 evidencias que §3 lista como respaldo de la Alternativa A (I1, I2, I4, I5, I8, I10) son 4 rojas y 2 amarillas.

Dicho sin anestesia: **construimos un motor de reglas de carga sobre cero conducta observada.** Lo único verde que tenemos justifica que hay un mercado, no que este PF tenga este problema.

Segundo lugar: los **umbrales del semáforo** (`index.html` líneas 672-677 y 741-790). El código mismo lo admite con tres `[PENDIENTE]` en `calculateRecommendation()` (líneas 737-739), pero la interfaz los muestra con autoridad clínica.

---

## 2. Sesgos del equipo

### 2.1 Confirmación — evidencia en contra que está en el research y NO aparece en la sección 4

Encontramos cuatro. Ninguna está discutida en §4.2 ni en §4.3:

1. **I10 contra la Pata B.** I10 dice que la barrera principal es la complejidad, no el precio, porque no tienen staff para operar software complejo. Elegimos A **+ B**: le sumamos al producto una capa de análisis de video con IA. §4.2 discute si la B nos gusta demasiado, pero nunca la confronta con I10. Si la barrera es la complejidad, la Pata B es la decisión más contraria a nuestra propia evidencia.
2. **I3 + I9 contra el núcleo elegido.** El research dice que el driver #1 de adopción es la conmoción y que los padres empujan por ahí. En §6.2 el registro de conmociones quedó clasificado como **"Simulable"**, es decir, afuera del desarrollo. Degradamos el driver que nuestro propio research puso primero y pusimos en el centro la traducción de carga, que viene de I1 (rojo). §4.2 menciona "una versión minimalista de C" como alternativa posible, pero la trata como una curiosidad, no como evidencia en contra.
3. **C1 + I1 contra la frecuencia de uso.** §1.2 dice staff reducido, el PF cubre varias categorías, y I1 dice que hoy el dato "se mira, no se usa". El supuesto "que el coach use la herramienta al menos 1 vez por semana" (§4.2) está listado como requisito, pero no como riesgo: tenemos evidencia de que hoy no lo hace.
4. **Dependencia de hardware.** La tabla comparativa de §3 castiga a la Alternativa C con "Dependencia de hardware: Alta (necesita todo)" y le da a A "Alta (necesita wearable)". Es el mismo problema con distinto texto. C3 (§1.6) dice que no sabemos cuántos clubes tienen dispositivos. Elegimos igual la opción hardware-dependiente.

### 2.2 Efecto IKEA — ¿descartaríamos igual la alternativa?

**No. Si otro equipo nos presentara la "C minimalista" (solo registro de conmociones con protocolo return-to-play), no la descartaríamos.** Y hay dos razones que nos incomodan:

- Descartamos la C por una corrección docente ("eso no es el problema de fondo", §1.1 nota y §3 riesgo de C), no por evidencia nuestra. Eso no es efecto IKEA, es **sesgo de autoridad**: cambiamos la decisión de producto por la opinión de quien nos evalúa.
- Nuestro propio archivo nos contradice dos veces: §4.2 dice que una C minimalista "podría ser un MVP más simple con adopción más rápida por presión regulatoria", y el MVP construido **ya tiene la conmoción como regla de prioridad 1** (`index.html` línea 742: es la primera condición del motor, y la única recomendación que no se puede sobrescribir, línea 1066). Es decir: el equipo dijo que la conmoción estaba fuera del núcleo y después la programó como lo más importante del producto.

Efecto IKEA puro sí aparece en la Pata B: §4.2 lo confiesa textualmente ("la Pata B nos atrae más... No enamorarse de la B") y la mantuvimos de todos modos. Lo escribimos y no actuamos en consecuencia. Declarar un sesgo no lo corrige.

### 2.3 Brecha decir-hacer — la señal de la hipótesis

**La señal es una opinión, no una conducta. Las dos.**

- Hipótesis principal (§5): "6 de 10 cuerpos técnicos... **reportan haber cambiado** al menos 1 decisión semanal". *Reportan* = autorreporte retrospectivo. Mide memoria y cortesía, no conducta.
- Hipótesis secundaria (§5): "7 de 10 jugadores... **declaran haber trabajado** en al menos 1 aspecto". *Declaran* = lo mismo, con el agravante de deseabilidad social frente al coach.

No cambiamos el criterio (regla de la guía). Lo que hacemos es registrarlo como la limitación central del diseño de medición y **triangularlo** con conducta registrada en el protocolo de la Guía 3 (ver §4 y §5): planificación escrita antes de abrir el MVP, divergencia jugador por jugador, y log CSV.

---

## 3. Arquitectura de decisión del MVP

Recorrimos `index.html` en el orden del flujo real: banner → escenarios → dashboard → filtros → lista → modal → override → cierre.

| # | Elemento del MVP | Sesgo que activa | ¿A favor de quién? | ¿Infla la medición de la hipótesis? | Decisión |
|---|---|---|---|---|---|
| E1 | Copy de los botones de escenario: "probar 🔴 override" (L595), "predominio 🟡" (L599), "Jugador con protocolo activo 🔒" (L602) | Características de demanda / efecto experimentador. La interfaz le dice al usuario qué tiene que hacer | **Nuestra métrica** | **Sí, de forma directa.** El evento `override` (L892) es nuestra prueba de "cambió una decisión". Un botón que literalmente dice "probar override" fabrica ese evento | **Sale** (v2 del prompt). Es el hallazgo más grave de la auditoría |
| E2 | `preset1 "Semana Normal"` activo por default (L589) con 7 verdes | Default + ancla. La primera foto del plantel es "casi todo bien" | Nuestra métrica | **Sí.** Si la primera pantalla coincide con lo que el PF ya pensaba, sube el "la recomendación coincidió con lo que decidió" (§6.1) sin que el sistema haya aportado nada | **Se declara.** Para la prueba usamos un escenario asignado y rotado, registrado en el protocolo |
| E3 | Fricción asimétrica del acuerdo vs. el desacuerdo: aceptar = 0 clics; disentir = abrir modal (L975) + abrir acordeón (L1070) + elegir recomendación + **categoría obligatoria** (L1086, validada en L1117) + confirmar | Statu quo + costo de disentir. Y lo inverso: el silencio se cuenta como acuerdo | Nuestra métrica | **Sí, en los dos sentidos.** Deprime los overrides (sub-registra el desacuerdo) e infla el acuerdo, porque **no existe ningún evento que registre "sigo la recomendación"**. Acuerdo = ausencia de dato | **Sale parcialmente** (v2: botón explícito "Aplico esta recomendación" + categoría opcional). Lo demás se declara |
| E4 | Lenguaje de autoridad clínica en las explicaciones: "Se recomienda descanso para evitar lesiones musculares" (L754), "PROTEGIDO" (L744) | Sesgo de autoridad + aversión a la pérdida (lesión) | Usuario (seguridad) y **nuestra métrica** | **Sí.** Con un tester no experto (compañero, amigo) la obediencia es casi total. Con un PF real de URBA puede pasar lo contrario: detecta el umbral inventado y pierde confianza | **Queda, se declara.** El tono protector es parte del valor, pero los umbrales se marcan como no validados en pantalla y en el consentimiento |
| E5 | Umbrales y anclas numéricas: `LOAD_UA_MAP` ">750 UA" (L672-677) y el tope ">750 UA" repetido en la explicación de rojo (L754). El motor tiene tres `[PENDIENTE]` admitiendo que no están validados (L737-739) | Anclaje + precisión falsa. Un número exacto se lee como ciencia | Nuestra métrica (credibilidad) | **Sí, indirectamente.** El PF puede estar validando "el número suena razonable", no "la recomendación me sirvió" | **Queda, se declara** como limitación clínica explícita en el informe de la Guía 3 |
| E6 | Orden forzado rojo → amarillo → verde (L945-946) + stat cards del dashboard (L917-929) como primer dato visible | Ancla + encuadre de severidad. Lo primero que se ve son los problemas y los contadores | Usuario (triage útil) | Parcialmente. Dirige la atención a los casos que más probablemente generen una "decisión cambiada" | **Queda** porque ayuda al usuario (el PF necesita triage el lunes) **y lo declaramos** |
| E7 | Datos simulados: plantel de 10 jugadores con nombres y puestos reales (L655-666) y 4 presets completos (L679-730) | Prueba social / realismo falso | Neutro, mitigado | No, mientras el banner se vea | **Queda.** Mitigado por el banner "⚡ Datos simulados — Prototipo MVP" (L574), que está fijo arriba. Fue una buena decisión de la Guía 2, la confirmamos |
| E8 | Candado del protocolo de conmoción: rojo no sobrescribible (L742-748, L1066-1068) | Pérdida de agencia + efecto halo. Es lo más impresionante del MVP | Usuario (seguridad) | **Sí, por halo.** El "wow" del candado puede derramarse sobre la recomendación de carga, que es lo que la hipótesis mide. Y contradice a I7 ("el coach quiere poder revisar/editar") | **Queda, se declara.** No se toca por seguridad; en el informe se separa qué valoró el usuario: el candado o la traducción de carga |
| E9 | Opciones del override: solo 4 (L1079-1084), sin "🔴 Sin contacto"; y la posición se reduce a Forward/Back (L1048-1051) pese a que el roster tiene subpuestos (L655-666) | Elección forzada. El menú define el vocabulario de decisión del PF | Nuestra métrica | **Sí.** Si la decisión real del PF no está en la lista, elige la más parecida y la contamos como coincidencia. Además I5 (umbrales por puesto) queda sin poder expresarse | **Se declara** en v2 como pendiente; en la prueba se pregunta en voz alta qué decisión habría tomado si pudiera escribirla libre |
| E10 | `changePreset()` borra todos los overrides (L837) | Pérdida de evidencia | Nadie | **Sí, al revés: desinfla y ensucia.** Un cambio de escenario borra las decisiones previas y deja el log sin contexto | **Se declara.** En el protocolo: un escenario por participante, sin cambiar de preset durante la sesión |
| E11 | `localStorage` sin identificador de participante ni corte de sesión (L1136-1143) + `logAction('app_init')` en cada carga (L1209) | Contaminación de la medición | Nuestra métrica | **Sí.** Si probamos con varios PF en el mismo celular, los logs se mezclan y una sola persona entusiasta puede parecer varias. Y "abrió la app" (§6.1) se registra con solo cargar la página, incluso si el usuario no mira nada | **Sale** (v2: campo de ID de participante + reset de log por sesión) |
| E12 | Pantalla final: no hay. Después del override se cierra el modal y se vuelve a la lista (L894-895). El único cierre posible es `alert("No hay registros para descargar.")` (L1151) | Ausencia de pico-final. El usuario no se lleva nada | Nadie | No la infla, pero **la deja ciega**: no hay momento en el que el usuario diga qué se lleva, y no hay cierre que registre valor percibido | **Se declara.** Lo cubre el protocolo de la Guía 3 con la pregunta de cierre, no con una pantalla |

### 3.1 Empujón que más puede inflar la métrica

**E1 + E3 juntos, y en ese orden.**

La hipótesis principal se valida si el PF *cambió una decisión gracias a la recomendación*. El MVP tiene un botón de escenario que dice **"probar 🔴 override"** y un único evento que registra desacuerdo, que es justamente el `override`. Es decir: **la interfaz pide explícitamente que se produzca el evento que nosotros vamos a contar como prueba de valor.** Si lo dejamos así, no medimos la hipótesis: medimos obediencia a una instrucción escrita en un botón.

Y el complemento es peor que el empujón: cuando el PF **está de acuerdo**, el MVP no registra nada. El acuerdo se infiere del silencio, que es exactamente lo que también produce alguien que no entendió, que no quiso contradecir al sistema o que se aburrió.

### 3.2 Qué decidimos hacer con él

1. **Sacar el copy instructivo** de los cuatro botones de escenario (E1). Son nombres neutros, sin indicar qué conducta se espera. → v2 del prompt.
2. **Agregar el evento faltante**: botón explícito "Aplico esta recomendación" por jugador, que registra el acuerdo como dato positivo y no como ausencia (E3). Así el acuerdo y el desacuerdo tienen el mismo costo y los dos dejan rastro. → v2 del prompt.
3. **Agregar ID de participante** y corte de log por sesión (E11). → v2 del prompt.
4. **Capturar la línea de base antes de abrir el MVP** (cambio de protocolo, no de MVP): el PF escribe su decisión para los 10 jugadores en papel; después abre la app; recién entonces se cuenta la divergencia jugador por jugador. Sin línea de base no existe "cambió una decisión", solo existe "dijo que cambió".
5. Todo lo demás de la tabla queda y se declara en el informe.

---

## 4. Pre-mortem

> Pasaron dos semanas. La prueba dio positivo: 6 de 10 cuerpos técnicos reportaron haber cambiado al menos una decisión. Y era mentira.

### Causas posibles de un falso positivo

Agrupadas por dónde está el problema:

**A — Está en con quién probamos**

1. **Probamos con compañeros, amigos y jugadores, no con PF de URBA Top 12.** Un compañero de cursada no tiene una decisión previa que cambiar: no planificaba nada el lunes. Le mostramos el semáforo, le parece razonable y nos dice que sí "cambiaría" algo. El 6 de 10 se cumple sin un solo usuario del segmento definido en §1.2.
2. **Sesgo de selección del club.** Llegamos por contacto personal a los clubes que ya tienen GPS y son los más tecnófilos. C3 (§1.6) dice que no sabemos qué porcentaje del universo tiene dispositivos: validamos la app con el 10 % del mercado que no representa al 90 %.
3. **Deseabilidad social.** Es el proyecto de la facultad de un conocido. Nadie le dice "no me sirve" a alguien que le pide una devolución cara a cara. El entusiasmo se registra como cambio de decisión.

**B — Está en el propio MVP**

4. **El botón "probar 🔴 override" (E1) hizo el trabajo.** El usuario hizo el override porque la pantalla se lo pidió, y nosotros lo leímos como "cambió una decisión gracias a la recomendación".
5. **El preset "Semana Normal" por default (E2) coincidió con la intuición del PF.** El PF ya pensaba que el plantel estaba bien, el semáforo mostró 7 verdes y confirmó. "La recomendación coincidió con lo que decidió" (§6.1) marca positivo, y el sistema no aportó ninguna información nueva: solo le devolvió su propia intuición.
6. **El efecto halo del candado de conmoción (E8).** Lo que el PF valoró fue el protocolo return-to-play (driver I3), no la traducción de carga. Validamos la Pata A con el entusiasmo que generó un módulo clasificado como "Simulable" en §6.2.
7. **La autoridad clínica de los textos (E4/E5).** El usuario aceptó "carga crítica >750 UA" como si fuera un umbral validado. El código dice `[PENDIENTE]` tres veces (L737-739). Validamos la estética de la precisión, no la utilidad de la decisión.
8. **No hay línea de base (E3/E12).** Sin la decisión previa escrita, "cambié una decisión" es un recuerdo construido después de ver la pantalla (sesgo retrospectivo). Es literalmente imposible que esta prueba dé negativo.

**C — Está en cómo leemos los resultados nosotros**

9. **Traducimos "me parece útil" a "cambié una decisión".** Al codificar las respuestas, cualquier comentario positivo entra en la columna del criterio. Es el sesgo de confirmación de §2.1 aplicado al análisis de datos.
10. **Contamos mal el log.** `localStorage` sin ID de participante (E11) mezcla sesiones, y `app_init` se dispara con solo cargar la página. Diez aperturas de un mismo participante parecen diez usuarios activos.
11. **Ignoramos el denominador.** Probamos con 18 personas, 6 dijeron que sí, y reportamos "6 de 10". El criterio es 6 **de 10**, no 6 en total.
12. **Nos quedamos con la Pata A porque ya la construimos.** Si la prueba muestra que el valor estaba en la conmoción, el efecto IKEA de §2.2 nos va a hacer escribir "se validó la traducción de carga" igual.

### Preguntas reescritas para la prueba

De intención futura → conducta pasada. Las tres obligatorias, más dos que agregamos.

| # | Pregunta sesgada (versión original) | Pregunta corregida |
|---|---|---|
| 1 | ¿Usarías esta app todos los lunes para planificar? | **Contame el último lunes de temporada: ¿qué abriste primero, qué miraste y a qué hora quedó cerrada la planificación de la semana?** (Pedir que muestre la planilla o el cuaderno en pantalla) |
| 2 | ¿Te parece útil la recomendación del semáforo? | **Antes de que te muestre nada: escribí acá, para estos 10 jugadores, qué harías esta semana con cada uno.** Después de usar el MVP: **¿en cuáles tu decisión escrita y la pantalla no coinciden, y en cuáles vas a cambiar lo que escribiste?** |
| 3 | ¿Cambiarías una decisión basándote en esto? | **En los últimos tres partidos, ¿hubo algún jugador al que hiciste entrenar o jugar y después te arrepentiste? ¿Qué viste que te hizo arrepentirte?** |
| 4 | ¿Confiarías en una recomendación automática? | **La última vez que un dato del GPS o del reloj contradijo lo que veías en la cancha, ¿qué hiciste? ¿A quién le avisaste?** |
| 5 | ¿Te gusta el diseño / te resultó claro? | **¿En qué momento te frenaste, releíste algo dos veces o buscaste algo que no estaba?** |

Las preguntas 1, 2 y 3 son las tres obligatorias de la guía. La 2 es además el mecanismo de línea de base: sin ella el criterio de la §5 no es medible.

---

## 5. Cambios

### Cambios al MVP (versión del prompt)

Archivo: `mvp/prompt-v2.md`. Tres cambios, ninguno toca el motor de decisión ni los umbrales:

1. **Copy neutro en los botones de escenario.** Se eliminan "probar 🔴 override", "predominio 🟡" y "Jugador con protocolo activo 🔒". Los escenarios pasan a llamarse "Escenario 1/2/3/4" con una descripción puramente factual. (Corrige E1)
2. **Evento de acuerdo explícito.** Botón "✓ Aplico esta recomendación" en el detalle de cada jugador, que loguea `apply_recommendation`. El acuerdo deja de medirse por ausencia de dato, y el costo de acordar y de disentir se iguala. La categoría del override pasa de obligatoria a opcional. (Corrige E3)
3. **ID de participante y corte de log por sesión.** Campo al inicio de la sesión; el log se etiqueta con ese ID y se exporta/limpia por participante. (Corrige E11)

No se modificó nada durante la auditoría: los tres cambios están especificados en el prompt v2 y aplicados en `mvp/index.html` (v2), con `mvp/index-v1.html` guardado como referencia de lo auditado.

### Cambios al protocolo de prueba

Archivo: `guion-de-prueba.md`.

1. **Línea de base ciega obligatoria.** El participante escribe su decisión para los 10 jugadores **antes** de ver el MVP. La divergencia se cuenta jugador por jugador, no por autorreporte.
2. **Un escenario asignado y rotado por participante**, elegido por nosotros antes de empezar, sin cambiar de preset durante la sesión (neutraliza E2 y E10).
3. **Reclutamiento acotado y declarado:** solo PF, head coaches o analistas de clubes con al menos un dispositivo de medición. Cada participante que no cumpla el perfil se registra aparte y **no cuenta** para el 6 de 10.
4. **Guion sin preguntas de intención futura.** Las cinco reescrituras de §4 son obligatorias; el facilitador no sugiere acciones ("probá el override", "fijate el candado").
5. **Codificación a ciegas y a dos manos.** Dos integrantes clasifican por separado cada sesión como cumple / no cumple el criterio, con la regla escrita de antemano: "cambió una decisión" = divergencia registrada entre la línea de base escrita y la decisión final, no comentario positivo. Los desacuerdos se resuelven mirando el CSV.
6. **Denominador explícito:** 10 cuerpos técnicos del perfil. Se reporta sobre 10, no sobre el total de personas contactadas.
7. **Separar el halo de la conmoción:** la pregunta de cierre pide elegir y justificar qué parte del MVP valoró más, para poder atribuir el resultado a la Pata A o al módulo de conmoción.

### Limitaciones que declaramos

1. **Conducta de usuario observada: 0 %.** El 100 % de la evidencia cualitativa (I1-I11) sale de entrevistas simuladas. La encuesta cuantitativa está diseñada y no se distribuyó (§1.8).
2. **La evidencia "más fuerte" es una interpretación.** El "vacío de mercado" (§4.3) es nuestra lectura del feature set de los competidores (M5 → 🟡), no un test de sus productos.
3. **La señal de las dos hipótesis es autorreporte** ("reportan", "declaran"). No cambiamos el criterio; lo triangulamos con línea de base y log CSV.
4. **Los umbrales del motor no están validados clínicamente.** `calculateRecommendation()` lo admite con tres `[PENDIENTE]` (L737-739) y la interfaz los muestra igual, con autoridad. Se declara en pantalla, en el consentimiento y en el informe.
5. **El motor reduce la posición a Forward/Back** (E9), con lo cual I5 (umbrales por puesto) queda validado solo de forma gruesa.
6. **El protocolo de conmoción es Simulable** (§6.2) y es, al mismo tiempo, la regla de prioridad 1 del MVP y la única no sobrescribible (E8). Si el valor percibido se concentra ahí, la hipótesis principal no quedó validada aunque el criterio dé positivo.
7. **Sesgo de autoridad en la elección de solución.** Descartamos la Alternativa C por una corrección docente, no por evidencia propia (§2.2).
8. **Pata B sin auditar en el MVP.** El `index.html` solo implementa la Pata A. La hipótesis secundaria (informe por IA para el jugador) no tiene prototipo y no se prueba en la Guía 3.
9. **La Pata B contradice a I10** (complejidad como barrera principal) y mantenemos la decisión (§2.1).

### Lo que NO cambiamos

**La hipótesis de valor y el criterio quedan exactamente como están en §5 del archivo de la Guía 1/2:**

> Creemos que una app que traduzca los datos de wearables/GPS en recomendaciones semanales en lenguaje llano ayudará a cuerpos técnicos de clubes de rugby del URBA Top 12 a tomar decisiones de carga y alineación con respaldo en vez de por intuición.
> Lo sabremos si **al menos 6 de 10** cuerpos técnicos que prueben el MVP durante 4 semanas reportan haber cambiado al menos 1 decisión semanal gracias a la recomendación de la herramienta.

Tampoco cambiamos el usuario, la situación, el valor ni la acción central del MVP Canvas (§6.1), ni la clasificación de alcance (§6.2).

---

## Cierre — nuestro hallazgo más incómodo, en una línea

**Nuestro MVP tiene un botón que dice "probar override" y el override es exactamente el evento que íbamos a contar como prueba de que la herramienta funciona: le pedíamos al usuario que produjera nuestro resultado positivo.**

Segundo, casi empatado: cuando el PF está de acuerdo con el sistema, el MVP no registra nada, así que el acuerdo —la mitad de nuestra medición— se infiere del silencio.

---

## Anexo — Uso de IA en esta auditoría

| Qué hizo la IA | Qué decidió el equipo |
|---|---|
| Clasificó las 20 piezas de evidencia citando sección de origen | Revisamos cada color. Discutimos I3, I4, I8 y M5 (quedaron amarillas, no verdes) y aceptamos que I6 era rojo pese a sonar a conducta observada |
| Listó 12 empujones del `index.html` con número de línea | Verificamos las líneas en el repo. Decidimos nosotros queda / sale / se declara en las 12 filas |
| Señaló 4 evidencias en contra ausentes de §4 | Las aceptamos todas. La de I10 vs. Pata B es la que más nos costó |
| Marcó que la señal de las dos hipótesis es autorreporte | Confirmamos. **No cambiamos el criterio**: agregamos triangulación en el protocolo |
| Propuso reescrituras de las preguntas | Elegimos 5 y las adaptamos al vocabulario de rugby (contacto, forwards/backs, lunes de planificación) |

La IA no modificó el código durante la auditoría, no reescribió la hipótesis ni el criterio, y no decidió qué empujones quedaban.
