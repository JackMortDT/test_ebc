# Control de cambios y control de versiones dev.

1. Se definen las tareas a realizar en conjunto con el equipo de desarrollo.
2. Se selecciona la tarea de mayor relevancia.
3. Se crean las tareas en Jira.
4. Se crea un **branch** acorde al *issue* o incidencia a realizar.
5. El **branch** se crea a partir de los cambios en PROD y si no esta creado este **branch**, se crea a partir del **branch** más actual.
6. Mientras se trabaja en ese issue el desarrollador va haciendo **commits** sobre el **branch** creado.
7. El desarrollador actualiza el **branch** remoto para poder verse por cualquier otro desarrollador.
8. Se sincronzan los cambios en las ramas remotas haciendo uso de los comandos git fetch y git merge.
9. Una vez finalizado el *issue* se mezclan los cambios en master para ser probado por los propios desarrolladores.
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

Se revisa si hay cambios en el **branch** remoto de master y si es así se sincroniza, si no, se procede con la mezcla

```sh
git checkout master
git merge branch-1
```

![Alt text](/images/init4.png?raw=true)

Se mezclan los cambios en master.

Se continuan realizando los issues correspondientes por el equipo.

![Alt text](/images/init5.png?raw=true)

En este caso se tiene dos tareas que se están trabajando al mismo tiempo por diferentes colaboradores del equipo.

Para poder mezclar