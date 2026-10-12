---
name: historia-usuario
description: Redacta historias de usuario y tareas para cualquier tipo de software (web, móvil, backend, APIs, embebido, hardware, datos, etc.) con una plantilla fija (título, historia, criterios de aceptación, fuera de alcance, dependencias, preguntas abiertas). Úsala siempre que el usuario pida redactar, aterrizar, refinar, dividir o convertir en historia de usuario una tarea, requerimiento, ticket o idea, aunque solo diga "redáctala como tarea", "ponla como historia" o "escríbeme los criterios de aceptación".
---

# Historias de usuario

Convierte requerimientos sueltos en historias de usuario claras, con criterios verificables y límites explícitos, sin importar el tipo de software.

## Flujo de trabajo

1. **Detecta el modo**:
   - Si el requerimiento ya es claro → redacta directamente con la plantilla.
   - Si es ambiguo o tiene incertidumbre → aterrízalo antes de redactar (paso 2).
2. **Aterrizar (una pregunta por turno)**. Pregunta solo lo que cambia el alcance. Prioriza:
   - ¿Qué pasa hoy? (situación actual y problema real)
   - ¿Quién se beneficia o es el actor? (usuario final, operador, administrador, otro sistema, equipo interno)
   - ¿Cuándo se dispara y cuándo termina?
   - ¿Qué pasa si falla o se queda trabado?
   Separa siempre el **problema real** de la **solución propuesta**: la solución es un medio.
3. **Redacta** con `assets/plantilla-historia.md`.
4. **Cierra huecos**: al final señala máximo 2 huecos o preguntas abiertas relevantes.

## Reglas de redacción

- **Título**: verbo en infinitivo, específico, usable como título de ticket.
- **Historia**: "Como [rol], quiero [capacidad], para [valor]". El "para" explica el problema que se evita o el valor que se obtiene, no repite el "quiero".
- **Criterios de aceptación**: numerados, observables y verificables. Cubre: disparador, resultado, caso negativo (cancelación o fallo) y estado final. Una condición por criterio; usa sub-viñetas solo para listas de condiciones.
- **Fuera de alcance**: inclúyelo cuando algo relacionado lo gestione otra API, equipo u otra historia. Indica quién lo gestiona.
- **Dependencias / consideraciones**: si algo fuera de alcance afecta a la historia, dilo explícitamente (ej. "si un servicio externo no responde, el flujo podría quedarse en espera").
- **No dupliques**: si un comportamiento ya está cubierto por otra historia, referencia esa historia por su título en lugar de repetir criterios.
- **Preguntas abiertas**: solo dudas reales pendientes de definir; no inventes requisitos.
- **Vocabulario**: usa los términos del dominio que use la persona (sus entidades, roles, sistemas y componentes) en lugar de términos genéricos.

## Qué NO hacer

- No inventes comportamientos que el usuario no mencionó; si hay duda, va a "Preguntas abiertas".
- No mezcles varias capacidades en una historia; si aparecen dos, propón dividir.
- No metas detalles de implementación (clases, endpoints, tecnologías) salvo que el usuario los pida.
- No te extiendas en explicaciones: entrega la historia y 1-2 observaciones.

## Ejemplo breve

**Título:** Enviar correo de confirmación al completar un pedido

**Historia:** Como cliente, quiero recibir un correo de confirmación cuando mi pedido se completa, para tener comprobante y saber que la compra fue exitosa.

**Criterios de aceptación:**
1. El correo se envía únicamente después de que el pago se confirma con éxito.
2. El correo incluye el número de pedido, los productos y el total pagado.
3. Si el pago falla o se cancela, no se envía el correo.
4. Si el envío del correo falla, el pedido no se revierte y el error se registra en log.

**Fuera de alcance:**
- Diseño visual de la plantilla del correo (lo gestiona el equipo de marca).

**Preguntas abiertas:**
- ¿Se debe reintentar el envío si el proveedor de correo falla?
