# Prueba La Chona

## Demo disponible

Abre **[lachona.ai](https://lachona.ai)**, solicita acceso con **Armar mi reunión** y espera la aprobación del anfitrión. Regresa desde el mismo navegador para consultar el estado. El enlace a Telegram aparece después de la aprobación. Si ya tienes acceso, usa **Ya tengo acceso**.

La demo utiliza Telegram y un servicio local; no basta con abrir la landing para probar la conversación. Si tu solicitud sigue pendiente, consulta el [video de presentación registrado](https://www.loom.com/share/135a3098f5b14cd38d324bf965abad09) mientras el anfitrión revisa el acceso.

## Un recorrido de dos minutos, una vez aprobado

1. Envía: **6 botellas de tequila blanco, presupuesto $3000, Zapopan, 30 invitados**.
2. Comprueba el resumen: tequila blanco, seis botellas, $3,000 MXN, treinta invitados y Zapopan. La cantidad de invitados se mantiene separada de las botellas.
3. Confirma con **Sí, buscar opciones**.
4. Revisa proveedor, presentación exacta, precio unitario, subtotal, enlace y fecha de observación.
5. Envía **presupuesto $1000**, confirma de nuevo y observa si hay una opción que cumpla el nuevo presupuesto.
6. Prueba **6 botellas de bebidas sin alcohol, presupuesto $600, Zapopan**. No debe sustituirlas por alcohol ni inventar un precio.

Una observación usada en la verificación del 30 de octubre de 2026 fue Campo Azul Blanco 100% Agave 750 ml, La Penca: $287 MXN por botella × 6 = **$1,722 MXN**, sin envío. Es un resultado histórico verificable, no una promesa de precio o disponibilidad actuales. [Fuente del producto](https://lapencavinos.com/producto/campo-azul-blanco-100-agave-750ml/).

## Cómo ejecutar el proyecto desde el código

El código está en un repositorio privado. El propietario debe conceder acceso al revisor antes de ejecutar los pasos siguientes; este repositorio público no contiene la aplicación. [Solicitar revisión técnica](https://github.com/sergiodeduarte/lachona/issues/new?title=Acceso%20para%20revisi%C3%B3n%20t%C3%A9cnica).

Requisitos: Node.js 22.13+, npm, Ollama con `qwen3.5:4b`, un bot propio de Telegram y un servicio de acceso Cloudflare Workers/D1 configurado. No reutilices credenciales del despliegue de La Chona.

```sh
git clone https://github.com/sergiodeduarte/la-chona-private.git
cd la-chona-private
npm ci
cp .env.example .env  # solo en una instalación nueva
ollama pull qwen3.5:4b
```

Configura en `.env` tu token de bot, identidad numérica del propietario, URL del servicio de acceso y secreto compartido. Para alojar una instancia independiente, sigue `docs/ENGINEERING.md` y `docs/RUNBOOK.md` en el repositorio privado: requieren preparar la configuración de dominio/Worker/D1 para tu cuenta antes de desplegar. El script de producción apunta a la infraestructura del propietario; no es un instalador genérico.

```sh
npm test
npm run check
cd landing
npm ci
npx tsc --noEmit
npm run build
cd ..
# Con el servicio de acceso configurado y Ollama ejecutándose:
npm start
```

Las pruebas automatizadas usan servicios simulados y bases de datos de prueba; no sustituyen una demostración con usuarios reales. Solo debe ejecutarse un proceso de polling por bot. El repositorio privado contiene el procedimiento de arranque, migraciones, supervisión, recuperación y verificación.

## Qué está disponible y qué sigue

V1 maneja una categoría a la vez y hasta tres alternativas del catálogo disponible. Cada alternativa cubre la cantidad completa, no es parte de una compra combinada. Stock, entrega y envío se confirman con el proveedor. No hay compra automática, búsqueda abierta de proveedores, catering, reservas de espacios ni contratación de entretenimiento.

V2 ampliará el producto por etapas. La incorporación de más proveedores y servicios es trabajo futuro.
