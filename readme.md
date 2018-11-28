# Ejercicio 1

## ¿Qué comando utilizaste en el paso 11? ¿Por qué?

> ```git --hard reset HEAD~1```

El comando reset mueve los punteros HEAD y styled al commit anterior. Con el 
modificador --hard le indicamos a Git que queremos que refleje los cambios 
en nuestro *working directory*.

## ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?

El commit que queremos rehacer, debido a la navegabilidad del grafo, se 
encuentra por encima de nuestros punteros HEAD y style. Así que, para poder 
acceder a él nuevamente, tendremos que identificar su hash. Para ello 
usamos:

> ```git reflog```

Una vez identificado el hash del commit, podemos volver a posicionar los 
punteros sobre él mediante el comando:

>```git reset <hash_del_commit>```

Finalmente, dado que en primer lugar hemos deshecho el commit con el 
modificador --hard, los cambios se han reflejado en el working copy. Por lo 
tanto, al "rehacer" el último commit hay que descartar los cambios en el 
*stage*. Lo logramos con:

>git checkout -- git-nuestro.md

## El marge del paso 13, ¿causó algún conflicto? ¿Por qué?

No, ninguno. Styled absorbe a master. En terminos de navegabilidad, master 
está por debajo de styled, por lo que a styled no le supone ningún cambio 
absorber a master. Todos los commits de master ya eran visibles para styled 
antes del merge.

## El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?

Sí, hay conflictos. El archivo en el branch actual (styled) difiere del 
archivo en el branch a absorber (htmlify), y además el merge no se puede 
completar mediante *fast-forward*. Por lo tanto, git nos deja 
decidir qué cambios conservar y cuales descartar.

## El merge en el paso 21, ¿Causó algún conflicto? ¿Por qúé?

No. Mergear master con styled no genera conflictos porqué se lleva a cabo 
mediante *fast-forward*.

## ¿Qué comandos utilizaste en el paso 25?

>```git log --graph```

## El merge del paso 26, ¿podría ser fast forward? ¿Por qué?

Sí, porqué en el momento de realizar el commit de title en master nos 
encontramos con que la rama master está en la misma línea que la rama title.

## Comandos del paso 27

>```git reset HEAD~1```

Al estar deshaciendo un merge que se ha llevado a cabo de forma recursiva 
(sin fast forward), lo podemos deshacer con el comando reset, indicándole 
que queremos acceder al commit inmediatamente anterior.

Para no perder los cambios en el working copy nos abstenemos de utilizar el 
modificador ```--hard```.

## Comandos paso 28

Al deshacer el merge sin modificar el working copy nos encontramos con que 
el contenido del archivo no coincide con el contenido que el commit 
esperaría encontrar. Éstas diferencias se marcan como modificaciones que 
tendríamos que añadir y commitear. Para deshacernos de ellas, usamos el 
comando:

>```git checkout -- git-nuestro.md```

## Comandos paso 29

Dado que no estamos sobre ella, para eliminar la rama title nos valemos del 
comando:

>```git branch -D title```

Cabe indicar que git nos fuerza a usar "D" para asegurarse que sabemos qué 
estamos haciendo, porqué al eliminar la rama title se quedará un commit 
"inaccesible".

## Comandos paso 30

Primero queremos averiguar el hash que corresponde al commit generado al 
mergear las branches anteriormente. Esto lo logramos con:

>```git reflog | grep merge```

El uso de grep facilita la lectura del reflog, pero no es obligada. A 
continuación, usamos el siguiente comando para volver a colocar la branch 
master en el commit del merge

>```git reset <hash_del_commit>```

## Comandos paso 32

Primero averiguamos el hash del primer commit con:

>```git log```

Va a ser el de más abajo.

Con el comando:

>```git checkout <hash_del_commit>```

Colocamos el puntero HEAD sobre el mismo.

## Comandos paso 33

Con el comando:

>```git reflog```

Identificamos el hash del commit. Lo podemos identificar facilmente porqué 
el mensaje del commit que buscamos es "Añadimos un título al archivo 
git-nuestro.md". A continuación, nos colocamos sobre el con:

>```git checkout <hash_del_commit>
