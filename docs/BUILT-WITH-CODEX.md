# Construida con Codex

## Una tarea concreta, con evidencia

![Codex trabajando en La Chona](evidence/codex-usage.png)

Captura original proporcionada por Sergio Duarte. Muestra una sesión de Codex en el terminal durante la tarea de conservar la landing anterior y publicar la propuesta aprobada con el flujo real de acceso. Se ve la inspección del comando de rollback y el trabajo de conexión del formulario a la base de datos y aprobación. La captura documenta el proceso; la verificación posterior aporta la evidencia del resultado.

El nombre público `lachonabot` es visible. No se publican archivos `.env`, tokens del bot, claves de Cloudflare, datos de solicitudes ni historiales privados de conversaciones.

## Qué hizo Codex y cómo se comprobó

| Trabajo | Comprobación registrada |
| --- | --- |
| Bot TypeScript, interpretación mediante Ollama y cola serial | Pruebas de mensajes, aislamiento, duplicados, cantidad/invitados y restricciones sin alcohol |
| Validación y catálogo con procedencia | Cálculos deterministas, precios desconocidos excluidos de totales y fuentes con fechas |
| Registro web y aprobación manual | Flujo real con dos sesiones: solicitud pendiente, aprobación del anfitrión, aparición del enlace, revocación y cierre de sesión |
| Landing y cambio de diseño | Compilación, escritorio/móvil, ausencia de desbordamiento horizontal y apertura del formulario |
| Respaldo antes de publicar | Archivo de fuente/build y versión anterior identificada; disponibilidad de rollback comprobada sin ejecutar un rollback real |
| Cambio de identidad del bot | Preservación de borradores, reinicio de offsets del nuevo bot y pruebas de migración |

El humano definió el alcance, eligió el diseño, aprobó el despliegue, configuró las cuentas y probó la conversación. Codex implementó, revisó y verificó iteraciones bajo esas decisiones.

## Trabajo nuevo y reutilización

El historial del proyecto empieza con documentación el 29 de octubre de 2026. La implementación del bot, el acceso, el catálogo y las iteraciones de landing se registran el 29–30 de octubre. Parte del trabajo continuó después de la sesión presencial del Build Day; no afirmamos que la versión actual completa ya existiera durante esa sesión.

Se reutilizaron un starter de Sites/Vinext, bibliotecas y componentes existentes. Ollama/Qwen y Telegram son herramientas de terceros; los precios proceden del proveedor. Consulta [reutilización y licencias](REUSE-AND-LICENSES.md).

## Límites de la evidencia

La verificación registrada incluye tests automatizados y flujo web real. El benchmark de cinco interpretaciones secuenciales de Qwen fue **60.44 segundos**, con entradas validadas. No fue una prueba de cinco cuentas reales de Telegram en paralelo. La prueba real de conversación proporcionada por el propietario conservó treinta invitados como contexto y calculó seis botellas a $287 = $1,722 MXN.

El siguiente paso de validación es ampliar la prueba con personas reales, distintos mensajes y una ráfaga de varias cuentas. La evidencia de uso de Codex y la elegibilidad final son revisadas por los organizadores; este documento no afirma una aprobación ya concedida.

Fuentes de requisitos: [evidencia de Codex, diapositiva 8](https://codex-build-day-guadalajara-slides.aileenvl375305.chatgpt.site/assets/slide-08.png), [elegibilidad, diapositiva 10](https://codex-build-day-guadalajara-slides.aileenvl375305.chatgpt.site/assets/slide-10.png).
