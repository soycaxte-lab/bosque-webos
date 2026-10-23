# Compatibilidad y diagnóstico
Objetivo: webOS TV 4.0 o posterior, sujeto a pruebas físicas. No hay modelos certificados todavía.
La biblioteca oficial indica soporte completo desde webOS TV 4.0.

| Problema | Comprobar |
| --- | --- |
| No conecta | Misma red, IP, puerto 9922, usuario prisoner, clave y sesión |
| Falta biblioteca al empaquetar | app/vendor/webOSTV.js |
| No abre una app | ID, región, instalación, parámetros y permisos |
| Error -101 | Aplicación no encontrada |
| Error -103 / -104 | Restricción de seguridad o app privilegiada |
| Sin desenfoque | El motor puede no admitir backdrop-filter; queda un panel translúcido |
| Inicio abre el menú de LG | Esperado: no se reasigna ese botón |
| No abre al encender | No se ofrece arranque automático |
| Desaparece al caducar Developer Mode | Reactiva, enlaza si hace falta y reinstala |
| No guarda | Almacenamiento no disponible o lleno; se muestra el error |
| Fondo remoto no aparece | URL, conexión, TLS y formato; prueba un archivo local |

TV en directo y HDMI pueden estar bloqueados para aplicaciones de desarrollo.
El modo ambiente oculta la interfaz y mantiene las protecciones del televisor.
No se distribuyen logotipos comerciales ni la fotografía de referencia.

## Registro de pruebas
Antes de anunciar compatibilidad, documenta modelo, versión de webOS, región, versión de Bosque, controles y resultado de cada acceso. No publiques claves, IP privadas ni cuentas.
