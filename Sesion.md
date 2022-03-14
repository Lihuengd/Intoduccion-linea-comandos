# Introducción a la línea de comandos
* * * 

## 1. Introducción
Al igual que las personas nos comunicamos entre nosotras a través de un idioma, las máquinas entienden también un lenguaje. Existen muchos lenguajes de programación, pero nosotros nos centraremos en el lenguaje de **Bash** (Bourne Again Shell), un intérprete de órdenes y lenguaje de programación empleado en distribuciones GNU/Linux. Si te interesa conocer más sobre el origen de Bash, dirígete a este [Link](https://es.wikipedia.org/wiki/Bash).
![bash](Imagenes/bash.jpg)
La razón por la cual trabajamos en esta Shell/lenguaje es que se trata de un lenguaje relativamente sencillo y muy robusto, lo que lo hace muy eficiente a la hora de usar memoria y correr procesos costosos. Además, permite crear entornos en los que se pueden usar otros lenguajes (Python, R, Perl, etc.), y por eso es un lenguaje básico en el análisis de datos procedentes de (meta)genómica y (meta)transcriptómica.

Como hemos dicho, Bash es un intérprete de órdenes, por lo que nos va a permitir dictarle órdenes concretas para que sean ejecutadas por nuestro ordenador. Las órdenes que recibe Bash, como cualquier lenguaje de programación, son estrictas, es decir, Bash irá interpretando caracter por caracter y si encuentra algo inesperado (algún caracter incorrecto, alguna mayuscula/minuscula cambiada, espacios donde no deben ir, etc) devolverá un error. Es importante tener esto en cuenta, ya que la mayor parte de los errores que cometemos mientras estamos trabajando en la shell se deben a fallos de escritura.

Una vez que Bash recibe la órden desde nuestro teclado (entrada estándar) y la interpreta correctamente, esta será ejecutada por el ordenador y nos imprimirá una respuesta en nuestra pantalla (salida estándar). De manera muy simplificada, este es el funcionamiento de Bash.
![Entrada-orden-salida](Imagenes/Entrada-orden-salida.png)


## 2. Navegación por el sistema de ficheros
Después de esta introducción, empezarémos con nuestros primeros comandos. Un aspecto básico y fundamental cuando trabajamos en la shell, es la navegación a través de nuestro sistema de ficheros. Normalmente, accedemos a nuestros documentos usando un explorador de archivos en el que los ficheros (archihvos) se encuentran organizados en directorios (carpetas) en un sistema jerarquico, y simplemente haciendo *clic* sobre ellos accedemos al directorio deseado, abrimos documentos, eliminamos ficheros, etc. En la terminal podremos hacer exactamente lo mismo, y para ello existen un conjunto de órdenes o comandos que usaremos continuamente.

Imaginemos que nos despertamos en un lugar desconocido y no podemos ver nada, todo esta negro, como nuetsra terminal. En esta situación, se me ocurriría hacer preguntas como ¿qué hago aquí? y ¿dónde estoy?. La primera pregunta sólo la podréis responder vosotros, pero para la segunda Bash esta a nuestra disposición esperando a que introduzcamos órdenes (lo sabemos por el *prompt* o indicador, que en mi caso es el símbolo $). Para preguntar por nuestra ubicación en nuestro sistema de ficheros usarémos el comando `pwd` que significa *print working directory*. Este comando sirve para saber "dónde estamos". Bash nos devuelve una ruta o *path* en la que se indican los directorios en los que nos encontramos, separados cada uno por barras inclinadas (Directorio1/Directorio2/Directorio3). En mi caso:
```
$ pwd
/c/Users/lihuen
```
Esta ruta nos esta indicando que actualmente me encuentro en un directorio llamado "lihuen", que esta dentro de otro llamaso "Users", que a su vez esta en otro llamado "c" que se encuentra alojado en el directorio raíz.

Exito! Ya sé dónde estoy. Ahora quiero saber quién soy. Comandos como `whoami` o `id` nos ayudarána  saber más acerca de nosotros.
```
$ whoami
lihuen

$ id
uid=197609(lihuen) gid=197609 groups=197609
```
En resúmen, esto sería nuestro nombre y DNI. Ahora que ya sabemos dónde estamos y quienes somos, estaría bien saber si hay alguien con nosotros, aparte de ese ente superior que nos contesta a todas nuestras preguntas. En nuestro caso, estarémos sólos la mayoría, pero suele ser común en informática trabajar en servidores externos más potentes que el de nuestro ordenador. En estos casos, no serémos los únicos que usamos el servidor y viene bien saber quién esta con nosotros (comando `who`) e, incluso, interactuar con otros usuarios (comando `write`). 

Además de estas preguntas básicas, también podemos preguntar quñé hay a nuestro alrededor con la órden `ls`.
## 3. Redirección de entradas y salidas

## 4. Filtros básicos

## 5. Filtros avanzados

## 6. Virtual Box

