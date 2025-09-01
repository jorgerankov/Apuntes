##### Crear la Base de Datos
	CREATE DATABASE "MI_BASE_DE_DATOS"
##### Crear Tabla
	CREATE TABLE "mi_tabla"

##### Tipos de datos

|      TEXT      |    INTEGER    |       BLOB        |               REAL                |              NUMERIC              |
| :------------: | :-----------: | :---------------: | :-------------------------------: | :-------------------------------: |
| Almacena texto | Almacena ints | Almacena binarios | Almacena numeros de hasta 64 bits | Almacena cualquier tipo de numero |

#### Propiedades de la Tabla

|       Name        |     Type     | NN  |               PK                |       AI       |  U  |
| :---------------: | :----------: | :-: | :-----------------------------: | :------------: | :-: |
| Nombre de columna | Tipo de dato |     | Primary key<br>(Registro unico) | Auto Increment |     |

##### Codigos de SQLite:
	SELECT * FROM usuarios -> Selecciono y retorno la tabla
	
	INSERT INTO usuarios (nombre, apellido) VALUES ('valor1', 'valor2')
		-> Inserto datos en la tabla con sus respectivos valores 
	
	DELETE FROM usuarios -> Elimina todo valor de la tabla
