## [Començant](https://cs50.harvard.edu/x/2023/psets/1/mario/more/#getting-started)

Obriu el [codi VS.](https://cs50.dev/)

Comenceu fent clic dins de la finestra de la vostra terminal i, a continuació, executeu `cd`\-lo sol. Hauríeu de trobar que la seva "indicació" s'assembla a la següent.

Feu clic dins d'aquesta finestra de terminal i, a continuació, executeu

```
wget https://cdn.cs50.net/2022/fall/psets/1/mario-more.zip
```

seguit d'Enter per baixar un ZIP anomenat `mario-more.zip`al vostre espai de codi. Aneu amb compte de no passar per alt l'espai entre `wget`i l'URL següent, o qualsevol altre caràcter!

Ara executa

per crear una carpeta anomenada `mario-more`. Ja no necessiteu el fitxer ZIP, així que podeu executar-lo

i responeu amb "y" seguit d'Enter a la sol·licitud per eliminar el fitxer ZIP que heu baixat.

Ara escriviu

seguit d'Enter per moure't a (és a dir, obrir) aquest directori. La vostra sol·licitud ara hauria de semblar-se a la següent.

Si tot ha tingut èxit, hauríeu d'executar

i vegeu un fitxer anomenat `mario.c`. L'execució `code mario.c`hauria d'obrir el fitxer on escriureu el codi per a aquest conjunt de problemes. Si no, torna sobre els teus passos i mira si pots determinar on t'has equivocat!

## [Món 1-1](https://cs50.harvard.edu/x/2023/psets/1/mario/more/#world-1-1)

Cap a l'inici del món 1-1 a Super Mario Brothers de Nintendo, Mario ha de saltar per sobre de les piràmides de blocs adjacents, segons el següent.

![captura de pantalla de Mario saltant per sobre de les piràmides adjacents](https://cs50.harvard.edu/x/2023/psets/1/mario/more/pyramids.png)

Recreem aquestes piràmides en C, encara que sigui en text, utilitzant hash ( `#`) per a maons, a la següent. Cada hash és una mica més alt que ample, de manera que les piràmides també seran més altes que amples.

```
   #  #
  ##  ##
 ###  ###
####  ####
```

El programa que escriurem es dirà `mario`. I permetem a l'usuari decidir quanta alçada han de ser les piràmides, demanant-los primer un nombre enter positiu entre, per exemple, 1 i 8, inclosos.

A continuació s'explica com pot funcionar el programa si l'usuari entra `8`quan se li demana:

```
$ ./mario
Height: 8
       #  #
      ##  ##
     ###  ###
    ####  ####
   #####  #####
  ######  ######
 #######  #######
########  ########

```

A continuació s'explica com pot funcionar el programa si l'usuari entra `4`quan se li demana:

```
$ ./mario
Height: 4
   #  #
  ##  ##
 ###  ###
####  ####
```

A continuació s'explica com pot funcionar el programa si l'usuari entra `2`quan se li demana:

```
$ ./mario
Height: 2
 #  #
##  ##
```

I així és com podria funcionar el programa si l'usuari entra `1`quan se li demana:

Si l'usuari, de fet, no introdueix un nombre enter positiu entre 1 i 8, inclosos, quan se li demani, el programa hauria de tornar a demanar a l'usuari fins que cooperi:

```
$ ./mario
Height: -1
Height: 0
Height: 42
Height: 50
Height: 4
   #  #
  ##  ##
 ###  ###
####  ####
```

Tingueu en compte que l'amplada del "buit" entre les piràmides adjacents és igual a l'amplada de dos hash, independentment de l'altura de les piràmides.

Obriu el vostre `mario.c`fitxer per implementar aquest problema tal com es descriu!

### [Tutorial](https://cs50.harvard.edu/x/2023/psets/1/mario/more/#walkthrough)

<iframe allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" data-video="" src="https://www.youtube.com/embed/FzN9RAjYG_Q?modestbranding=0&amp;rel=0&amp;showinfo=0" data-ruffle-polyfilled="" scrolling="no" id="iFrameResizer0"></iframe>

### [Com provar el vostre codi](https://cs50.harvard.edu/x/2023/psets/1/mario/more/#how-to-test-your-code)

El vostre codi funciona com s'indica quan introduïu?

-   `-1`(o altres nombres negatius)?
-   `0`?
-   `1`a través de `8`?
-   `9`o altres números positius?
-   lletres o paraules?
-   no hi ha cap entrada, quan només premeu Enter?

També podeu executar el següent per avaluar la correcció del vostre codi mitjançant `check50`. Però assegureu-vos de compilar-lo i provar-lo vosaltres mateixos també!

```
check50 cs50/problems/2023/x/mario/more
```

Executeu el següent per avaluar l'estil del vostre codi amb `style50`.

## [Com enviar](https://cs50.harvard.edu/x/2023/psets/1/mario/more/#how-to-submit)

Al vostre terminal, executeu el següent per enviar el vostre treball.

```
submit50 cs50/problems/2023/x/mario/more
```