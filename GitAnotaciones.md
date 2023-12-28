# Anotaciones de Git

https://www.youtube.com/watch?v=3GymExBkKjE&t=3674s

Inicialmente debemos instalar Git y luego desde la terminal comenzar a crear una carpeta en una dirección específica.

Luego de crear un fichero determinado debemos crear en esa dirección un control de versiones determinado.

## Creación de un control de versiones Git

Una vez que estemos en una carpeta determinada colocamos el comando:
```
git init
```
A partir de ahora ese directorio va a funcionar como un repositorio

### Add

Para añadir a los fichero al repositorio en si debo usar 

```
git add NOMBRE DEL FICHERO
```

Se recomienda usar 


```
git add .
```

De esta forma se refresca todo

### Commit

Debo de alguna forma crear un registro de los cambios que hice en ese fichero en el que estoy trabajando, por lo que uso commits, este si o si debe ser creado con comentarios

```
git commit -m "Comentario 1"

```

Y luego me mostrará la cantidad de cambios y el identificador de ese commit

Para saber quién hizo los commits debo colocar 

```
git log
```

Y veré todo el registro

*SIEMPRE* que querramos crear más ficheros y agregarlos a nuestro repositorio de Git deberemos usar _add_ y _commit_

Si quiero volver a como estaba antes

```
git checkout
```

Me permite volver a un punto determinado



```
git log --graph 

```
Puedo ver todo lo referido a commits en cada rama

Se pueden crear comandos en 1:04:00

Puedo ignorar algunos ficheros de mi repositorio por ejemplo

```
touch .gitignore

```
Luego cuando se crea ese fichero deberemos agregar el nombre de otros ficheros de la siguiente forma:

**/.nombre_del_fichero

Luego se agrega con add

```
git add .gitignore
```

Se commitea y listo

## Ver diferencias entre una versión anterior y la actual

Se agrega el comando 

```
git diff
```


## Volver a un commit determinado

Deberemos usar el comando de checkout pero con la identificación de del commit (hacemos git log y copiamos esa dirección)

## Borrar

Si deseo borrar commits y comenzar desde un commit en particular uso el hard reset

```
git reset --hard "dirección"
```

Y si luego me arrepiento

Hago lo mismo pero en vez de esa dirección uso otra más actual
Para conocer esas direcciones si no las recuerdo debo usar

```
git reflog
```

## Crear ramas

Siempre que creemos ramas hacemos una bifuración del camino de rama main, básicamente cuando quiero hacer una version con mejoras que no quiero que se mezcle con main

La rama la creo con 

```
git branch login
```

Si quiero moverme a esa rama uso switch

```
git switch login
```

Es *IMPORTANTE* entender que cuando trabajamos en una rama, creamos ficheros u hacemos cambios y luego camibamos a otra rama esos cambios NO aparecerán ya que fueron realizados en otra rama originalmente.

## Merge

Si deseo combinar los datos de una rama con otra debo usar el comando merge, esto es si tengo una rama coloco

```
git merge rama2
```
Entonces la rama 1 tendrá los cambios de la rama 2 porque lo mergee

## Conflictos

Existe una situación llamada "conflicto", esta sucede cuando en 2 ramas (o más) se toca el MISMO archivo con las MISMAS líneas de código, y ambos cambios son commiteados para luego ser MERGEADOS, por lo que Git nos dice: "Esto no es posible" pero nos deja elegir con qué versión nos quedamos.

Se mostrarán ambas versiones, dejaré una, deberé colocar ADD y luego COMMIT.

## Stash

Puede pasar que yo esté desarrollando un código en una rama y me piden que cambie de rama para arreglar un error, pero Git NO me deja cambiar de rama (con Switch) sin hacer commit, el tema es que yo NO deseo hacer commit ya que ese código que estaba desarrollando no está terminado, ahí es donde debo hacer STASH

```
git stash
```

Y luego de esto puedo hacer switch cambiando de rama porque el stash guarda una copia temporal de mis modificaciones (sin hacer el commit)

Una vez que termino lo qu deseo hacer en la rama que yo cambié lo que debo hacer es

```
git switch RAMA_ANTERIOR
```

Y luego

```
git stash pop
```

Si NO hago esto no levanto los cambios y solo me aparecerá lo que tenía desde el último commit de esa rama.

Y para ELIMINAR eso guardado en el stash uso

```
git stash drop
```

## Eliminación de ramas

```
git branch -d NOMBRE_DE_RAMA
```

NUNCA se elimina totalmente, puedo moverme a otros commits y recuperar la rama, pero en el flujo principal no aparecerá por comodidad.

## Github

Crear cuenta y repositorio y una vez alli verificamos de instalar para trabajar con claves SSH

https://www.youtube.com/watch?v=g0ZV-neSM7E

Una vez creado todo (incluido la clase SSH en Github) se procede a clonar los respositorios copiando la forma SSH y colocando esto en la consola de Git Bash

```
git clone "eso que copiamos del repo de Github"
```

