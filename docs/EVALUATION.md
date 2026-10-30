# Guía para evaluar La Chona

**Demo:** [lachona.ai](https://lachona.ai) · **Presentación:** [Loom](https://www.loom.com/share/135a3098f5b14cd38d324bf965abad09) · **[Evidencia de Codex](BUILT-WITH-CODEX.md)**

## Qué resuelve V1

Una persona comparte bebida, cantidad, presupuesto y zona. La Chona confirma la interpretación y presenta hasta tres alternativas del catálogo con proveedor, presentación exacta, precio observado, subtotal y fuente. Más servicios para organizar fiestas pertenecen a V2.

## Recorrido de evaluación

Solicita acceso en la landing y espera la aprobación del anfitrión. Vuelve desde el mismo navegador para abrir el enlace de Telegram. Envía: **6 botellas de tequila blanco, presupuesto $3000, Zapopan, 30 invitados**. Confirma el resumen, revisa las opciones y luego prueba **presupuesto $1000**. Treinta invitados deben seguir siendo contexto, no treinta botellas. [Guion e instrucciones](DEMO.md).

## Evidencia técnica

| Aspecto | Qué revisar |
| --- | --- |
| Utilidad y alcance | Flujo completo de bebidas; separación explícita de V1 y funciones futuras |
| Confiabilidad | Confirmación humana, cantidades validadas, subtotales en centavos y precios con fuente/fecha |
| Experiencia | Landing móvil/escritorio, estados de aprobación, mensajes de espera y recuperación |
| Arquitectura | TypeScript, Qwen/Ollama local, cola serial, SQLite y acceso Workers/D1 |
| Uso de Codex | Captura original, tareas concretas y explicación de su verificación |
| Reutilización | Starter, bibliotecas y procedencia documentados en [atribuciones](REUSE-AND-LICENSES.md) |

Pasaron 23 pruebas automatizadas y comprobaciones de tipos. El flujo web real se verificó con aprobación y revocación. El benchmark local de cinco interpretaciones consecutivas fue 60.44 segundos; no representa cinco cuentas reales simultáneas.

## Límites y acceso al código

V1 utiliza un catálogo acotado de un proveedor de Guadalajara/Zapopan. No compra, contrata ni garantiza existencia, envío o entrega. La demo requiere aprobación y el equipo de inferencia local disponible.

El código y la documentación operativa son privados. El propietario debe conceder acceso para revisión técnica; [solicítalo aquí](https://github.com/sergiodeduarte/lachona/issues/new?title=Acceso%20para%20revisi%C3%B3n%20t%C3%A9cnica). El material público explica el producto y sus evidencias; la decisión de elegibilidad corresponde a los organizadores.
