## <u>Completar todas las Acciones requeridas</u> (!!!)
### <u>Obtener App_ID</u>
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) 
- Copiar Identificador de App 
- ![[Pasted image 20260103123024.png|350]]
### <u>Obtener Clave Secreta de App</u>
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) --> Seleccionar tu App
- Ir a **Configuración de la app** --> **Básica**
- Presionar el botón **Mostrar** en el recuadro **Clave secreta de la app** 
### Suscribir Wpp a Permisos y funciones
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) --> Seleccionar tu App
- Elegir solapa **Casos de Uso** --> **Permisos y funciones**
- Suscribir app a:
	- **business_management**,
	- **whatsapp_business_messaging**,
	- **whatsapp_business_management**,
	- **whatsapp_business_manage_events**
	- **public_profile**
### <u>Obtener WA Business ID</u>

### <u>Obtener PHONE_NUMBER_ID</u>

### <u>Crear un password (VERIFY_TOKEN)</u>

### <u>Generar un Token permantente (ACCESS_TOKEN)</u>
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) --> Seleccionar tu App
- Elegir solapa **Casos de Uso** --> **Configuración**
- Seleccionar **Crea un token de acceso permanente**
- Seguir los pasos en pantalla para asignar el token a la App, los permisos necesarios y el tiempo de vida del token
### Crear una cuenta de WhatsApp Business
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) --> Seleccionar tu App
- Elegir solapa **Casos de Uso** --> **Configuración**

### <u>Suscribir la app al WABA por API</u>
```
curl -i -X POST "https://graph.facebook.com/v24.0/1410466587262068/subscribed_apps" \
  -H "Authorization: Bearer $WA_TOKEN"
```


