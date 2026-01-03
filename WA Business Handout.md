### Obtener App_ID
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) 
- Copiar Identificador de App 
- ![[Pasted image 20260103123024.png|350]]
### Obtener Clave Secreta de App
- Ir a [Apps de Meta Developers](https://developers.facebook.com/apps/) --> Seleccionar tu App
- Ir a **Configuración de la app** --> **Básica**
- Presionar el botón **Mostrar** en el recuadro 

### Obtener WAB ID

### Obtener PHONE_NUMBER_ID

### Crear un password (VERIFY_TOKEN)

### Generar un Token permantente (ACCESS_TOKEN)



### Suscribir la app al WABA por API
```
curl -i -X POST "https://graph.facebook.com/v24.0/1410466587262068/subscribed_apps" \
  -H "Authorization: Bearer $WA_TOKEN"
```


