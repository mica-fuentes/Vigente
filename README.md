# Vigente · demo interactiva

Prototipo navegable de **Vigente**, la app de calendario de vencimientos impositivos para estudios contables.
Se construyó a partir del Figma **TP-DG3** (página «NO TOCAR»: User Flow + Mapa de navegación) y cubre las
tres superficies del diseño: **web**, **app móvil** y **smartwatch**.

No tiene backend ni build: son archivos estáticos (HTML + CSS + JS). Los datos viven en `localStorage`.

## Cómo abrirla

- **Doble clic en `index.html`** (o, si preferís servidor: `python -m http.server 5173` y abrir `http://localhost:5173`).
- Hace falta internet sólo para las tipografías (Inter y Space Grotesk, de Google Fonts). Sin conexión usa una tipografía del sistema.
- Cualquier email/contraseña entra (si escribís un email, tiene que tener formato válido).

## Qué hay

| Archivo | Qué es |
|---|---|
| `index.html` | **Web** (1440 px): login, recuperar contraseña, Hoy, Calendario (lista/semana/mes), detalle de trámite, clientes, ficha, documentación, novedades, foro, configuración |
| `app.html` | **App móvil** (390 px, en marco de teléfono): login, Hoy, Calendario, detalle, nota, Clientes, Novedades, Foro, Notificaciones |
| `watch.html` | **Smartwatch**: vista previa interactiva con los 4 estados del Figma |
| `css/vigente.css` · `css/mobile.css` | Sistema de diseño (tokens del Figma) y estilos de app/reloj |
| `js/store.js` | Datos de ejemplo + estado compartido + reglas (estados de trámites, generación de calendario) |
| `js/ui.js` | Helpers: badges, modales, toasts, descargas, barra de demo |
| `js/web-*.js` · `js/mobile.js` · `js/watch.js` | Pantallas de cada superficie |

Web, app y reloj **comparten el estado**: si marcás «Ya lo presenté» en el reloj, el trámite queda presentado en la web y en la app.

## Barra «Demo» (abajo a la derecha)

- Abre la **app móvil** y el **smartwatch** en ventanas aparte.
- **Reiniciar la demo** · **Empezar desde cero (primer día)** (estado vacío → onboarding de 3 pasos / importar Excel) · **Simular sin conexión con la fuente** · Cerrar sesión.

## Qué funciona (web)

- **Presentar un trámite** (Hoy o detalle) con fecha, **deshacer**, **avisar al cliente** (texto editable), **agregar nota**, **pedir documentación** (lista, fecha límite, vista previa del correo) y seguimiento en *Documentación pendiente*.
- Variantes del trámite: **vencido** (presentar fuera de término), **prórroga aplicada** (con «Fijar fecha manualmente»).
- **Calendario** lista / semana / mes con navegación; los contadores se recalculan.
- **Alta de cliente**: modal → perfil impositivo → «Generando el calendario» → calendario con trámites nuevos. También **onboarding del primer cliente** e **importación** (CSV real; .xlsx muestra una vista previa de demostración).
- **Ficha del cliente** con 4 pestañas (el perfil impositivo editable recalcula los vencimientos futuros).
- **Notificaciones** (panel, marcar leídas, navegan a su pantalla), **búsqueda** de clientes (sin tildes), filtros.
- **Novedades y cursos**, clientes afectados (adhesión editable), **foro** (categorías, responder, «Me sirve», abrir tema).
- **Configuración**: cambiar foto, cambiar contraseña (con validaciones), verificación en dos pasos, alertas, fuentes oficiales, plan, exportar cartera.

## Pantallas y dispositivos

- La **web** (`index.html`) es responsive: en escritorio usa el menú lateral; en tablet y celular (hasta 900 px) pasa a una barra superior con menú, notificaciones y botón «Demo», las tablas se vuelven tarjetas y los modales se abren como hoja inferior. Probada de 320 a 1440 px.
- La **app móvil** (`app.html`) ocupa toda la pantalla en celulares (≤ 520 px) y se muestra dentro de un marco de teléfono en pantallas más grandes.

## Alcance de la demo

Es una demostración de diseño, no un producto: **no se envían correos reales** (avisos, recordatorios, recuperar contraseña),
no hay verificación por mail ni cifrado de documentos, y las contraseñas no se guardan ni se validan.
Las fuentes (AFIP/ARCA, ARBA, AGIP) son simuladas. Las exportaciones y la plantilla de importación son **CSV**.

## Fecha de la demo

«Hoy» está fijo en **miércoles 12 de agosto de 2026** (como en las pantallas de Hoy del Figma) para que el calendario siempre se vea igual.
