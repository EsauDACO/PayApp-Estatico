# PayApp+

Versión frontend-only de PayApp+, una aplicación de gestión financiera desarrollada originalmente con Node.js, Express y PostgreSQL. Esta variante elimina por completo la dependencia de un backend real: toda la lógica de negocio, validaciones y persistencia se ejecutan en el navegador mediante JavaScript vanilla y localStorage, lo que permite explorar el flujo completo del producto sin necesidad de servidor, base de datos ni proceso de inicio de sesión.
Propósito
Esta versión está pensada como una capa de demostración/prototipo: replica las funcionalidades clave del proyecto original (transferencias, pagos, historial, panel administrativo) de forma autocontenida, ideal para presentaciones, revisión rápida de UX/UI o como referencia de portafolio, sin exponer credenciales ni requerir infraestructura.
Acceso
Al cargar la página se presenta un selector de rol en lugar de un formulario de login:

Ver como Usuario — accede a la vista de cliente con una cuenta de ejemplo precargada.
Ver como Administrador — accede al panel administrativo con datos agregados del sistema.

No existe autenticación real ni separación de sesiones; el cambio de rol es instantáneo y puede alternarse en cualquier momento desde la barra lateral.
Funcionalidades
Vista de usuario

Resumen de cuenta con saldo disponible y número de cuenta.
Transferencias entre cuentas, con validación de saldo suficiente, existencia de la cuenta destino, bloqueo de autotransferencias y rechazo de cuentas destino bloqueadas.
Pago de servicios (electricidad, internet, agua, telefonía, streaming) con referencia y monto.
Historial de movimientos con filtrado por tipo y estado, y gráficas de ingresos vs. gastos (Chart.js).

Vista de administrador

Resumen agregado: usuarios registrados, saldo total del sistema y volumen de transacciones.
Tabla de usuarios con acciones de bloqueo/desbloqueo y cambio de rol (confirmadas mediante modal).
Listado global de transacciones de todos los usuarios.
Asignación manual de saldo a cualquier cuenta cliente.

Persistencia de datos
Todos los datos (usuarios, cuentas, transacciones) se almacenan en localStorage del navegador bajo una única clave (payapp_demo_v1). Esto significa que:

Los cambios persisten entre recargas y cierres del navegador.
Los datos son locales a cada navegador/dispositivo — no hay sincronización entre usuarios reales.
Existe una opción de "Restablecer datos de ejemplo" que limpia el localStorage y vuelve al dataset inicial.

Stack técnico
CapaTecnologíaEstructuraHTML5EstilosCSS puro (basado en el sistema de diseño del proyecto original)LógicaJavaScript vanilla (sin frameworks)GráficasChart.js (vía CDN)PersistencialocalStorage (API nativa del navegador)
Limitaciones conocidas

No hay autenticación, cifrado ni validación de servidor: todas las reglas de negocio son client-side y pueden ser manipuladas desde las herramientas de desarrollador del navegador.
No apto como sistema financiero real ni para datos sensibles; es exclusivamente una demo de interfaz y flujo funcional.
El dataset es fijo y sintético; no refleja transacciones ni usuarios reales.

Uso
Clona o descarga index.html y style.css en la misma carpeta y abre index.html directamente en cualquier navegador moderno. No requiere instalación de dependencias ni servidor local.
