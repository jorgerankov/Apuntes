- Permiten contener 
- Standarized unit of software
- Plataforma que me permite guardar/contener una aplicacion A y sus liberias de manera virtualizada
- Icluye todo lo necesario para correrla, junto al OS, el Server y el hardware necesario
- Mejora la abstraccion de elementos 

### Container != Virtualizacion
- Contiene distintos niveles de abstraccion
- En los servers, todos los componentes pelean por los recursos
- Poniendo una plataforma de virtualizacion, todo se estabiliza de mejor manera, pero implica instalar todo para toda virtualizacion
- Containers son mejores en eficiencia de recursos y en gasto, las apps virtualizadas comparten librerias y no se pelea por recursos, se comparten y, ademas, se pueden isolar

### Docker
- Container ligero que permite armar una plataforma de virtualizacion
- Da herramientas para crear, almacenar, modificar y correr containers
- Se integra con testers, builders y deployment pipelines
- #### Beneficios
	- ES portable
	- Se puede almacenar todo package en un solo e inmnutable artifact ->  image
	- Puedo llevarla a cualquier lugar para correrla, tambien puedo correr diferentes versiones