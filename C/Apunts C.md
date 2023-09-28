# Apunts C

## Introducció

- Recorda que les màquines només entenen binaris. On els humans escriuen `codi font`, una llista d'instruccions per a l'ordinador que és llegible pels humans, les màquines només entenen el que ara podem anomenar `codi màquina`. Aquest codi màquina és un patró d'uns i zeros que produeix un efecte desitjat.
- Resulta que podem convertir .source code. en `machine code` utilitzant una peça molt especial de programari anomenada `compilador`. Avui us presentarem un compilador que us permetrà convertir el codi font en el llenguatge de programació `C` en codi màquina.
- Avui, a més d'aprendre com programar, aprendràs com escriure un bon codi.
- El codi es pot avaluar en tres eixos:
 * En primer lloc, **correcció** es refereix a «executa el codi com es pretén?» 
* En segon lloc, **disseny** es refereix a “com de bé està dissenyat el codi?”
* Finalment, **estil** es refereix a "com d'estèticament agradable i coherent és el codi?"

## Hola mon!

- El compilador que s'utilitza per a aquest curs és *Visual Studio Code*, afectuosament anomenat , al qual es pot accedir mitjançant el mateix URL, o simplement com \*VS Code.\*
- Una de les raons més importants que utilitzem el VS Code és que té tot el programari necessari per al curs ja precarregat. Aquest curs i les instruccions van ser dissenyades pensant en VS Code. 
- Podeu obrir el codi VS a [cs50.dev](https://cs50.dev/).
- El compilador es pot dividir en diverses regions:

![IDE](https://cs50.harvard.edu/x/2023/notes/1/cs50Week1Slide017.png "IDE") Observeu que hi ha un  *explorador d'arxius* al costat esquerre on trobareu els vostres fitxers. A més, tingueu en compte que hi ha una regió al mig anomenada *text editor* on podreu editar el vostre programa. Finalment, hi ha una `interfície de línia d'ordres`, coneguda com a *CLI*, *command line* o *terminal*, on podem enviar ordres a l'ordinador en el núvol.

- Podem construir el vostre primer programa en C escrivint `code hello.c` a la finestra del terminal. Observeu que hem abaixat deliberadament tot el nom del fitxer i inclòs l'extensió `.c`. Llavors, a l'editor de text que apareix, escriviu el codi de la manera següent:

```C
#include <stdio.h>

int main(void)
{
    printf("hola, món\n");
}
```

Tingueu en compte que cada caràcter anterior serveix un propòsit. Si l'escriviu incorrectament, el programa no s'executarà.
- En fer clic de nou a la finestra del terminal, podreu compilar el codi executant `make hello`. Observeu que estem ometent `.c`. `make` és un compilador que cercarà el nostre fitxer `hello.c` i el convertirà en un programa anomenat `hello`. Si l'execució d'aquesta ordre no produeix errors, podeu continuar. Si no, comproveu el codi per assegurar-vos que coincideixi amb l'anterior.
- Ara, escriviu `./hello` i el vostre programa s'executarà dient `hello, world`.
- Ara, obre el  explorerfile explorer. a l'esquerra. Observareu que ara hi ha un fitxer anomenat `hello.c` i un altre anomenat `hello`. El compilador pot llegir `hello.c`: és on s'emmagatzema el codi. `hello` és un fitxer executable que podeu executar, però el compilador no el pot llegir.
- Mirem el nostre codi amb més cura:

```C
#include <stdio.h>

int main(void)
{
    printf("hola, món\n");
}
```

Tingueu en compte que el nostre codi es ressalta mitjançant el ressaltat de la sintaxi.


## Funcions

- A Scratch, hem utilitzat el bloc `say` per mostrar qualsevol text a la pantalla. De fet, en C, tenim una funció anomenada `printf` que fa exactament això.
- Tingueu en compte que el nostre codi ja invoca aquesta funció:

```C
printf("hola, món\n");
```

Tingueu en compte que s'anomena la funció printf. L'argument passat a printf és «hola, món\\n». La declaració de codi es tanca amb un `;`.

- Un error comú en la programació C és l'omissió d'un punt i coma. Modifica el codi de la manera següent:

```C
#include <stdio.h>

int main(void)
{
    printf("hola, món\n")
}
```

Observeu que el punt i coma ja no existeix.

- A la finestra del terminal, executeu `make hello`. Ara es trobaran amb nombrosos errors! Col·loqueu el punt i coma de nou en la posició correcta i torneu a executar `make hello`, els errors desapareixeran.
- Observeu també el símbol especial `\n` en el codi. Proveu d'eliminar aquests caràcters i tornar a fer el vostre programa executant `make hello`. Escriu `./hello` a la finestra del terminal, com ha canviat el vostre programa?
- Restaura el programa al següent:

```C 
#include <stdio.h>

int main(void)
{
    printf("hola, món\n");
}
```

Observeu que s'ha restaurat el punt i coma i `\n`.

- La declaració a l'inici del codi `#include <stdio.h>` és una ordre molt especial que diu a la compilació que voleu utilitzar les capacitats de  thelibrary_ anomenades `stdio.h`. Permet, entre moltes altres coses, utilitzar la funció `printf`. Podeu llegir sobre totes les capacitats d'aquesta biblioteca als [manuals](https://manual.cs50.io/).
- Resulta que CS50 té la seva pròpia biblioteca anomenada `cs50.h`. Utilitzem aquesta biblioteca al vostre programa.

## [Variables](https://cs50.harvard.edu/x/2023/notes/1/#variables)

- Recordeu que a Scratch, vam tenir l'habilitat de preguntar a l'usuari "Què és el vostre nom?" i dir "hola" amb aquest nom afegit.
- En C, podem fer el mateix. Modifica el codi de la manera següent:

```C
#include <cs50.h>
#include <stdio.h>

int main(void)
{
string resposta = get_string("Quin és el vostre nom? ");
printf("hola, %s\n", resposta);
}
```

Tingueu en compte que `#include <cs50.h>` s'ha afegit a la part superior del codi. La funció `get_string` s'utilitza per a obtenir una cadena de l'usuari. Després, la variable `answer` es passa a la funció `printf`. `%s` li diu a la funció `printf` que es prepari per rebre una `string`.

- `answer` és un lloc de retenció especial que anomenem .variable.. `answer` és del tipus `string` i pot contenir qualsevol cadena dins. Hi ha molts .tipus de dades_, com `int`, `bool`, `char` i molts altres.
- Executant `make hello` de nou a la finestra del terminal, podreu executar el programa escrivint `./hello`. El programa ara demana el vostre nom i després ho diu amb el vostre nom adjunt.

## [Condicionals](https://cs50.harvard.edu/x/2023/notes/1/#conditionals)

- Un altre bloc de construcció que vas utilitzar a Scratch era el de .conditionals.. Per exemple, és possible que vulgueu fer una cosa si x és més gran que y. A més, potser voldreu fer alguna cosa més si no es compleix aquesta condició.
- A la finestra del terminal, escriviu `code compare.c` i escriviu el codi de la manera següent:

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
int x = get =int("Què és x? ");
int y = get =int("Què és y? ");

if (x < y)
{
printf("x és més petit que y\n");
}
}
```

Observeu que creem dues variables, una `int` o un enter anomenat `x` i una altra anomenada `y`. Els valors d'aquests estan poblats utilitzant la funció `get_int`.

- Podeu executar el codi executant `make compare` a la finestra del terminal, seguit de `./compare`. Si obteniu algun missatge d'error, comproveu el codi per als errors.
- Podem millorar el vostre programa codificant de la manera següent:

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
int x = get =int("Què és x? ");
int y = get =int("Què és y? ");

if (x < y)
{
printf("x és més petit que y\n");
}
else if (x > y)
{
printf("x és més gran que y\n");
}
else
{
printf("x és igual que y\n");
}
}
```

Observeu que ara es tenen en compte tots els resultats potencials.

- Pots tornar a fer i executar el teu programa i provar-lo.
- Considerant un altre tipus de dades anomenat `char`, podem iniciar un programa nou escrivint `code agree.c` a la finestra del terminal. A l'editor de text, escriviu el codi de la manera següent:

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
// Demana a l'usuari que accepti
char c = get =char("Esteu d'acord? ");

// Comprova si hi ha acord
si (c == 'Y' ) c == 'y')
{
printf("D'acord.\n");
}
altrament si (c == 'N' ) c == 'n')
{
printf("No acordat.\n");
}
}
```

Tingueu en compte que les cometes simples s'utilitzen per a caràcters individuals. A més, cal tenir en compte que `==` assegura que alguna cosa .és igual_ a una altra cosa, on un únic signe igual tindria una funció molt diferent en C. Finalment, cal tenir en compte que `=` significa efectivament .or..

- Podeu provar el codi escrivint `make agree` a la finestra del terminal, seguit de `./agree`.

## [Loops](https://cs50.harvard.edu/x/2023/notes/1/#loops)

- També podem utilitzar el bloc de construcció de bucles de Scratch en els nostres programes C.
- A la finestra del terminal, escriviu `code meow.c` i escriviu el codi de la manera següent:

```
#include <stdio.h>

int main(void)
{
printf("meow\n");
printf("meow\n");
printf("meow\n");
}
```

Fixeu-vos que això fa el que es pretenia però té l'oportunitat de dissenyar millor.

- Podem millorar el nostre programa modificant el codi de la manera següent:

```
#include <stdio.h>

int main(void)
{
int i = 0;
while (i ) 3)
{
printf("meow\n");
i++;
}
}
```

Observeu que creem una `int` anomenada `i` i li assignem el valor `0`. Després, crearem un bucle `mentre` que durarà tant com `i , 3`. Llavors, el bucle corre. Cada vegada que s'afegeix `1` a `i` utilitzant l'expressió `i++`.

- De la mateixa manera, podem implementar una mena de compte enrere modificant el nostre codi de la manera següent:

```
#include <stdio.h>

int main(void)
{
int i = 3;
while (i ) 0)
{
printf("meow\n");
i--;
}
}
```

Observeu com el nostre comptador `i` s'inicia a `3`. Cada vegada que s'executa el bucle, es reduirà el comptador en `1`. Un cop el comptador sigui inferior a zero, aturarà el bucle.

- Podem millorar encara més el disseny utilitzant un bucle `for`. Modifica el codi de la manera següent:

```
#include <stdio.h>

int main(void)
{
for (int i = 0; i ; 3; i++)
{
printf("meow\n");
}
}
```

Observeu que el bucle `for` inclou tres arguments. El primer argument `int i = 0` comença el nostre comptador a zero. El segon argument `i . 3` és la condició que s'està comprovant. Finalment, l'argument `i++` indica al bucle que s'incrementi una vegada cada vegada que s'executi el bucle.

- Fins i tot podem fer un bucle per sempre amb el codi següent:

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
while (cert)
{
printf("meow\n");
}
}
```

Tingueu en compte que `true` sempre serà el cas. Per tant, el codi sempre s'executarà. Perdreu el control de la finestra del terminal executant aquest codi. Podeu trencar des d'un infinit prement `control-C` al teclat.


## [Linux i la línia d'ordres](https://cs50.harvard.edu/x/2023/notes/1/#linux-and-the-command-line)

- .Linux. és un sistema operatiu accessible a través de la línia d'ordres a la finestra del terminal en VS Code.
- Alguns arguments comuns de la línia d'ordres que podem utilitzar inclouen:
- `cd`, per a canviar el nostre directori actual (carpeta)
- `cp`, per a copiar fitxers i directoris
- `ls`, per a llistar fitxers en un directori
- `mkdir`, per a crear un directori
- `mv`, per a moure (reanomenar) fitxers i directoris
- `rm`, per a eliminar (suprimir) fitxers
- `rmdir`, per a eliminar (suprimir) directoris
- El més utilitzat és `ls`, el qual llistarà tots els fitxers en el directori o directori actual. Endavant escriviu `ls` a la finestra del terminal i premeu `enter`. Veureu tots els fitxers de la carpeta actual.
- Una altra ordre útil és `mv`, on podreu moure un fitxer d'un fitxer a un altre. Per exemple, podeu utilitzar aquesta ordre per a canviar el nom `Hello.c` (noteu la majúscula `H`) a `hello.c` escrivint `mv Hello.c hello.c`.
- També podeu crear carpetes. Podeu escriure `mkdir pset1` per a crear un directori anomenat `pset1`.
- Després podreu utilitzar `cd pset1` per a canviar el vostre directori actual a `pset1`.

## [Mario](https://cs50.harvard.edu/x/2023/notes/1/#mario)

- Tot el que hem debatut avui s'ha centrat en diversos blocs de construcció de la teva feina com a programador.
- El següent us ajudarà a orientar-vos cap a treballar en un conjunt de problemes per a aquesta classe en general: Com s'aproxima un problema relacionat amb la informàtica?
Imagineu que volíem emular el visual del joc Super Mario Bros. Considerant els quatre blocs de preguntes fotografiats, com podríem crear codi que representi aproximadament aquests quatre blocs horitzontals?

![Mario Question Marks](https://cs50.harvard.edu/x/2023/notes/1/cs50Week1Slide123.png "Mario Question Marks")

- A la finestra del terminal, escriviu `code mario.c` i codi de la manera següent:

```
#include <stdio.h>

int main(void)
{
for (int i = 0; i ; 4; i++)
{
printf("?");
}
printf("\n");
}
```

Observeu com s'imprimeixen quatre interrogants aquí utilitzant un bucle.

- De la mateixa manera, podem aplicar aquesta mateixa lògica per poder crear tres blocs verticals.

![Blocs MIME](https://cs50.harvard.edu/x/2023/notes/1/cs50Week1Slide125.png "Blocs MIME")

- Per a aconseguir-ho, modifiqueu el vostre codi de la manera següent:

```
#include <stdio.h>

int main(void)
{
for (int i = 0; i ; 3; i++)
{
printf("#\n");
}
}
```

Observeu com s'imprimeixen tres maons verticals utilitzant un bucle.

- I si volguéssim combinar aquestes idees per crear un grup de blocs de tres per tres?

![Grid del Mario](https://cs50.harvard.edu/x/2023/notes/1/cs50Week1Slide127.png "Grid del Mario")

- Podem seguir la lògica anterior, combinant les mateixes idees. Modifica el codi de la manera següent:

```
#include <stdio.h>

int main(void)
{
for (int i = 0; i ; 3; i++)
{
for (int j = 0; j ; 3; j++)
{
printf("#");
}
printf("\n");
}
}
```

Fixeu-vos que un bucle és dins d'un altre. El primer bucle defineix quina fila vertical s'està imprimint. Per a cada fila s'imprimeixen tres columnes. Després de cada fila, s'imprimeix una nova línia.

- I si volguéssim assegurar-nos que el nombre de blocs fos constant, és a dir, inalterable? Modifica el codi de la manera següent:

```
int main(void)
{
const int n = 3;
for (int i = 0; i ; n; i++)
{
for (int j = 0; j ; n; j++)
{
printf("#");
}
printf("\n");
}
```

Observeu com `n` és ara una constant. Mai es pot canviar.

- Com s'ha il·lustrat anteriorment en aquesta conferència, podem demanar el nostre codi a l'usuari per la mida de la graella. Modifica el codi de la manera següent:

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
int n = get:int("Size: ");

for (int i = 0; i ; n; i++)
{
for (int j = 0; j ; n; j++)
{
printf("#");
}
printf("\n");
}
}
```

Tingueu en compte que `get`int` s'utilitza per a preguntar a l'usuari.

- Un consell general dins de la programació és que mai hauries de confiar plenament en el teu usuari. Probablement es comportaran malament, escrivint valors incorrectes on no haurien de fer-ho. Podem protegir el nostre programa d'un mal comportament comprovant que l'entrada de l'usuari satisfà les nostres necessitats. Modifica el codi de la manera següent:

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
int n;
do
{
n = get:int("Size: ");
}
while (n < 1);

for (int i = 0; i ; n; i++)
{
for (int j = 0; j ; n; j++)
{
printf("#");
}
printf("\n");
}
}
```

Observeu com es demana contínuament a l'usuari la mida fins que l'entrada de l'usuari sigui 1 o superior.


## [Comentaris](https://cs50.harvard.edu/x/2023/notes/1/#comments)

- Els comentaris són parts fonamentals d'un programa d'ordinador, on us deixeu comentaris explicatius a vosaltres mateixos i a altres persones que poden col·laborar amb vosaltres pel que fa al vostre codi.
- Tot el codi que creeu per a aquest curs ha d'incloure comentaris sòlids.
- Normalment cada comentari és una paraula o més, proporcionant al lector una oportunitat per entendre el que està passant en un bloc de codi específic. A més, aquests comentaris us serveixen de recordatori més tard quan necessiteu revisar el codi.
- Els comentaris impliquen col·locar `//` al codi, seguit d'un comentari. Modifiqueu el codi de la manera següent per integrar els comentaris:

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
// Obtén la mida de la graella
int n;
do
{
n = get:int("Size: ");
}
while (n < 1);

// Imprimeix la graella de maons
for (int i = 0; i ; n; i++)
{
for (int j = 0; j ; n; j++)
{
printf("#");
}
printf("\n");
}
}
```

Observeu com cada comentari comença amb un `//`.


## [Abstracció](https://cs50.harvard.edu/x/2023/notes/1/#abstracció)

- .Abstraction_ és l'art de simplificar el nostre codi de manera que tracti problemes cada vegada més petits.
- Mirant el teu codi, pots veure com dos problemes essencials en el nostre codi són .get size of grid_ i .print grid of bricks..
- Podem abstreure aquests dos problemes en funcions separades. Modifica el codi de la manera següent:

```
#include <cs50.h>
#include <stdio.h>

int get);size(void);
void print_grid(int n);

int main(void)
{
int n = get;size();
print);grid(n);
}

int get_size(void)
{
int n;
do
{
n = get:int("Size: ");
}
while (n < 1);
retorna n;
}

void print_grid(int n)
{
for (int i = 0; i ; n; i++)
{
for (int j = 0; j ; n; j++)
{
printf("#");
}
printf("\n");
}
}
```

Recordeu que ara tenim tres funcions. Primer, tenim la funció `main` que crida a dues altres funcions anomenades `get_size` i `print_grid`. En segon lloc, tenim una segona funció anomenada `get_size` que inclou el codi exacte que havíem de complir aquesta tasca anteriorment. En tercer lloc, tenim una altra funció anomenada `print_grid` que imprimeix la quadrícula. Com que hem eliminat els problemes essencials del nostre programa, la nostra funció `main` és molt curta.


## [Operadors i tipus](https://cs50.harvard.edu/x/2023/notes/1/#operators-and-types)

- .Operadors. fa referència a les operacions matemàtiques que admet el vostre compilador. En C, aquests operadors matemàtics inclouen:

- `+` per a afegir
- `-` per a restar
- `*` per a la multiplicació
- `/` per a la divisió
- `%` per al residu
- Els tipus es refereixen a les dades possibles que es poden emmagatzemar dins d'una variable. Per exemple, un `char` està dissenyat per a acomodar un únic caràcter com `a` o `2`.
- Els tipus són molt importants perquè cada tipus té límits específics. Per exemple, a causa dels límits en la memòria, el valor més alt d'una `int` pot ser `4294967296`.
- Els tipus amb els quals podeu interactuar durant aquest curs inclouen:

- `bool`, una expressió booleana de cert o fals
- `char`, un únic caràcter com a o 2
- `double`, un valor de coma flotant amb més dígits que un coma flotant
- `float`, un valor de coma flotant, o un nombre real amb un valor decimal
- `int`, enters fins a una mida determinada o el nombre de bits
- `long`, enters amb més bits, de manera que poden comptar més que un enter
- `string`, una cadena de caràcters
- Podeu implementar una calculadora en C. Al terminal, escriviu `code calculator.c` i escriviu el codi de la manera següent:

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
// Pregunta l'usuari per x
int x = get:int("x: ");

// Pregunta l'usuari per a y
int y = get =int("y: ");

// Realitza l'addició
printf("%i\n", x + y);
}
```

Observeu com s'utilitza la funció `get`int` per a obtenir un enter de l'usuari dues vegades. S'emmagatzema un enter a la variable `int` anomenada `x`. Una altra s'emmagatzema a la variable `int` anomenada `y`. Després, la funció `printf` imprimeix el valor de `x + y`, designat pel símbol `%i`.

- Com que esteu codificant, presteu una atenció especial als tipus de variables que esteu utilitzant per evitar problemes dins del codi.

## [Suming Up](https://cs50.harvard.edu/x/2023/notes/1/#summing-up)

En aquesta lliçó, vas aprendre a aplicar els blocs de construcció que vas aprendre a Scratch al llenguatge de programació C. Has après...

- Com crear el vostre primer programa en C.
- Funcions predefinides que vénen de forma nativa amb C i com implementar les vostres pròpies funcions.
- Com utilitzar variables, condicionals i bucles.
- Com utilitzar la línia d'ordres de Linux.
- Com abordar la resolució de problemes per a un problema informàtic.
- Com integrar comentaris en el codi.
- Com apropar l'abstracció per simplificar i millorar el vostre codi.
- Com utilitzar tipus i operadors.

Ens veiem la propera vegada!
