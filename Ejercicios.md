
1. Intenta convertir un gtf a bed. (Explicar qué son los bed)
También, vamos a poder usar expresiones regulares con grep. Por ejemplo aquí vamos a sacar un .gtf en formato .bed:
```
abenito@cpg3:~/sesion-iii/gtfs$ grep -v "^#" Drosophila_melanogaster.BDGP6.28.102.gtf | cut -f 1,4,5 | head
3R	567076	2532932
3R	567076	2532932
3R	567076	567268
3R	835376	835491
3R	835378	835491
3R	835378	835380
3R	869486	869548
3R	869486	869548
3R	895786	895893
3R	895786	895893
```
