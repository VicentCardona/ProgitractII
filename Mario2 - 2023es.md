## [Empezando](https://cs50.harvard.edu/x/2023/psets/1/mario/more/#getting-started)

Abra el [código VS.](https://cs50.dev/)

Comience haciendo clic dentro de la ventana de su terminal, luego ejecútelo `cd`solo. Debería encontrar que su "mensaje" se parece al siguiente.

Haga clic dentro de esa ventana de terminal y luego ejecute

```
wget https://cdn.cs50.net/2022/fall/psets/1/mario-more.zip
```

seguido de Enter para descargar un ZIP llamado `mario-more.zip`en su codespace. ¡Tenga cuidado de no pasar por alto el espacio entre `wget`la siguiente URL o cualquier otro carácter!

Ahora ejecuta

para crear una carpeta llamada `mario-more`. Ya no necesitas el archivo ZIP, así que puedes ejecutar

y responda con "y" seguido de Enter cuando se le solicite para eliminar el archivo ZIP que descargó.

Ahora escribe

seguido de Enter para moverse a (es decir, abrir) ese directorio. Su mensaje ahora debería parecerse al siguiente.

Si todo fue exitoso, debes ejecutar

y ver un archivo llamado `mario.c`. La ejecución `code mario.c`debería abrir el archivo donde escribirá su código para este conjunto de problemas. Si no, vuelve sobre tus pasos y ve si puedes determinar dónde te equivocaste.

## [Mundial 1-1](https://cs50.harvard.edu/x/2023/psets/1/mario/more/#world-1-1)

Hacia el comienzo del Mundo 1-1 en Super Mario Brothers de Nintendo, Mario debe saltar sobre pirámides de bloques adyacentes, según lo siguiente.

![Captura de pantalla de Mario saltando sobre pirámides adyacentes.](https://cs50.harvard.edu/x/2023/psets/1/mario/more/pyramids.png)

Let’s recreate those pyramids in C, albeit in text, using hashes (`#`) for bricks, a la the below. Each hash is a bit taller than it is wide, so the pyramids themselves will also be taller than they are wide.

```
   #  #
  ##  ##
 ###  ###
####  ####
```

The program we’ll write will be called `mario`. And let’s allow the user to decide just how tall the pyramids should be by first prompting them for a positive integer between, say, 1 and 8, inclusive.

Here’s how the program might work if the user inputs `8` when prompted:

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

Here’s how the program might work if the user inputs `4` when prompted:

```
$ ./mario
Height: 4
   #  #
  ##  ##
 ###  ###
####  ####
```

Here’s how the program might work if the user inputs `2` when prompted:

```
$ ./mario
Height: 2
 #  #
##  ##
```

And here’s how the program might work if the user inputs `1` when prompted:

If the user doesn’t, in fact, input a positive integer between 1 and 8, inclusive, when prompted, the program should re-prompt the user until they cooperate:

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

Observe que el ancho del "espacio" entre pirámides adyacentes es igual al ancho de dos hashes, independientemente de la altura de las pirámides.

¡Abra su `mario.c`archivo para implementar este problema como se describe!

### [Tutorial](https://cs50.harvard.edu/x/2023/psets/1/mario/more/#walkthrough)

<iframe allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" data-video="" src="https://www.youtube.com/embed/FzN9RAjYG_Q?modestbranding=0&amp;rel=0&amp;showinfo=0" data-ruffle-polyfilled="" scrolling="no" id="iFrameResizer0"></iframe>

### [Cómo probar su código](https://cs50.harvard.edu/x/2023/psets/1/mario/more/#how-to-test-your-code)

¿Su código funciona según lo prescrito cuando ingresa?

-   `-1`(u otros números negativos)?
-   `0`?
-   `1`¿ a través de `8`?
-   `9`u otros números positivos?
-   ¿letras o palabras?
-   ¿No hay entrada alguna, cuando solo presionas Enter?

También puede ejecutar lo siguiente para evaluar la exactitud de su código usando `check50`. ¡Pero asegúrese de compilarlo y probarlo usted mismo también!

```
check50 cs50/problems/2023/x/mario/more
```

Ejecute lo siguiente para evaluar el estilo de su código usando `style50`.

## [Cómo enviar](https://cs50.harvard.edu/x/2023/psets/1/mario/more/#how-to-submit)

En su terminal, ejecute lo siguiente para enviar su trabajo.

```
submit50 cs50/problems/2023/x/mario/more
```