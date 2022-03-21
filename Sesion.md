# Introducción a la línea de comandos
* * * 

## 1. Introducción
Al igual que las personas nos comunicamos entre nosotras a través de un idioma, las máquinas entienden también un lenguaje. Existen muchos lenguajes de programación, pero nosotros nos centraremos en el lenguaje de **Bash** (Bourne Again Shell), un intérprete de órdenes y lenguaje de programación empleado en distribuciones GNU/Linux. Si te interesa conocer más sobre el origen de Bash, dirígete a este [Link](https://es.wikipedia.org/wiki/Bash).
![bash](Imagenes/bash.jpg)
La razón por la cual trabajamos en esta Shell/lenguaje es que se trata de un lenguaje relativamente sencillo y muy robusto, lo que lo hace muy eficiente a la hora de usar memoria y correr procesos costosos.**Si la velocidad es una preocupación (por ejemplo, cuando estemos manejando ficheros muy grandes, y/o gran cantidad de ficheros), las herramientas UNIX son, normalmente, las que dan la implementación más veloz.** Además, permite crear entornos en los que se pueden usar otros lenguajes (Python, R, Perl, etc.) y, por eso, es un lenguaje básico en el análisis de datos procedentes de (meta)genómica y (meta)transcriptómica. 

Como hemos dicho, Bash es un intérprete de órdenes, por lo que podemos dictarle órdenes concretas para que sean ejecutadas por nuestro ordenador. Las órdenes que recibe Bash, como cualquier lenguaje de programación, son estrictas, es decir, Bash irá interpretando carácter por carácter y si encuentra algo inesperado (algún carácter incorrecto, alguna mayúscula/minúscula cambiada, espacios donde no deben ir, etc.) devolverá un error. Es importante tener esto en cuenta, ya que la mayor parte de los errores que cometemos mientras estamos trabajando en la shell se deben a fallos de escritura.

Una vez que Bash recibe la orden desde nuestro teclado (**la entrada estándar**) y la interpreta correctamente, esta será ejecutada por el ordenador y nos imprimirá una respuesta en nuestra pantalla (**la salida estándar**). De manera muy simplificada, este es el funcionamiento de Bash.
![Entrada-orden-salida](Imagenes/Entrada-orden-salida.png)


## 2. Navegación por el sistema de ficheros
Después de esta introducción, empezarémos con nuestros primeros comandos. Un aspecto básico y fundamental, cuando trabajamos en la shell, es la navegación a través de nuestro sistema de ficheros. Normalmente, accedemos a nuestros documentos usando un explorador de archivos en el que los ficheros (archivos) se encuentran organizados en directorios (carpetas) en un sistema jerárquico, y simplemente haciendo *clic* sobre ellos accedemos al directorio deseado, abrimos documentos, eliminamos ficheros, etc. En la terminal podremos hacer exactamente lo mismo, y, para ello, existen un conjunto de órdenes o comandos que usaremos continuamente.
![sistema-ficheros](Imagenes/sistema-ficheros.png).
### Primeras palabras
Imaginemos que nos despertamos en un lugar desconocido y no podemos ver nada, todo esta negro, como nuetsra terminal. En esta situación, se me ocurriría hacer preguntas como "¿qué hago aquí?" y "¿dónde estoy?". La primera pregunta sólo la podréis responder vosotros, pero para la segunda Bash está a nuestra disposición esperando a que introduzcamos órdenes (lo sabemos por el *prompt* o indicador, que en mi caso es el símbolo $). Para preguntar por nuestra ubicación en nuestro sistema de ficheros usarémos el comando `pwd` que significa *print working directory*. Este comando sirve para saber "dónde estamos". Bash nos devuelve una ruta o *path* en la que se indican los directorios en los que nos encontramos, separados cada uno por barras inclinadas (Directorio1/Directorio2/Directorio3). En mi caso:
```
$ pwd
/c/Users/lihuen
```
Esta ruta nos esta indicando que actualmente me encuentro en un directorio llamado "lihuen", que está dentro de otro llamado "Users", que a su vez está en otro llamado "c". Esta ruta es mi directorio raíz.

¡Éxito! Ya sé dónde estoy. Ahora quiero saber quién soy. Comandos como `whoami` o `id` nos ayudarán a saber más acerca de nosotros.
```
$ whoami
lihuen

$ id
uid=197609(lihuen) gid=197609 groups=197609
```
En resumen, esto sería nuestro nombre y DNI. Ahora que ya sabemos dónde estamos y quienes somos, estaría bien saber si hay alguien con nosotros, aparte de ese ente superior que nos contesta a todas nuestras preguntas. En nuestro caso, estaremos solos la mayoría, pero suele ser común en informática trabajar en servidores externos más potentes que el de nuestro ordenador. En estos casos, no seremos los únicos que usamos el servidor y viene bien saber quién está con nosotros (comando `who`) e, incluso, interactuar con otros usuarios (comando `write`). 

Además de estas preguntas básicas, también podemos preguntar qué hay a nuestro alrededor. Para ello, usamos la orden `ls`, que devolverá por pantalla la lista de ficheros y/o directorios que hay dentro del directorio de trabajo en el que nos encontramos. `ls` también acepta como argumento una ruta o directorio concreto para ver su contenido sin necesidad de desplazarnos hasta dicho directorio para consultarlo.
```
$ ls
 ALEMÁN/                  Documentos/   Imágenes/
'Almacén personal.lnk'*   Escritorio/   desktop.ini

$ ls Escritorio/
'Google Drive.lnk'*      Notas-Lihuen.docx    RStudio.lnk*         desktop.ini
'Microsoft Teams.lnk'*   Proyecto-Tmolitor/   datos_invernadero/  
```
Llegados aquí es bueno apuntar que en Bash las órdenes tienen diferentes opciones que modifican ligeramente la función y nos pueden ser muy útiles cuando queremos hacer cosas concretas. Ejemplo de ello sería la opcion `-l` de la órden `ls`. Usando `ls -l` conseguiremos información detallada de cada directorio o fichero que se encuentre en el directorio de trabajo (permisos, dueño, inodo, tamaño, fecha de última modificación, etc). 
```
$ ls -l
total 77
drwxr-xr-x 1 lihue 197609    0 Nov 28 14:06  ALEMÁN/
-rwxr-xr-x 1 lihue 197609 1140 Mar 21 01:02 'Almacén personal.lnk'*
drwxr-xr-x 1 lihue 197609    0 Mar 19 13:35  Documentos/
drwxr-xr-x 1 lihue 197609    0 Mar 21 07:24  Escritorio/
drwxr-xr-x 1 lihue 197609    0 Mar 19 13:35  Imágenes/
-rw-r--r-- 1 lihue 197609   90 Dec  2 18:13  desktop.ini

```
Para conocer todas las opciones de una función puedes consultar el manual con la orden `man` o pedir ayuda a Bash con la opción `--help`. 
```
$ ls --help
Usage: ls [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).
Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.

Mandatory arguments to long options are mandatory for short options too.
  -a, --all                  do not ignore entries starting with .
  -A, --almost-all           do not list implied . and ..
      --author               with -l, print the author of each file
  -b, --escape               print C-style escapes for nongraphic characters
      --block-size=SIZE      with -l, scale sizes by SIZE when printing them;
                               e.g., '--block-size=M'; see SIZE format below
  -B, --ignore-backups       do not list implied entries ending with ~
  -c                         with -lt: sort by, and show, ctime (time of last
                               modification of file status information);
.
.
.
.
(Muchas cosas)
```
### Primeros pasos
Ahora toca aprender a moverse por el sistema de ficheros. El comando más importante es `cd` (*change directory*). Si introducimos `cd` sin argumento, nos moveremos hacia el directorio raíz, mientras que si le indicamos una ruta, nos llevará al directorio indicado por la ruta. 
```
$ cd 
$ pwd
/c/Users/lihuen

$ cd OneDrive/Escritorio/
$ pwd
/c/Users/lihuen/OneDrive/Escritorio
```
Algo muy útil para movernos por nuestro sistema de ficheros es indicarle a `cd` que nos lleve al directorio padre del directorio de trabajo, es decir, un directorio hacia atrás. Esto lo hacemos con dos puntos. 
```
$ cd ..
$ pwd
/c/Users/lihuen/OneDrive
```
Y si queremos crear un directorio nuevo para trabajar dentro de él, usamos la órden `mkdir` y el nombre del nuevo directorio. Prueba creando un directorio con el nombre Curso-bioinfo. A partir de ahora este será tu directorio de trabajo. Si queremos borrar un directorio usamos la órden `rmdir`, pero esta solo funcionará si el directorio está vacío.

Otras órdenes muy úitiles para trabajar en línea de comandos son `cp`, `mv` y `rm`. Sirven para copiar, mover y borrar ficheros o directorios, respectivamente. La órden `cp` acepta dos argumentos: primero el nombre o ruta del fichero/directorio que pretendemos copiar y luego el nombre y/o la ruta de la copia. Si sólo ponemos el nombre y no la ruta, Bash entiende que el fichero o directorio a copiar se encuentra en el directorio de trabajo y que la copia debe guardarse también en el directorio de trabajo. Vamos a crear un directorio de prueba y copiarlo.
```
$ mkdir PRUEBA
$ cp PRUEBA PRUEBA-copia
cp: -r not specified; omitting directory 'PRUEBA'
```
UPS! Ha habido un error. La razón de este error es que al intentar copiar un directorio, Bash pide que le indiques la opción `-r` (*recursive*), que va a copiar el directorio y recursivamente todo su contenido.
```
$ cp -r PRUEBA PRUEBA-copia
$ ls
'Google Drive.lnk'*  'Microsoft Teams.lnk'*   Notas-Lihuen.docx   PRUEBA/   PRUEBA-copia/  
Proyecto-Tmolitor/   RStudio.lnk*   datos_invernadero/   desktop.ini  
```
Por su parte, el comando `mv` sirve para mover ficheros o directorios de una ubicación a otra. También acepta dos argumentos: el primero es la ruta del fichero/directorio que queremos mover y el segundo es la ruta destino, es decir, la nueva ubicación que queremos (incluyendo el nuevo nombre o el que ya tenía). Esta orden también se usa para cambiar el nombre a los ficheros o directorios.
```
$ mv PRUEBA PRUEBA-copia

$ ls PRUEBA-copia/
PRUEBA/
```
Bueno, como esto era una prueba, vamos a borrar el directorio PRUEBA-copia. `rmdir` no nos deja porque el directorio no esta vacío. Para borrar directorios que no estan vacíos, no hace falta que borres uno por uno los ficheros/directorios que contiene. Basta con indicarle `-r` a rm y no quedará rastro.
```
$rmdir PRUEBA-copia/
rmdir: failed to remove 'PRUEBA-copia/': Directory not empty

$ rm -r PRUEBA-copia/
$ ls
'Google Drive.lnk'*  'Microsoft Teams.lnk'*   Notas-Lihuen.docx   Proyecto-Tmolitor/   RStudio.lnk*   datos_invernadero/   desktop.ini
```
**Cuidado**. Las acciones de copiar o mover cosas en nuestro sistema de ficheros son un arma de doble filo en UNIX, ya que no dispone de comprobación de sobreescritura. Esto conlleva la pérdida de la información que teníamos antes en nuestro fichero/directorio al sobreescribirse la nueva información. Si esto nos pasa, no habrá vuelta atrás. Lo mismo ocurre con la órden `rm`. UNIX no cuenta con una papelera a la que podamos recurrir si hemos borrado algo por error, así que los ficheros que borremos con `rm` se pierden para siempre. 

Si quieres saber más detalles sobre la navegación por el sistema de ficheros puedes echar un vistazo en este [link](https://sospedia.net/shell-bash-gnulinux/).

TRUQUILLOS: autocompletado con el tabulador y acceso a comandos anteriores con las flechas del teclado.

## 3. Redirección de entradas y salidas
Hasta ahora hemos visto cómo darle una orden a Bash  y cómo este las ejecuta devolviendo su respuesta por pantalla (la salida estándar). De hecho, ahora mismo tendrás tu pantalla llena de cosas. Si en algún momento te agobias y quieres limpiar tu pantalla, teclea `clear` y obtendrás paz mental.

Como os decía, la pantalla es la "salida estándar", ya que, a no ser que le indiquemos lo contrario, Bash imprimirá por defecto el resultado en la pantalla. Por su parte, la entrada estándar es nuestro teclado. En Bash, podemos hacer que la salida y la entrada dejen de ser la estándar y sean, por ejemplo, un fichero que le indiquemos.
![Redireccion-entrada-salida](Imagenes/Redireccion-entrada-salida.png)
Pongámoslo en práctica. Imaginemos que queremos guardar el resultado de la orden `ls` en un fichero para consultarlo más tarde. Basta con redirigir el resultado de `ls` a un fichero de texto nuevo con el símbolo 'mayor que' (>). 
```
$ ls > fichero-nuevo.txt

$ ls        (comprobamos que se ha creado)
'Google Drive.lnk'*  'Microsoft Teams.lnk'*   Notas-Lihuen.docx   Proyecto-Tmolitor/   RStudio.lnk*   datos_invernadero/   desktop.ini   fichero-nuevo.txt  

$ cat fichero-nuevo.txt    (leemos el fichero nuevo)
Google Drive.lnk*
Microsoft Teams.lnk*
Notas-Lihuen.docx
Proyecto-Tmolitor/
RStudio.lnk*
datos_invernadero/
desktop.ini
fichero-nuevo.txt
```
En este caso, se creará un fichero nuevo con el resultado de `ls`. Si el archivo fichero-nuevo.txt estuviera creado ya, lo que estaríamos haciendo es sobreescribirlo, es decir, borrar todo su contenido y escribir el contenido nuevo. Si lo que queremos es añadir el resultado de `ls` a algo que ya tenemos escrito en un fichero, debemos redirigir la salida con una doble símbolo mayor que (>>). Vamos a probar añadiendo el resultado de un nuevo comando (`date`) al contenido del fichero-nuevo.txt. 
```
$ date >> fichero-nuevo.txt
```
¿Sabríais decirme qué hace `date`? Para ello, tendríamos que ver lo que hay dentro de nuestro fichero-nuevo.txt. Esto lo haremos con la orden `cat` (*con-cat-enate*), que mostrará por pantalla todo el contenido de nuestro fichero.
```
$ cat fichero-nuevo.txt
Google Drive.lnk*
Microsoft Teams.lnk*
Notas-Lihuen.docx
Proyecto-Tmolitor/
RStudio.lnk*
datos_invernadero/
desktop.ini
fichero-nuevo.txt
Mon Mar 21 08:20:33     2022
```

De la misma forma, podemos redirirgir la entrada para que nuestras órdenes se ejecuten sobre la información de un fichero. Para ello, tendríamos que usar el símbolo menor que (<), pero esto lo pondrémos en práctica más adelante.

## 4. Edición de ficheros 
Una de las partes básicas y más importantes cuando trabajamos en línea de comandos es la edición de ficheros. En este curso veremos dos opciones. La primera de ellas es `cat`, que ya la hemos usado. En realidad, la acción de `cat` simplemente consiste en imprimir por pantalla lo que recibe desde el teclado, de forma que si invocamos `cat` sin argumentos se va a quedar esperando a que le introduzcamos información por nuestro teclado. Cuando le introducimos algo y pulsamos 'enter', `cat` repite todo lo que tecleamos.
```
$cat
lunes
lunes
martes
martes
[[Ctrl+C]] para interrumpir el proceso de forma abrupta y salir de este bucle.
``` 
Si nosotros redirigimos la salida de `cat` a un fichero llamado dias-de-la-semana.txt, escribimos los días de la semana y al teminar pulsamos `Ctrl+D` (interrumpe procesos de forma no abrupta), habremos creado un fichero nuevo con los días de la semana.
```
$cat > dias-de-la-semana.txt
lunes
martes
miercoles
jueves
viernes
sabado
domingo
[[Ctrl+D]]
```
```
$cat dias-de-la-semana
lunes
martes
miercoles
jueves
viernes
sabado
domingo
```
Sin embargo, `cat` es bastante rudimentario y limitado. Por ejemplo, no me dejaría editar el fichero existente para añadir tildes a los días de la semana y, por eso, no podemos decir que `cat` sea un editor de textos. Para ello, es mejor usar verdaderos editores de texto, como `nano`, el editor más usado. `nano` es una herramienta que nos sirve para crear y editar ficheros de texto plano. Los ficheros de texto a los que estamos acostumbrados (ficheros .doc como los de Word) no son ficheros de texto plano, por lo que `nano` no podrá trabajar con ellos. Prueba a crear un fichero-nuevo2.txt con `nano` e inspecciona la interfaz de `nano` para acostumbrarte a ella. Es bastante intuitiva.
```
$nano fichero-nuevo2.txt
```
PARA EMPEZAR A USAR NANO OS DEJO EN EL REPOSITORIO UNA CHULETILLA QUE AYUDARÁ (chuleta-gnu-nano.pdf)

## 5. Filtros básicos y pipelines
Además de para leer y crear ficheros de texto, `cat` se podría considerar el **filtro** más simple de Bash, ya que no hace nada con la información que le pasamos, la deja como estaba. Existen otros filtros muy útiles y que usaremos muy amenudo. Como su propio nombre indica, estos comandos filtran la información que se les pasa por la entrada y devuelven lo que nos interesa. Por ejemplo, el filtro `sort` ordena todas las líneas de un fichero. Vamos a usarlo con nuestro fichero dias-de-la-semana.txt.
```
$sort dias-de-la-semana
domingo
jueves
lunes
martes
miercoles
sabado
viernes
```
`sort`, por defecto, tomará el orden lexicográfico (10<2). Para que ordene números hay que decírselo con `-n`. Otro detalle es que `sort` ordena de menor a mayor. Si queremos que ordene en el otro sentido, debemos pasarle la opción `-r`.
```
```
Hasta ahora, los filtros no parecen tener mucha utilidad, esto podríamos hacerlo perfectamente en una hoja de cálculo o en un editor de texto. Sin embargo, cuando trabajamos con información derivada de la secuenciacion de ADN, solemos trabajar con archivos muy grandes y pesados que tardan en abrirse y hasta la operación más simple como ordenar sus filas sería un dolor. Así que a partir de ahora vamos a trabajar con un ficheros reales. 

En este repositorio disponéis de un archivo `Staphylococcus-aureus.gtf`. Vamos a inspeccionar este fichero con la orden `less` que tiene la ventaja de no cargar todo el contenido del fichero en la memoria para mostrarlo, lo que lo hace muy eficiente en el uso de memoria. 
```
$ less Staphylococcus-aureus.gtf
```
Con `less` podemos inspeccionar cada línea del fichero, incluso hasta la última línea presionando enter. A estas alturas ya habrás podido comprobar el tamaño de nuestro fichero. Presiona "q" (*quit*) para salir de `less`. Sería interesante contar las líneas de este fihcero usando el filtro `wc` (*word-count*), el cual cuenta líneas, palabras y caracteres del fichero pasado como argumento.
```
$ wc Staphylococcus-aureus.gtf
  2780  34554 353205 Staphylococcus-aureus.gtf
```
Si queremos que `wc` nos cuente solo las líneas de nuestro fichero, podemos especificarle la opción `-l`
```
$ wc -l Staphylococcus-aureus.gtf
2780 Staphylococcus-aureus.gtf
```

Otra opción cuando no queremos cargar todo el contenido de un fichero en nuestra pantalla es usar los filtros `head` y `tail` que mostrarán las 10 primeras y las 10 últimas líneas de nuestro fichero, respectivamente.
```
head Staphylococcus-aureus.gtf
##gff-version 3
AP017922.1      FIG     CDS     517     1878    .       +       1       ID=fig|6666666.735992.peg.1;Name=Chromosomal replication initiator protein DnaA
AP017922.1      FIG     CDS     2155    3288    .       +       1       ID=fig|6666666.735992.peg.2;Name=DNA polymerase III beta subunit (EC 2.7.7.7);Ontology_term=KEGG_ENZYME:2.7.7.7
AP017922.1      FIG     CDS     3678    3914    .       +       0       ID=fig|6666666.735992.peg.3;Name=Uncharacterized S4 RNA-binding-domain protein YbcJ
AP017922.1      FIG     CDS     3911    5023    .       +       2       ID=fig|6666666.735992.peg.4;Name=DNA recombination and repair protein RecF
AP017922.1      FIG     CDS     5033    6967    .       +       2       ID=fig|6666666.735992.peg.5;Name=DNA gyrase subunit B (EC 5.99.1.3);Ontology_term=KEGG_ENZYME:5.99.1.3
AP017922.1      FIG     CDS     7004    9664    .       +       2       ID=fig|6666666.735992.peg.6;Name=DNA gyrase subunit A (EC 5.99.1.3);Ontology_term=KEGG_ENZYME:5.99.1.3
AP017922.1      FIG     CDS     9750    10562   .       -       0       ID=fig|6666666.735992.peg.7;Name=ADP-dependent (S)-NAD(P)H-hydrate dehydratase (EC 4.2.1.136);Ontology_term=KEGG_ENZYME:4.2.1.136
AP017922.1      FIG     CDS     10887   11114   .       +       0       ID=fig|6666666.735992.peg.8;Name=Histidine ammonia-lyase (EC 4.3.1.3);Ontology_term=KEGG_ENZYME:4.3.1.3
AP017922.1      FIG     CDS     11115   12401   .       +       0       ID=fig|6666666.735992.peg.9;Name=Histidine ammonia-lyase (EC 4.3.1.3);Ontology_term=KEGG_ENZYME:4.3.1.3
```

```
tail Staphylococcus-aureus.gtf
AP017922.1      FIG     tRNA    2159860 2159934 .       -       .       ID=fig|6666666.735992.rna.73;Name=tRNA-Asn-GTT
AP017922.1      FIG     RNA     2159943 2160064 .       -       .       ID=fig|6666666.735992.rna.74;Name=5S rRNA
AP017922.1      FIG     RNA     2159943 2160064 .       -       .       ID=fig|6666666.735992.rna.74;Name=5S rRNA
AP017922.1      FIG     RNA     2159943 2160064 .       -       .       ID=fig|6666666.735992.rna.74;Name=5S rRNA
AP017922.1      FIG     RNA     2160134 2163058 .       -       .       ID=fig|6666666.735992.rna.75;Name=LSU rRNA
AP017922.1      FIG     RNA     2160134 2163058 .       -       .       ID=fig|6666666.735992.rna.75;Name=LSU rRNA
AP017922.1      FIG     RNA     2160134 2163058 .       -       .       ID=fig|6666666.735992.rna.75;Name=LSU rRNA
AP017922.1      FIG     RNA     2163404 2164968 .       -       .       ID=fig|6666666.735992.rna.76;Name=SSU rRNA
AP017922.1      FIG     RNA     2163404 2164968 .       -       .       ID=fig|6666666.735992.rna.76;Name=SSU rRNA
AP017922.1      FIG     RNA     2163404 2164968 .       -       .       ID=fig|6666666.735992.rna.76;Name=SSU rRNA
```
¿Y si nos interesaran las 20 primeras líneas? Existe la opcion `-n` para indicarle en número de líneas que queremos que `head` o `tail` nos muestren por pantalla.
Inténtalo en tu consola.
```
$head -n20 Staphylococcus-aureus.gtf
```
Si has sido lo suficientemente observador, te habrás fijado en que la tercera columna de nuestro gtf indica el tipo de anotación o *features* (CDS, RNA, etc). Vamos a intentar contar cuántas anotaciones hay de cada tipo. Aquí, el filtro `cut` nos viene al pelo, ya que es ideal para trabajar con datos tabulados como nuestro gtf. `cut`, como su nombre indica, sirve para cortar los datos de nuestro fichero y sacar lo que nos interesa. En realidad, para que cut corte las columnas que nos interesan tenemos que indicarle la opcion `-f` y a continuación (sin espacio) las columnas separadas por comas (2,3) o un rango de columnas (2-3).
```
$cut -f2-3 Staphylococcus-aureus.gtf
```
Por defecto, `cut` va a interpretar el tabulador como el separador de nuestros datos. Pero podemos especificar el que queramos con la opción `-d`. Muy útil cuando trabajamos con csv.

Como orden complementaria a `cut`, existe `paste`. Esta orden toma una línea del fichero y le añade lo que queremos. 

Pero bueno, no nos desviemos. Después de ejecutar `cut -f2-3` os habrán aparecido en pantalla un montón de líneas. Sin embargo, lo que a nosotros nos interesa es el número que hay de cada *feature*. El filtro `uniq` nos ayudará, ya que su función es quitar ocurrencias repetidas, es decir, nos mostrará por pantalla sólo las líneas únicas. Además, con la opción -c nos contará cuántas veces aparece cada línea.
```
cut -f2-3 Staphylococcus-aureus.gtf | uniq -c
      1 ##gff-version 3
   2551 FIG     CDS
      9 FIG     tRNA
     12 FIG     RNA
     24 FIG     tRNA
      3 FIG     RNA
      3 FIG     tRNA
      6 FIG     RNA
    114 FIG     tRNA
      6 FIG     RNA
      6 FIG     tRNA
     12 FIG     RNA
     24 FIG     tRNA
      9 FIG     RNA
```

Como podéis ver, hemos introducido un símbolo nuevo (`|`), la barra vertical o pipe. Este símbolo tiene una función clave: pasar la salida de `cut` como entrada de `uniq`. En informática, la encadenación de funciones de diferentes órdenes para obtener un resultado final deseado se conoce como **pipeline** o tubería. 
![pipeline](Imagenes/pipeline.png)

Sin embargo, nuestra pipeline no cumple del todo la función que queríamos, ya que no nos presenta el recuento correctamente. Esto ocurre porque el filtro `uniq` es un poco limitado y sólo hará bien el recuento si los datos estan ordenados. 
```
$ cut -f2-3 Staphylococcus-aureus.gtf | sort | uniq -c
      1 ##gff-version 3
   2551 FIG     CDS
     48 FIG     RNA
    180 FIG     tRNA
```

¡Conseguido! Como veis, la combinación de filtros puede sernos de mucha utilidad cuando inspeccionamos archivos procedentes de la secuenciación o anotación de genomas. Estos son sólo algunos filtros de los más usados, pero no son los únicos.

## 6. Filtros avanzados
Hasta ahora hemos visto filtros con funciones bastante simples. En este apartado veremos tres filtros con funciones un poco más complejas: `grep`, `awk` y `sed`.

### grep
`grep` es el filtro por exelencia para trabajar en línea de comandos con Bash. Llega a ser hasta 5 veces más rápido que cualquier otro filtro o cualquier otra herramienta de búsqueda parecida que podamos escribir en Python o en R, por ejemplo. Esta rapidez de acción se debe a que `grep` está diseñada específicamente para cumplir una sola función muy muy bien: buscar en un fichero las **líneas** que casan con un **patrón**.

Así, `grep` recibe dos argumentos obligatorios:
- El patrón a buscar (cadena o expresión regular).
- El fichero o ficheros donde queremos que busque el patrón.

Un ejemplo sencillo sería, por ejemplo, buscar las palabras que contengan la letra V en nuestro archivo dias-de-la-semana.txt:
```
$ grep "v" dias-de-la-semana.txt
jueves
viernes
```
Las comillas para definir el patrón no son obligatorias, pero es mejor que acostumbres a hacerlo así, ya que si tenemos que buscar un patrón que contenga espacios, probablemente `grep` sepa interpretarlo bien.

Como cualquier filtro, `grep` también dispone de opciones. Por ejemplo, con la opción `-c` podemos contar las líneas en las que `grep` ha encontrado el patrón y con la opción `-v` le decimos que busque las líneas en las que NO aparece el patrón. Si observas bien nuestro fichero gtf tiene un encabezado `##gff-version 3`, que ha sido considerado como línea cuando ejecutabamos `wc -l`. 
```
wc -l Staphylococcus-aureus.gtf
2780 Staphylococcus-aureus.gtf
```
En realidad, esto no nos interesa ya que el encabezado aporta más bien poco cuando queremos saber el número de anotaciónes que tenemos en el gtf. Vamos a contar ahora todas las líneas de nuestro fichero, sin tener en cuenta el encabezado:
```
$grep -vc "^#" Staphylococcus-aureus.gtf
2779
```

**EXPRESIONES REGULARES**

En este punto de la sesión, nos vemos obligados a hacer un alto en el camino para explicar qué son las **expresiones regulares**, ya que la potencia de `grep` se ve incrementada con el uso de expresiones regulares en sus patrones. De hecho, `grep` viene de *global-regular-expression-print* . Las expresiones regulares no son más que secuencias de caracteres que especifican un patrón de búsqueda en un texto. En realidad se llaman METACARACTERES. Si quieres saber más, puedes visitar este [Link](https://en.wikipedia.org/wiki/Regular_expression#Standards).

Existen muchos metacaracteres que podemos emplear para las expresiones regulares. De hecho, nosotras ya hemos usado una en nuestro patrón `"^#"`. Este símbolo significa "líneas cuyo primer carácter sea #". Aquí te dejo algunas más:

| Metacaracter(es) | Descripción                                                                                                                                                                                            |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| .                | Casa con exactamente un carácter                                                                                                                                                                             |
| [ ]              | Casa con exactamente un carácter de una clase de caracteres                                                                                                                                          |
| ^                | Casa con el principio de una línea o palabra                                                                                                                                   |
| \$                | Casa con el final de una línea o palabra                                                                                                                                                          |
| *                | Casa con **cero o más** ocurrencias del carácter (o grupo de caracteres/expresiones) inmediatamente a la izquierda                                                                                                           |
| ?                | Casa con **cero o una** ocurrencias del carácter (o grupo de caracteres/expresiones) inmediatamente a la izquierda                                                                                                            |
| +                | Casa con **una o más** ocurrencias del carácter (o grupo de caracteres/expresiones) inmediatamente a la izquierda                                                                                                            |
| {n}              | Casa **exactamente con n** ocurrencias del carácter (o grupo de caracteres/expresiones) inmediatamente a la izquierda                                                                                                                      |
| {m,n}            | Casa **m a n** ocurrencias (intervalo cerrado) del carácter (o grupo de caracteres/expresiones) inmediatamente a la izquierda                                                                                                 |
| \|               | Combina expresiones regulares con un OR                                                                                                                                                                 |
| \                | Escapar metacaracteres. Se usa cuando se quiere casar con un metacaracter literalmente. Por ejemplo, `\.` casa con un punto, y `\?` casa con un símbolo de cierre de interrogación.                                                                   |
| ( )              | Usado para agrupar caracteres en una única unidad, a los que se le podrán aplicar modificadores como `*` o `+`. También se usa para delimitar el alcance de una expresión OR, o en expresiones avanzadas para insertar reemplazos. |



En los patrones con expresiones regulares también se pueden introducir rangos de caracteres, es decir, se puede indicar que case, por ejemplo, con todos los números comprendidos entre 1 y 8 o con las letras comprendidas entre a y m poniendo los caracteres entre corchetes y separados con un guión (`[1-8]` `[a-m]`).

Vamos a ver un ejemplo de uso de expresiones regulares con `grep` para entendernos mejor. Cuando hiciste `head` y `tail` sobre el gtf, también pudiste observar que aquellas anotaciones correspondientes a CDS tenían un id.peg, mientras que las anotaciones de RNA o tRNA tienen un id.rna. Imaginemos que queremos contar todas las anotaciones con id.peg en nuestro gtf para comprobar que efectivamente coincide con el recuento de CDS que hicimos anteriormente. Con grep podría ser algo así:
```
$ grep -E -c 'peg.[0-9]{0,9}' Staphylococcus-aureus.gtf
2551
```
Para explicar este ejemplo, iremos paso por paso. Primero analizamos las opciones utilizadas. En este caso he usado la opción `-c` para contar las líneas que coinciden con el patrón (ya la hemos visto) y la opción -E para que grep entienda que le voy a pasar una Expresión Regular Extendida (EREs). Existen las Expresiones Regulares Básicas (BREs), que son las que entiende `grep` por defecto y se limitan a unos pocos metacaracteres (`^`, `$`, `.` y `*`), y existen las EREs que son más modernas y admiten más metacaracteres y nos dan mucho más juego. Como `grep` fue diseñada para BREs, tenemos que indicarle con la opción -E que vamos a usar EREs en nuestro patrón.

Por su parte, el patrón `peg.[0-9]{0,9}` le dice a grep que busque líneas que casen con "peg." seguidas de un número comprendido ente 0 y 9 y que esos números pueden repetirse de 0 a 9 veces, es decir, que busque todas las combinaciones posibles de números hasta nueve digitos. En definitiva, todos los números o, dicho correctamente, todos los peg que hay en nuestras anotaciones. Podemos comprobarlo observando las primeras y últimas líneas:
```
grep -E 'peg.[0-9]{0,9}' Staphylococcus-aureus.gtf | head
AP017922.1      FIG     CDS     517     1878    .       +       1       ID=fig|6666666.735992.peg.1;Name=Chromosomal replication initiator protein DnaA
AP017922.1      FIG     CDS     2155    3288    .       +       1       ID=fig|6666666.735992.peg.2;Name=DNA polymerase III beta subunit (EC 2.7.7.7);Ontology_term=KEGG_ENZYME:2.7.7.7
AP017922.1      FIG     CDS     3678    3914    .       +       0       ID=fig|6666666.735992.peg.3;Name=Uncharacterized S4 RNA-binding-domain protein YbcJ
AP017922.1      FIG     CDS     3911    5023    .       +       2       ID=fig|6666666.735992.peg.4;Name=DNA recombination and repair protein RecF
AP017922.1      FIG     CDS     5033    6967    .       +       2       ID=fig|6666666.735992.peg.5;Name=DNA gyrase subunit B (EC 5.99.1.3);Ontology_term=KEGG_ENZYME:5.99.1.3
AP017922.1      FIG     CDS     7004    9664    .       +       2       ID=fig|6666666.735992.peg.6;Name=DNA gyrase subunit A (EC 5.99.1.3);Ontology_term=KEGG_ENZYME:5.99.1.3
AP017922.1      FIG     CDS     9750    10562   .       -       0       ID=fig|6666666.735992.peg.7;Name=ADP-dependent (S)-NAD(P)H-hydrate dehydratase (EC 4.2.1.136);Ontology_term=KEGG_ENZYME:4.2.1.136
AP017922.1      FIG     CDS     10887   11114   .       +       0       ID=fig|6666666.735992.peg.8;Name=Histidine ammonia-lyase (EC 4.3.1.3);Ontology_term=KEGG_ENZYME:4.3.1.3
AP017922.1      FIG     CDS     11115   12401   .       +       0       ID=fig|6666666.735992.peg.9;Name=Histidine ammonia-lyase (EC 4.3.1.3);Ontology_term=KEGG_ENZYME:4.3.1.3
AP017922.1      FIG     CDS     12779   14065   .       +       2       ID=fig|6666666.735992.peg.10;Name=Seryl-tRNA synthetase (EC 6.1.1.11);Ontology_term=KEGG_ENZYME:6.1.1.11
```
```
grep -E 'peg.[0-9]{0,9}' Staphylococcus-aureus.gtf | tail
AP017922.1      FIG     CDS     2721000 2721200 .       +       0       ID=fig|6666666.735992.peg.2542;Name=Cold shock protein of CSP family
AP017922.1      FIG     CDS     2721318 2721887 .       -       0       ID=fig|6666666.735992.peg.2543;Name=Transcriptional regulator%2C Xre family
AP017922.1      FIG     CDS     2722147 2722542 .       -       1       ID=fig|6666666.735992.peg.2544;Name=hypothetical protein
AP017922.1      FIG     CDS     2722610 2722963 .       -       2       ID=fig|6666666.735992.peg.2545;Name=hypothetical protein
AP017922.1      FIG     CDS     2723459 2724298 .       -       2       ID=fig|6666666.735992.peg.2546;Name=Chromosome (plasmid) partitioning protein ParB-2
AP017922.1      FIG     CDS     2724341 2725060 .       -       2       ID=fig|6666666.735992.peg.2547;Name=16S rRNA (guanine(527)-N(7))-methyltransferase (EC 2.1.1.170);Ontology_term=KEGG_ENZYME:2.1.1.170
AP017922.1      FIG     CDS     2725060 2726937 .       -       1       ID=fig|6666666.735992.peg.2548;Name=tRNA-5-carboxymethylaminomethyl-2-thiouridine(34) synthesis protein MnmG
AP017922.1      FIG     CDS     2727004 2728383 .       -       1       ID=fig|6666666.735992.peg.2549;Name=tRNA-5-carboxymethylaminomethyl-2-thiouridine(34) synthesis protein MnmE
AP017922.1      FIG     CDS     2728527 2728874 .       -       0       ID=fig|6666666.735992.peg.2550;Name=Ribonuclease P protein component (EC 3.1.26.5);Ontology_term=KEGG_ENZYME:3.1.26.5
AP017922.1      FIG     CDS     2729001 2729138 .       -       0       ID=fig|6666666.735992.peg.2551;Name=LSU ribosomal protein L34p
```
O si queremos verlo con mayor claridad, podemos usar la opción `-o` que mostrará sólo la parte de la línea que coincide con el patrón
```
grep -E -o 'peg.[0-9]{0,9}' Staphylococcus-aureus.gtf | head
peg.1
peg.2
peg.3
peg.4
peg.5
peg.6
peg.7
peg.8
peg.9
peg.10
```
```
grep -E -o 'peg.[0-9]{0,9}' Staphylococcus-aureus.gtf | tail
peg.2542
peg.2543
peg.2544
peg.2545
peg.2546
peg.2547
peg.2548
peg.2549
peg.2550
peg.2551
```

Lo cierto es que esta aplicación de `grep` puede parecer sencilla, pero llega a ser muy poderosa. De hecho, `grep` es el pan nuestro de cada día cuando trabajamos en línea de comandos. PARA PROFUNDIZAR MÁS EN EL USO DE METACARACTERES CON GREP OS FACILITO UNA GUÍA MUY ÚTIL [AQUÍ](https://staff.washington.edu/weller/grep.html). 

### awk
Ahora que conocemos un poco el funcionamiento de `grep`, nos damos cuenta de que es un filtro un poco más complejo que los anteriores, pero, aún así sigue siendo relativamente sencillo. En este apartado trataremos de entender el funcionamiento de `awk`, un filtro que permite hacer análisis exploratorio de datos de forma más compleja, ya que permite el uso de expresiones lógicas (x>20). 

En realidad, `awk` es un lenguaje de programación muy pequeñito orientado al procesamiento de textos. Es muy útil para trabajar con datos tabulares y que procesa los datos de entrada fila por fila asignandole la fila leida a un variable `$0`, mientras que todos los campos (columnas) que compongan esta fila seran asignadas a las variables `$1`, `$2`, `$3`, etc. 

`awk` usará la siguientes estructura como argumento: `patron {acción}`, donde el patrón será una expresión lógica (ej.: $1>100) o una expresión regular. Cuando este patrón se evalúe a cierto, o la expresión regular case con el texto en cuestión, `awk` ejecutará la acción. Si omitimos el patrón, `awk` ejecutará la acción en todas las filas, mientras que si omitimos la acción pero especificamos un patrón, `awk` imprimirá todos los campos que casen con el patrón.
```
$ awk '{ print $0 }' Staphylococcus-aureus.gtf
.
.
.
(muchas cosas)
```
Como vemos, `awk` ha ejecutado la acción "mostrar fila" (`print $0`) en todo el gtf, ya que no se le ha indicado ningún patrón. Esto sería cumplir la misma función que `cat`.

También podemos usar `awk` para mostrar ciertas columnas de nuestro fichero:
```
$ grep -v "^#" Staphylococcus-aureus.gtf | awk '{ print $1 " " $4 " " $5 }' | head -n5
AP017922.1 517 1878
AP017922.1 2155 3288
AP017922.1 3678 3914
AP017922.1 3911 5023
AP017922.1 5033 6967
```
Esta misma pipeline que combina `grep` y `awk`, podría realizarse usando solamente `awk`, pero para ello debemos introducir expresiones lógicas. Algunas que acepta `awk` son: `a == b` (a es igual a b), `a != b`	(a no es igual a b), `a < b`	(a es menor que b), `a > b`	(a es mayor que b), `a <= b`	(a es menor o igual a b), `a >= b`	(a es mayor o igual a b), `a ~ b`	(a casa con la expresión regular b), `a !~ b`	(a no casa con la expresión regular b), `a && b`	(operador lógico AND), `a || b`	(operador lógico OR), y `!a`	(negación lógica).
```
$  awk '$0 !~ "^#" { print $1 " " $4 " " $5 }' Staphylococcus-aureus.gtf | head -n5
AP017922.1 517 1878
AP017922.1 2155 3288
AP017922.1 3678 3914
AP017922.1 3911 5023
AP017922.1 5033 6967
```
Sin embargo, hasta ahora, no hemos hecho nada que no hayamos hecho con los otros filtros. Vamos a complicar un poco la cosa. ¿Sabrías decirme qué hace la siguiente línea?
```
$ awk '$0 !~ /^#/ && $5 - $4 >= 200 { print $1 "\t" $4 "\t" $5 "\t" $5-$4}' Staphylococcus-aureus.gtf | head -n5
AP017922.1      517     1878    1361
AP017922.1      2155    3288    1133
AP017922.1      3678    3914    236
AP017922.1      3911    5023    1112
AP017922.1      5033    6967    1934
````
Vamos a desglosar esta línea:
- El patron `$0 !~ /^#/ && $5 - $4 >= 200` le esta indicando a `awk` que 1) analice las líneas que no empiecen por #, es decir, que ignore los encabezados (`$0 !~ /^#/`), 2) que aplique este patrón junto con el siguiente (`&&`), 3) que haga una resta entre la columna 5 y la columna 4 (`$5 - $4`), y 4) que compruebe si el resultado de la resta es mayor o igual que 200 (`>= 200`).
))
- La acción `{ print $1 "\t" $4 "\t" $5 "\t" $5-$4}` le indica a awk, que en todas aquellas líneas que han cumplido los requisitos del patrón, muetsre por pantalla las columnas 1, 4, 5 y el resultado de la resta columna5-columna4, separadas por tabuladores (`\t`).

En resumen, hemos calculado la longitud de las anotaciones y hemos seleccionado aquellas con una longitud mayor a 200 pares de bases. 

### sed
Por último, vamos a ver por encima el funcionamiento de `sed` (*stream-editor*). Esta es una herramienta muy útil para editar textos de forma repetitiva, por ejemplo, cuando queremos adaptar un fichero a un determinado formato y esto requiere la sustitución recursiva de una palabra por otra. 

´sed´ acepta la siguiente estructura como argumento: `s/patrón/reemplazo` + `fichero`

Asi, sed irá leyendo linea por linea y cuando encuentre el patrón lo sustituirá por el reemplazo:
```
$ sed "s/ID/AD/g" Staphylococcus-aureus.gtf | head
##gff-version 3
AP017922.1      FIG     CDS     517     1878    .       +       1       AD=fig|6666666.735992.peg.1;Name=Chromosomal replication initiator protein DnaA
AP017922.1      FIG     CDS     2155    3288    .       +       1       AD=fig|6666666.735992.peg.2;Name=DNA polymerase III beta subunit (EC 2.7.7.7);Ontology_term=KEGG_ENZYME:2.7.7.7
AP017922.1      FIG     CDS     3678    3914    .       +       0       AD=fig|6666666.735992.peg.3;Name=Uncharacterized S4 RNA-binding-domain protein YbcJ
AP017922.1      FIG     CDS     3911    5023    .       +       2       AD=fig|6666666.735992.peg.4;Name=DNA recombination and repair protein RecF
AP017922.1      FIG     CDS     5033    6967    .       +       2       AD=fig|6666666.735992.peg.5;Name=DNA gyrase subunit B (EC 5.99.1.3);Ontology_term=KEGG_ENZYME:5.99.1.3
AP017922.1      FIG     CDS     7004    9664    .       +       2       AD=fig|6666666.735992.peg.6;Name=DNA gyrase subunit A (EC 5.99.1.3);Ontology_term=KEGG_ENZYME:5.99.1.3
AP017922.1      FIG     CDS     9750    10562   .       -       0       AD=fig|6666666.735992.peg.7;Name=ADP-dependent (S)-NAD(P)H-hydrate dehydratase (EC 4.2.1.136);Ontology_term=KEGG_ENZYME:4.2.1.136
AP017922.1      FIG     CDS     10887   11114   .       +       0       AD=fig|6666666.735992.peg.8;Name=Histidine ammonia-lyase (EC 4.3.1.3);Ontology_term=KEGG_ENZYME:4.3.1.3
AP017922.1      FIG     CDS     11115   12401   .       +       0       AD=fig|6666666.735992.peg.9;Name=Histidine ammonia-lyase (EC 4.3.1.3);Ontology_term=KEGG_ENZYME:4.3.1.3

```
Vemos que he sustituido todas los "ID" de mi documento por "AD". El flag `g` del final se añade para que `sed` siga buscando el patrón en una línea aunque lo haya encontrado ya una vez. Así, si tenemos más de un "ID" en una misma fila, se sustituirán todos.

Esto en realidad, no sirve para absolutamente nada, pero puede ser de grán utilidad cuando se trata de adaptar nuestros streams rápidamente para que sean aceptados por otras herramientas.


## 7. Más comandos
Para terminar, os he querido dejar por aquí algunos comandos de gran utilidad cuando estéis trabajando en línea de comandos:


