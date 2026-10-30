# Obstáculos, correcciones y lecciones de La Chona

Estos problemas aparecieron al probar la demo con solicitudes reales. Los registramos para mostrar qué identificamos, cómo lo corregimos y qué límites siguen vigentes. **No basta con que la IA responda: la persona debe recibir una recomendación útil, verificable y fiel a su solicitud.**

## 1. Había bebidas en el catálogo, pero la respuesta decía que no había opciones

**Síntoma.** Distintas solicitudes terminaban en el mismo mensaje de “no tengo opciones verificadas”, incluso cuando el catálogo contenía productos adecuados.

**Causas identificadas.** Una preferencia de la bebida anterior podía quedarse activa al cambiar de categoría. Palabras generales de calidad o precio se trataban como si fueran parte obligatoria del nombre de un producto. Además, el catálogo inicial no cubría algunas presentaciones concretas pedidas por el usuario.

**Corrección.** Al cambiar de categoría se eliminan las preferencias heredadas, salvo que se vuelvan a indicar. Las descripciones generales dejan de funcionar como filtros de marca. Las marcas y variantes explícitas se conservan: no se sustituyen silenciosamente. Añadimos la equivalencia deliberada **Red Label / Etiqueta Roja** y dos presentaciones verificadas directamente en el proveedor, llevando el catálogo a **17 productos**. Las respuestas ahora distinguen falta de cobertura, preferencia no disponible y presupuesto insuficiente. Quitar una preferencia exige revisar y confirmar el nuevo resumen.

**Verificación.** Las regresiones recorren interpretación, confirmación y búsqueda con el catálogo real, incluyendo un “sí” escrito y cambios de categoría. Se comprobaron también dos interpretaciones con Qwen local. El usuario confirmó después la recepción de opciones en Telegram.

**Lección.** Un resumen correcto no demuestra que la búsqueda funcione. Hay que probar hasta la recomendación final y explicar por qué una restricción impide encontrar opciones. El catálogo sigue siendo finito; una ausencia se comunica, nunca se resuelve inventando un precio o cambiando la marca solicitada.

## 2. Llegaba el acuse, pero el resumen no aparecía durante más de cinco minutos

**Síntoma.** El bot decía “¡Va! Recibí tu solicitud…” y parecía quedarse pensando.

**Causa identificada.** Qwen ya había terminado y la solicitud estaba guardada. El envío del resultado a Telegram había quedado **sin confirmar**. El manejador anterior descartaba los detalles del error y marcaba el trabajo como terminado. La causa exacta de aquel fallo de transporte no puede recuperarse con los registros antiguos; no afirmamos que fuera necesariamente un timeout.

**Corrección.** Se separan los rechazos explícitos de los envíos ambiguos y se conservan diagnósticos sin credenciales ni contenido privado. Solo un rechazo explícito por límite de solicitudes permite un reintento breve y acotado. Los envíos sin confirmar no se repiten a ciegas. **/solicitud** recupera el último resumen guardado sin volver a ejecutar Qwen, verifica el acceso y pide confirmación antes de mostrar opciones. El estado del trabajo distingue ahora un fallo de entrega de un envío confirmado.

**Verificación.** Pasaron **41 pruebas automatizadas y la comprobación de tipos**, con casos de rechazo, espera acotada, envío ambiguo, deduplicación y recuperación. Telegram aceptó el envío de recuperación y **el usuario confirmó que recibió tanto el resumen como las opciones**. Esto verifica ese recorrido real; no sustituye una prueba de cinco cuentas simultáneas.

**Lección.** “Trabajo terminado” no significa “mensaje entregado”. Recepción, interpretación, persistencia y envío son pasos diferentes y deben poder diagnosticarse por separado. Recuperar una solicitud no debe borrar el contexto ni generar duplicados innecesarios.

## Qué nos llevamos a V2

Ampliar el producto por etapas también implica ampliar sus pruebas y rutas de recuperación. Más proveedores y servicios necesitan fuentes verificables, límites claros y confirmaciones útiles. [Prueba la demo](DEMO.md) o consulta la [guía de evaluación](EVALUATION.md).
