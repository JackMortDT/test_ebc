# Control de cambios y control de versiones dev.

1. Se definen las tareas a realizar en conjunto con el equipo de desarrollo.
2. Se selecciona la tarea de mayor relevancia.
3. Se crean las tareas en Jira.
4. Se crea un **branch** acorde al *issue* o incidencia a realizar.
5. El **branch** se crea a partir de los cambios en PROD y si no esta creado este **branch**, se crea a partir del **branch** más actual.
6. Mientras se trabaja en ese issue el desarrollador va haciendo **commits** sobre el **branch** creado.
7. El desarrollador actualiza el **branch** remoto para poder verse por cualquier otro desarrollador.
8. Se sincronzan los cambios en las ramas remotas haciendo uso de los comandos git fetch y git merge.
9. Una vez finalizado el *issue* se mezclan los cambios en **master** para ser probado por los propios desarrolladores.
10. Una vez validado el *issue* correspondiente se mezclan los cambios con el branch de QA.
11. Se solicita al usuario probar los cambios realizados.
12. Una vez validado los cambios por el usuario, se procede a autorizar los cambios para, mezclar finalmente con la rama de producción(PROD).

---

## Ejemplo técnico

```sh
git init
```

![Alt text](/images/init1.png?raw=true)

Se versiona el proyecto por primera vez y a su vez con Git se crea la rama principal **master**

```sh
git checkout -b branch-1
```

![Alt text](/images/init2.png?raw=true)

Se crea una rama a partir de **PROD** o de la rama más actual, en este caso **master**

```sh
git commit
git commit
git commit
```

![Alt text](/images/init3.png?raw=true)

Se realizan los cambios necesarios para solucionar el issue, pueden ser tantos commits como sean necesarios.

```sh
git fetch
```

Se revisa si hay cambios en el **branch** remoto de **master** y si es así se sincroniza, si no, se procede con la mezcla

```sh
git checkout master
git merge branch-1
```

![Alt text](/images/init4.png?raw=true)

Se mezclan los cambios en **master**.

Se continuan realizando los issues correspondientes por el equipo.

![Alt text](/images/init5.png?raw=true)

En este caso se tiene dos tareas que se están trabajando al mismo tiempo por diferentes colaboradores del equipo.

Para poder mezclar los cambios de una rama se tiene que verificar que el objetivo de mezcla, en este caso **master** no tenga cmabios.

```sh
git fetch
```

Une vez hecho esto y viendo que no hay cambios se procede con mezlcar el branch correspondiente, en este caso va a ser el branch-2

![Alt text](/images/init6.png?raw=true)

En el caso de este ejemplo se mezclo el branch-2 en **master**.

Al momento de querer mezclar el branch-3 se va a proceder con verificar si hay cambios en **master**

```sh
git fetch
```

En este caso si hay, por lo que se tendra que rebasar _(git rebase master)_ para colocar nuestros cambios al final de la historia.

```sh
git rebase master
```

![Alt text](/images/init7.png?raw=true)

Los cambios que hay en el branch-3 se pasan arriba de los cambios que hay en **master**, en este caso solo nos pasamos a la rama principal, en este caso **master** y procedemos con la mezcla.

![Alt text](/images/init7.png?raw=true)

La historia continua una linea recta y se puede trabajar de una manera mas organizada.

En el caso de haber mas colaboradores se necesita de una continua comunicación para poder saber si hay o no cambios en los **branch** a mezclar y así poder manejar la historia del trabajo de la mejor manera posible.