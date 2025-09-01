## Entidades
* Representacion de un objeto de manera especifica (distinto al original)
* **Ejemplos** en una tienda: Clientes, proveedores, ordenes de compra 
## Notacion de Chen
* Forma de poder **representar Entidades**
* Se representa con la *Entidad encerrada dentro de un cuadrado*

## <u>Atributos</u>
Distintas caracteristicas de un objeto, se representa con ese atributo encerrado en un ovalo
##### Atributos simples
* Atributos que son unicos y representan una sola definicion
* Se representan con un ovalo liso
##### Atributos compuestos
* Atributos que representan mas de una definicion con un mismo nombre
##### Atributos multivalor
* Atributos que tienen mas de un unico valor
* Se representan con dos ovalos 
##### Atributos derivados
* Aquellos que se pueden obtener a partir de otros atributos
* Se representan con un ovalo punteado (de puntos)
##### Atributo Clave (key)
* Registro unico para un elemento (ejemplo: ID)
* Es una key pero tambien se representa con un ovalo

## <u>Tablas (Table)</u>
Estructura de Datos que **se organiza en filas y columnas**
#### Campo (Field)
* **Nombre** que se le da a **cada columna de la Tabla**
#### Valor del Campo (Field value)
* Valor que se le pone a cada elemento que este en una celda de un Campo especifico
#### Registros (Record)
* Toda la fila de una Tabla
* **Ejemplo**: Segundo Registro (fila 2): todos los datos de los Campos de la fila 2 

##### Representacion de Campo, Registros y Valor del Campo:

|   Campo   |      Campo      |      Campo      |
| :-------: | :-------------: | :-------------: |
| Registros | Valor del Campo | Valor del Campo |
| Registros | Valor del Campo | Valor del Campo |

## <u>Query</u>
* **Consulta a Base de Datos** (retornar, ver, modificar, agregar, eliminar, etc)
* Se usan para **CRUD (Create, Read, Update, Delete )**

## <u>Identificadores</u>
* Campo especifico que me permite identificar un registro entero 
* Registro unico (por ejemplo por ID, no pueden ser nulos)

## Claves primarias vs foreigns
* **Primarias**: Aquellas que se utilizan para *identificar un Registro como unico*
* **Foreigns**: Aquellas que *hacen referencia a una clave primaria de otra tabla*
	* ***Ejemplo***: ID usuario en una tabla: 6 -> nombre del ID 6 en otra tabla = 'Juan Perez'