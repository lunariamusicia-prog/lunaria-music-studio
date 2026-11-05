# LUNARIA — V3 + primera pantalla de acceso

Este paquete conserva `web/index.html` como la página principal V3 y agrega `web/acceso.html` como primera pantalla de autenticación conectada a Supabase.

## Configuración incluida
- Supabase URL del proyecto `lunaria-production`.
- Publishable key (`sb_publishable_...`) en el navegador.
- Inicio de sesión por correo y contraseña.
- Solicitud de magic link para usuarios ya existentes (`shouldCreateUser: false`).
- Validación del perfil en `public.profiles` y del estado `active`.
- La pantalla muestra el rol detectado, pero todavía no expone módulos ni datos de pedidos.

## Cómo probar localmente
1. Descomprimir el ZIP.
2. Servir la carpeta `web` desde un servidor web local o desplegarla en un entorno de pruebas HTTPS.
3. Abrir `/acceso.html`.
4. Iniciar sesión con el correo y contraseña del administrador creado en Supabase.

No abrir como `file://` para pruebas definitivas de enlaces de autenticación. En Supabase Authentication > URL Configuration, agregar la URL del entorno de pruebas a Site URL / Redirect URLs según corresponda.

## Limitaciones y seguridad
- `index.html` sigue conservando el formulario de demostración; no registra pedidos en la base de datos.
- El panel administrativo y los paneles de producción/soporte aún no están construidos.
- Magic link depende de la configuración de URLs y del proveedor de correo de Supabase. No se debe probar como flujo de cliente final hasta configurar y validar correo.
- No se incluye ninguna secret key ni service_role key en el frontend.
- La autenticación no equivale a completar las pruebas de RLS. Antes de operar se deben revisar y probar permisos, restricciones por columna, carga y descarga privada, y backend de pedidos.
- No aceptar pagos ni pedidos reales con este paquete.
