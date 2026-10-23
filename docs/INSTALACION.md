# Instalar Bosque en tu LG webOS
## 1. Prepara el televisor
Conecta PC y TV a la misma red. Crea una cuenta gratuita de desarrollador de LG.
Instala **Developer Mode** desde la tienda del TV. Inicia sesión, activa **Dev Mode Status** y acepta el reinicio. Abre de nuevo la aplicación y activa **Key Server**.
Anota la IP y la frase de acceso que muestra. No las publiques.

## 2. Descarga y prepara el proyecto
En GitHub: Code → Download ZIP. Descomprime y abre una terminal en la carpeta que contiene package.json. Instala Node.js LTS desde https://nodejs.org/ y ejecuta:

```sh
node --version
npm --version
npm install
npm run preview
```

Abre http://127.0.0.1:4173. Ctrl+C detiene la vista previa. En el ordenador no se abren las apps del TV.

## 3. Biblioteca oficial de LG
La biblioteca webOSTV.js 1.2.13 ya está incluida en app/vendor/, sin modificaciones, junto a su licencia Apache 2.0. No necesitas descargarla ni usar un CDN.
Fuente: https://webostv.developer.lge.com/develop/references/webostvjs-introduction
Para actualizarla, descarga el ZIP oficial y conserva los avisos legales. Utiliza webOS TV, no webOS OSE.

## 4. Registra el TV
```sh
npx ares-setup-device
```
Elige add y escribe:
- Nombre: sala
- IP: la que aparece en tu TV
- Puerto: 9922
- Usuario SSH: prisoner
- Sin contraseña SSH

Activa Key Server y ejecuta:
```sh
npx ares-novacom --device sala --getkey
npx ares-device --system-info --device sala
```
Introduce la frase del TV cuando la solicite.

## 5. Empaqueta, instala y abre
```sh
npm test
npm run check
npm run package
npx ares-install --device sala dist/com.bosque.launcher_1.0.0_all.ipk
npx ares-launch --device sala com.bosque.launcher
```
Comprueba el nombre real del .ipk generado en dist/ y ajusta el comando si difiere. Después podrás abrir Bosque desde la lista de apps.

## 6. Personaliza
Abre ⚙ o pulsa azul. Cambia la sala, el fondo y las aplicaciones. Una línea por acceso:
```text
Netflix | netflix | {}
YouTube | youtube.leanback.v4 | {}
HDMI 1 | com.webos.app.hdmi1 | {}
```
Los IDs son ejemplos. Consulta lo instalado con:
```sh
npx ares-install --device sala --list
```
La lista puede no incluir todas las apps de sistema. Prueba un ID:
```sh
npx ares-launch --device sala netflix
```
Si funciona por CLI y falla en Bosque, revisa las restricciones de seguridad: la CLI y una app no tienen necesariamente los mismos permisos.

Comprueba en tu TV: flechas, OK, Atrás, puntero, apertura de cada app, regreso manual a Bosque, guardado al cerrar y abrir y actualización del reloj.

## 7. Fondo propio
Copia una foto con permiso de uso a app/assets/fondo.jpg. Empaqueta e instala de nuevo. En ajustes escribe assets/fondo.jpg.
También se admite HTTPS, que necesita conexión y un certificado/formato compatible. El servidor externo recibirá la solicitud del televisor.
Los fondos incluidos son ilustraciones originales, no la fotografía exacta de la referencia.

## 8. Más televisores y actualizaciones
Registra cada TV con otro nombre e instala el mismo .ipk. Cada televisor conserva sus propios ajustes.
Para actualizar código, aumenta version en app/appinfo.json y package.json, empaqueta y reinstala.
Renueva la sesión con EXTEND en Developer Mode **antes** de caducar. No se incluye renovación automática. Desinstalar o borrar datos puede eliminar los ajustes.

## Fuentes oficiales
Consultadas el 23 de octubre de 2026:
- [Developer Mode](https://webostv.developer.lge.com/develop/getting-started/developer-mode-app)
- [Primera aplicación](https://webostv.developer.lge.com/develop/getting-started/build-your-first-web-app)
- [Application Manager y errores](https://webostv.developer.lge.com/develop/references/application-manager)
- [Metadatos](https://webostv.developer.lge.com/develop/references/appinfo-json)
- [Permisos ACG](https://webostv.developer.lge.com/develop/guides/acg-guide)
