# Texto para pegar en el mural — Guía 2.5 / 3 · SPORTRACK

Cada bloque de abajo es una tarjeta del mural. Copiá y pegá el texto tal cual.
El detalle completo está en los 3 PDF adjuntos.

---

## TÍTULO DEL MURAL

**SPORTRACK — Auditoría de sesgos del MVP**
Equipo: [Completar nombres] · Noviembre 2026
Hipótesis y criterio: sin cambios. Lo que cambió es el MVP y cómo medimos.

---

## 1. SEMÁFORO DE EVIDENCIA

**19 piezas clasificadas**

- 🟢 Verde (hicimos / conducta observada): **21 %** — 4 piezas, todas datos de mercado
- 🟡 Amarillo (nos dijeron): **21 %** — 4 piezas
- 🔴 Rojo (supusimos): **58 %** — 11 piezas

**Conducta de usuario observada: 0 %.**
Las 11 evidencias de usuario (I1-I11) salen de entrevistas simuladas —
método habilitado por la consigna, no un atajo. La limitación no es cómo
las obtuvimos, sino hasta dónde llegan: no alcanzan para afirmar conducta.

**El rojo no es todo igual:** separamos supuesto informado (I5, I6, I9),
supuesto de mecanismo (I1, I2, I7, I10), supuesto sin fuente (C1, I11) y
supuesto ya declarado por el equipo (C2, C3). Cada grupo cuesta distinto validar.

**Decisión con menos respaldo:** elegir la Pata A ("El Traductor") como núcleo del producto.

---

## 2. SESGOS DEL EQUIPO

🔴 **Confirmación** — 4 evidencias en contra que no estaban en el archivo:
1. I10 dice que la complejidad es la barrera principal, y la Pata B (IA) agrega complejidad.
2. I3 + I9: la conmoción es el driver más mencionado, y la clasificamos como "Simulable".
3. C1 + I1 contradicen el supuesto de uso semanal sostenido.
4. Doble estándar con la dependencia de hardware: barrera para el competidor, requisito para nosotros.

🔴 **Efecto IKEA** — No descartaríamos la Alternativa C ni con evidencia mínima en contra. Y la descartamos por una corrección docente, no por evidencia propia → **sesgo de autoridad**.

🔴 **Brecha decir-hacer** — Las dos hipótesis se miden con "reportan" / "declaran". Es autorreporte, no conducta.

---

## 3. ARQUITECTURA DE DECISIÓN DEL MVP

**12 empujones detectados en `index.html`, con número de línea.**

🚨 **El peor (E1):** el botón de escenario decía literalmente *"Acumulación de fatiga, probar 🔴 override"*.
El override es **exactamente el evento que íbamos a contar como prueba de valor**.
Le pedíamos al usuario que produjera nuestro resultado positivo.

🚨 **Casi empatado (E3):** cuando el PF está de acuerdo, el MVP **no registra nada**.
Disentir costaba 5 pasos + categoría obligatoria. Estar de acuerdo costaba 0 y no dejaba dato.
La mitad de nuestra medición se infería del silencio.

**E11:** `localStorage` sin ID de participante → los logs de todos se mezclaban.

Decisión por empujón: **queda / sale / se declara** (tabla completa en el PDF 1).

---

## 4. PRE-MORTEM — 12 causas de falso positivo

**A. Con quién probamos**
Probamos con conocidos del club · sin perfil excluyente · sin denominador fijo

**B. El MVP mismo**
El botón sugiere la conducta que medimos · el acuerdo no deja registro · los umbrales se muestran con autoridad aunque no estén validados · el candado de conmoción genera efecto halo

**C. Cómo leemos los resultados**
Sin línea de base, "cambió una decisión" es un recuerdo construido después de ver la pantalla · confundir entusiasmo con cambio de conducta · codificar de a uno y discutiendo

---

## 5. QUÉ CAMBIAMOS

**En el MVP (prompt v2 → `index.html`):**
1. Copy neutro en los escenarios: "Escenario 1 · Lunes posterior a partido". Prohibido anticipar el resultado o sugerir la acción.
2. Botón "✓ Aplico esta recomendación" → el acuerdo deja registro y cuesta 1 clic, igual que el override. Categoría del override pasa a opcional.
3. ID de participante + corte de log por sesión. `app_init` → `page_load`, declarado como "no cuenta como uso".

**En el protocolo de prueba:**
Perfil excluyente · **línea de base ciega antes de abrir la app** · escenario asignado y rotado · facilitador en silencio · preguntas en pasado · denominador explícito "X de 10" · doble codificación a ciegas.

**9 limitaciones declaradas**, entre ellas: conducta de usuario observada 0 %, umbrales no validados clínicamente, y que el valor podría concentrarse en el módulo de conmoción (que es "Simulable"), no en la hipótesis principal.

---

## LO QUE NO CAMBIAMOS

> Creemos que una app que traduzca los datos de wearables/GPS en recomendaciones semanales en lenguaje llano ayudará a cuerpos técnicos de clubes de rugby del URBA Top 12 a tomar decisiones de carga y alineación con respaldo en vez de por intuición.
> Lo sabremos si **al menos 6 de 10** cuerpos técnicos que prueben el MVP durante 4 semanas reportan haber cambiado al menos 1 decisión semanal gracias a la recomendación.

Hipótesis, criterio, usuario, situación, valor y acción central: **intactos.**

---

## CIERRE — HALLAZGO MÁS INCÓMODO (1 línea)

**Nuestro MVP tenía un botón que decía "probar override", y el override es exactamente el evento que íbamos a contar como prueba de que la herramienta funciona: le pedíamos al usuario que produjera nuestro resultado positivo.**

---

## ANEXO — USO DE IA

La IA clasificó la evidencia, listó los 12 empujones con línea, señaló las evidencias en contra y propuso reescrituras de preguntas.
El equipo verificó cada línea en el repo y decidió queda/sale/se declara en las 12 filas.
**La IA no modificó el código durante la auditoría, ni reescribió la hipótesis ni el criterio.**
