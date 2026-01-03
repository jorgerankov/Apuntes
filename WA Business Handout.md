## <u>Completar todas las Acciones requeridas</u> (!!!)

## Cosas a crear antes de seguir los pasos
- Crear **App** en [Apps de Meta Developers](https://developers.facebook.com/apps/) 
- Crear **Portfolio Comercial** en [Facebook for Business](https://business.facebook.com/)
- Asignar **Administrador en Portfolio** y darle **activos**
### <u>Obtener App_ID</u>
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) 
- Copiar Identificador de App 
- ![[Pasted image 20260103123024.png|350]]
### <u>Obtener WA Business ID</u>
- Ir a [Facebook for Business](https://business.facebook.com/)
- Seleccionar el Portfolio comercial creado
- Ir a **Configuración** --> **Cuentas**--> **Cuentas de WhatsApp**
- Obtener **Identificador**
- ![[Pasted image 20260103125730.png]]

### <u>Obtener Clave Secreta de App</u>
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) --> Seleccionar tu App
- Ir a **Configuración de la app** --> **Básica**
- Presionar el botón **Mostrar** en el recuadro **Clave secreta de la app** 
### <u>Suscribir Wpp a Permisos y funciones</u>
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) --> Seleccionar tu App
- Elegir solapa **Casos de Uso** --> **Permisos y funciones**
- Suscribir app a:
	- **business_management**,
	- **whatsapp_business_messaging**,
	- **whatsapp_business_management**,
	- **whatsapp_business_manage_events**
	- **public_profile**

### <u>Obtener PHONE_NUMBER_ID</u>
```
curl -s "https://graph.facebook.com/v24.0/WABA_ID/phone_numbers?access_token=ACCESS_TOKEN"
```
- Cambiar WABA_ID y ACCESS_TOKEN por los valores de App
- De todo lo que devuelve, **"id" == PHONE_NUMBER_ID**

### <u>Generar un Token permantente (ACCESS_TOKEN)</u>
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) --> Seleccionar tu App
- Elegir solapa **Casos de Uso** --> **Configuración**
- Seleccionar **Crea un token de acceso permanente**
- Seguir los pasos en pantalla para asignar el token a la App, los permisos necesarios y el tiempo de vida del token
### <u>Crear una cuenta de WhatsApp Business</u>
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) --> Seleccionar tu App
- Elegir solapa **Casos de Uso** --> **Configuración**
- Seleccionar **Crea una cuenta de WhatsApp Business**
- Seguir los pasos para crear la cuenta de Wpp Business
	- Esta cuenta es distinta a la que conocemos todos ya que una está conectada a la App directamente, pero la que vamos a crear estará conectada a la API de Meta
	- Hay que eliminar la cuenta existente y crearla de cero con este método (Revisar posibilidad de no hacerlo)
		- O usar un número nuevo de WhatsApp

### <u>Suscribirse a Webhooks</u>
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) --> Seleccionar tu App
- Elegir solapa **Casos de Uso** --> **Configuración**
- Buscar **Suscribirte a webhooks**
- Pegar **URL de devolución de llamada** que provee, en este caso, ngrok
- **Crear un password (VERIFY_TOKEN)**, que es el que vamos a usar en la App para poder traer los POST de los mensajes y eventos que realicemos
- Presionar botón **Verificar y guardar**
- Suscribir los Webhooks a **todos los Campos del webhook disponibles**
	- Si alguno no nos deja, dejarlo así

### <u>Registrar PHONE_NUMBER_ID</u>
```
curl -X POST "https://graph.facebook.com/v21.0/PHONE_NUMBER_ID/register" \
  -H "Authorization: Bearer ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "messaging_product": "whatsapp",
    "pin": "000000"
  }'
```
- Cambiar WABA_ID y ACCESS_TOKEN por los valores de App
- Pueden poner el pin que quieran, "000000" es un default

### <u>Suscribir la app al WABA por API</u>
```
curl -i -X POST "https://graph.facebook.com/v24.0/WABA_ID/subscribed_apps" \
  -H "Authorization: Bearer ACCESS_TOKEN"
```
- Cambiar WABA_ID y ACCESS_TOKEN por los valores de App


Luego, agregar todos los valores obtenidos a un .env dentro de la carpeta, usarlos en el `server.js` del repo, **asignarle un port** (en el repo está puesto el port 3000) y levantar el servidor con `node server.js`

Correr ngrok con el comando `ngrok http XXXX`, donde XXXX es el puerto que levantamos en `server.js`

Finalmente, enviar mensajes de prueba y ver si se muestra el METADATA en consola. Si se muestra, ya levantamos el bot y está funcionando correctamente.
