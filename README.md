# Simulador de Partículas con Comportamientos

## Descripción General

Construir un sistema de particulas que permita definir tipos de particulas con comportamientos definidos por el usuario para interacción partícula-partícula y partícula-objeto y poder así observar el comportamiento de las mismas con el paso del tiempo.
La idea general es que con este sistema se pudiera implementar algunas de las siguientes ideas:
- Una simulación de hormigas de tipo A y B que busquen comida y se peleen si se ven.
- Los *Slimes Muds* que forman patrones interesantes
- Otra simulación de hormigas pero que en vez de pelear lo que hagan sea colaborar para poder llegar a alguna zona de comida que por alguna casualidad este rodeada de agua y para esto las hormigas deban ir moviendo objetos hacia el agua para poder pasar por arriba de ella (crear un puente)

## Entidades del sistema

El sistema que se simulara constara de los siguientes elementos

### Terreno

Por ahora se tiene pensado que sea una matriz rectangular de pixeles en donde se encontraran el resto de los objetos de la simulación

### Partículas

Las particulas son el centro de este proyecto y la idea es que uno pueda crear varios tipos de particulas y definir para cada una de ellas sus *sensores* y comportamientos en base a esos *sensores*.

#### Sensores

Los sensores son entidades que se les pueden agregar a las partículas para que perciban el entorno (entidades del sistema) y tomen acciones a partir de esto, acciones que serán definidas en el lenguaje especifico del dominio por el usuario que programe las particulas. Por ahora no tenemos bien definido si daremos la flexibilidad de implementar sensores o si los daremos por defecto como parte propia del lenguaje y que el usuario solo pueda cambiar parámetros del mismo para modificar la sensibilidad con que detecta entidades.
Estos sensores pueden devolver propiedades especificas de las entidades que detectan y mas aun, pudieran no detectar todas las entidades, es decir, un sensor puede detectar todas las particulas de tipo A y no detectar a las particulas de tipo B. Ademas podría también detectar solo 3 de 5 propiedades del objeto A

#### Comportamientos

Los comportamientos son unas estructuras que se le definen a las particulas para comportarse de alguna manera especifica con respecto a lo que perciban con los sensores que posean las mismas. En estos comportamientos se pueden usar algoritmos de IA que se hayan programado de antes en el Sistema de Simulación y llamarlos por medio del lenguaje especifico del dominio.
También se tiene pensada la posibilidad de darle capacidad a estas particulas de *agentes lógicos*, proveyéndoles así de un cuerpo de axiomas que serian su base de conocimientos sobre el entorno y ver como se adaptan al medio con el paso del tiempo.

### Objetos inanimados

Los objetos inanimados son todos los objetos que forman parte de la simulación que no son particulas ni el propio terreno.
Estos objetos se definen también en el lenguaje del dominio y se le asignan propiedades que pueden servir para algunos de los comportamientos de las particulas cuando detecten al objeto inanimado por medio de un sensor

## IA

La parte de Inteligencia Artificial la tenemos pensada para que unos cuantos algoritmos sean programados desde el Core del Sistema y que sean invocadas por medio del lenguaje especifico del dominio para ser usadas por las particulas en sus comportamientos. La otra parte es permitir modelar las particulas como *agentes lógicos* (tal como se menciona mas arriba en este Readme) y la otra es aprovecharnos de que unos cuantos algoritmos de IA como es el caso de los *Problemas de Búsqueda* (Vistos en conferencia) tienen algoritmos fijos para encontrar la solución y solamente hay que definir los estados iniciales y el final (objetivo), con funciones de transición de un estado a otro, etc, y permitir construir estos aspectos por parte del usuario mediante el lenguaje que proporcionemos y así permitir solucionar problemas que caigan dentro de esta categoría por parte de una partícula
