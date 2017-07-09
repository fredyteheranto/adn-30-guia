# Guia Tecinf S.A.S para AND 3.0

![ADN logo](http://www.tinformatica.com/ADNWEB/app/IMG/adnV.png)

Reglas estádares para escribir y mantener código frontend y backend para implementando git.


## Introducción

Esta guía ha sido formulada con el propósito de normalizar el código fuente realizado, a través de herramientas que ayuden a acelerar y mejorar el proceso de creación de código web como lo son Angular, Swagger,SCSS,Doker,git. Se siguen convenciones estándares, pero se optimizan y normalizan varias reglas implícitas, dejando lugar al uso de criterio de cada integrante del equipo de desarrollo web.

### Encabezado
En todo archivo *.ts ("TypeScript") que corresponda a un template de una o varias varias páginas se incluirá dentro de las primeras líneas del mismo el siguiente encabezado a modo de comentario oculto, el cual deberá ser llenado por el desarrollador a cargo del proyecto ó que esté realizando el template:  

Ejemplo:

```
 * Proyecto:
 * Fecha creacion:
 * Email Desarrollador:
 * Descripción: 
 * Dependencias: 
 * Dónde se utiliza:
```

###Comentarios
Si necesitas realizar comentarios Para una nueva función, utiliza el siguiente bloque de comentario como formato base para documentar:

```
/**
 * Nombre descriptivo
 * Funcionalidad / qué hace
 * Dónde: Dónde se utiliza (elemento, página, etc)
 * Email Desarrollador: email de quien hizo esto
 * Uso:
  	var funcion = function (
		@param1: int|bool|element|rangos|etc,
		@param2: int|bool|element|rangos|etc
	) {
		return: bool;
	};
 */
```

###Sintaxis
* Utiliza 2 espacios (soft tab) / 1 tab (hard tab) para indentar.
* Usa doble comilla " (double quote) para abrir y cerrar atributos, propiedades, valores, etc.

###Nomenclaturas
* Los archivos creados deben tener su nombre en minúsculas, sin espacios ni caracteres especiales. Si el contenido del archivo corresponde a una directiva un plugin o un controlador, éste debe identificarse claramente como dependiente de tal componente o libreria y se permite el uso del nombre en minusculaMayuscula (camelCase), de la siguiente manera:

```
persona.nombrePlugin-version.ts
```
* Crea nombres de funciones, parámetros, métodos, variables y atributos en inglés, descriptivas al contexto y/o función que cumple el elemento, camelCased y sin espacio después del nombre y con espacio antes del bracket {.

```
// Bien
function openModalWindow() {}

// Mal
function cerrar () {}
```
* Todas las variables deben ser declaradas antes de ser utilizadas. Prefiere que cada variable sea declarada en una nueva línea y con su comentario inline: 


```
var element, 	// this
	 indent,	// nivel de indentación
	 width;	// ancho del elemento sin el valor
```


##Usi de GIT como herramienta 

Git es un sistema de control de versiones distribuido gratuito y de código abierto diseñado para gestionar todo desde un proyecto pequeño a un proyecto muy grande con rapidez y eficiencia.

###Que debemos tener a la mano e instaldo antes de usarlo

* Instálate Git ``` http://git-scm.com/ ```

* Create una cuenta en   ``` https://bitbucket.com/ ```

* Configura tu entorno
		
		```
		 $ git config --global user.name "Bruce Wayne"
		 $ git config --global user.email bruce.wayne@wayneindustries.com
		```
* clientes git Ver ``` https://git-scm.com/downloads/guis/ ```


##Trabajando con git

### Objetos de Git.
Hay 4 tipos de objetos en git (el más importante a entender es el commit).

* Blob: se usa para almacenar datos de archivos, es generalmente un archivo.

* Tree: es, básicamente, como un directorio, hace referencia a un conjunto de otros trees y/o blobs (por ej. archivos y subdirectorios).

* Commit: apunta a un determinado tree, marcando como era en un momento determinado (quien no haya entendido lo que es un tree, sustituya la palabra tree por archivo). Contiene información sobre ese momento determinado, los cambios del autor desde el último commit, el commit anterior (conocido como parent), etc. También se puede entender un commit, de una forma más imprecisa y coloquial, como la modificación o el conjunto de modificaciones a uno o varios archivos del repositorio. Otra forma de entenderlo también sería, como una "foto" de uno o varios archivos del repositorio en un momento determinado.

* Tag: es una forma de marcar un commit como específico de alguna forma. Se usa normalmente para marcar algunos commits como releases específicos o algo destacable en esas lineas.

###Clonar un Repositorio

Esto es muy simple. Una vez se llegue al directorio donde se va a clonar el repo vía línea de comandos, se debe indicar lo siguiente.

``` <git clone linkhttp> ```

### Realizar cambios, revertirlos y subirlos al repositorio remoto

Esta parte comprende el workflow que se realiza con normalidad cuando se está trabajando en un repositorio manejando Git. La dividiré en las siguientes partes:

* Añadir uno o varios archivos a un commit.
* Realizar un commit con su correspondiente mensaje.
* Subir los cambios al repositorio remoto.
* Revertir los cambios realizados por dicho commit.

Para apreciar los cambios que se producen en el repositorio mientras se realizan estas acciones se utilizará el comando `<git status>` Si no hemos realizado ningún cambio en el repositorio, al usar ese comando nos debería mostrar algo así:

`<➜repo:(master) git status> <On branch master> <nothing to commit (working directory clean)>`

###Añadir archivos a un commit

Esto se realiza con el comando `<git add>` Seguido del nombre de la ruta y nombre del archivo que se quiere añadir al commit, de forma que quedaría así: `<git add directorio/directorio/archivo.extensión>`

Sólo podremos usarlo para archivos modificados o añadidos al repositorio.

###Realizar un commit

* `git commit -m " tipo_de_cambio(Visual o funcional) , mensaje,pie_de_mensaje"`

* Revisar los cambios individuales `git diff`

###Revisar historial de cambios

* git log
* git log --oneline

###Branches y merges
* Listado de branch (`git branch`)
* Crear branch (`git branch ADN-011`)
* Cambiar de rama (`git checkout ADN-011`)
* Crear branch y ubicarse en el (`git checkout -b ADN-011`)

### Merge

Las ramas divergen y en algún momento querremos fusionar los desarrollos:

```
git checkout <rama-destino>
git merge <rama-origen>
```

### Visualizar las ramas de trabajo

```
git log --online --graph
```
### Stash
* Guardando cambios pendientes (`git stash`)
* Listado de cambios almacenados (`git stash list`)
* Aplicar cambios (`git stash apply`)
* y mas opciones (`save, list, drop, pop, apply, branch`)

###Repositorios remotos
* Listamos repositorios (`git remote`)
* Agregamos la referencia (`git remote add origin  repo_.git`)
* Subir cambios  (`git push <brach>`)

### Flujo: fetch, pull, push

* Fetch: (importa los commits del repositorio remoto (no los aplica)
) ` git fetch origin` OR  `git branch -a`
* Pull: fetch + merge (`git pull origin`)

es posible que  habitualmente usemos  --rebase para conseguir una historia más lineal y evitar merges:

```
git pull --rebase origin
```
* Push: enviar los cambios al repositorio remoto `git push origin master`

##Trabajo en equipo
Quién y cuando se modificó cada línea de un fichero, esto se utiliza cuando necesitamos ver un errror especifico y no tenemos o no sabemos quien modifico x archivo se usa el siguiente comando `git blame file.ts`

####Ciclo de desarrollo 

![ADN logo](https://s3.amazonaws.com/media-p.slid.es/uploads/gruizdevilla/images/90562/git-workflow-release-cycle-3release.png)

####Metodo de trabajo

Cada viernes se libera un nuevo sprint y se realiza una reunion en la cual se revisan cambios ven tareas.

la idea es partir la semana de desarrollo en 4 dias los cuales son desarrollo fuerte y el vua 5 es dia de deploy.

por cada insidencia se realiza un brach con el nombre de la tarea en este caso esn nombradad como ADN-000 en la cual es responsable cada desarrollador el dia 4 previa a la entrega se realiza un QA por parte de los desarrolladores y los lideres viendo que bugs salen con el fin de  liberar una version estable la cual sea digna de una presentacion esta se realizara el dia 4 ( 12:00 ) previo a la reunion de entrega (16:00), el dia 6 se socializa con el equipo lo bueno y malo de la entrega y se estudian nuevas tareas planificando asi el trafico de la siguiente semana.

por cada semana se nombra un scrum master el cual de la mano del lider es responsable del sprint. 


##bibloiografia y referencas git

* http://librosweb.es/pro_git/
* http://charliedontcode.com/programacion/2011/11/27/tutorial-de-git-en-espanol.html
* http://blog.xenodesystems.com/2012/05/tutorial-git-desde-cero.html
* http://www.adictosaltrabajo.com/tutoriales/tutoriales.php?* pagina=githubFirstStepsUploadProject
http://www.adictosaltrabajo.com/tutoriales/tutoriales.php?pagina=git-branch-bash
