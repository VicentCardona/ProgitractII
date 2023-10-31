## Pluralitat

Per a aquest programa, implementareu un programa que faci una elecció, segons el següent.

```
$ ./plurality Alice Bob Charlie
Number of voters: 4
Vote: Alice
Vote: Bob
Vote: Charlie
Vote: Alice
Alice
```

## Backround

Les eleccions tenen totes les formes i mides. Al Regne Unit, el [primer ministre](https://www.parliament.uk/education/about-your-parliament/general-elections/) és nomenat oficialment pel monarca, que generalment tria el líder del partit polític que guanya més escons a la Cambra dels Comuns. [Els Estats Units utilitzen un procés de col·legi electoral](https://www.archives.gov/federal-register/electoral-college/about.html) de diversos passos on els ciutadans voten sobre com ha d'assignar cada estat els electors que després elegeixen el president.

Potser la manera més senzilla de celebrar eleccions, però, és a través d'un mètode conegut com a "vot de pluralitat" (també conegut com a "primer passatge" o "el guanyador s'emporta tot"). En el vot plural, cada elector pot votar per un candidat. Al final de les eleccions, el candidat que tingui el major nombre de vots és declarat guanyador de les eleccions.

## Començant

Inicieu sessió a [cs50.dev](https://cs50.dev/) , feu clic a la finestra del vostre terminal i executeu `cd`\-lo sol. Hauríeu de trobar que la sol·licitud de la vostra finestra de terminal s'assembla a la següent:

A continuació executeu

```
wget https://cdn.cs50.net/2022/fall/psets/3/plurality.zip
```

per descarregar un ZIP cridat `plurality.zip`al vostre espai de codi.

Després executar

per crear una carpeta anomenada `plurality`. Ja no necessiteu el fitxer ZIP, així que podeu executar-lo

i responeu amb "y" seguit d'Enter a la sol·licitud per eliminar el fitxer ZIP que heu baixat.

Ara escriviu

seguit d'Enter per moure't a (és a dir, obrir) aquest directori. La vostra sol·licitud ara hauria de semblar-se a la següent.

Si tot ha tingut èxit, hauríeu d'executar

i vegeu un fitxer anomenat `plurality.c`. L'execució `code plurality.c`hauria d'obrir el fitxer on escriureu el codi per a aquest conjunt de problemes. Si no, torna sobre els teus passos i mira si pots determinar on t'has equivocat!

## [Comprensió](https://cs50.harvard.edu/x/2023/psets/3/plurality/#understanding)

Fem una ullada `plurality.c`i llegim el codi de distribució que se us ha proporcionat.

La línia `#define MAX 9`és una sintaxi que s'utilitza aquí per significar que `MAX`és una constant (igual a `9`) que es pot utilitzar al llarg del programa. Aquí, representa el nombre màxim de candidats que pot tenir una elecció.

Aleshores, el fitxer defineix `struct`un `candidate`. Cadascun `candidate`té dos camps: un `string`anomenat `name`que representa el nom del candidat i un `int`anomenat `votes`que representa el nombre de vots que té el candidat. A continuació, el fitxer defineix una matriu global de `candidates`, on cada element és en si mateix un `candidate`.

Ara, feu una ullada a la `main`funció en si. Mireu si podeu trobar on el programa estableix una variable global `candidate_count`que representa el nombre de candidats a l'elecció, copia els arguments de la línia d'ordres a la matriu `candidates`i demana a l'usuari que introdueixi el nombre de votants. Aleshores, el programa permet que cada votant escrigui un vot (veieu com?), cridant a la `vote`funció de cada candidat votat. Finalment, `main`fa una trucada a la `print_winner`funció per imprimir el guanyador (o els guanyadors) de les eleccions.

Tanmateix, si mireu més avall al fitxer, notareu que les funcions `vote`i `print_winner`s'han deixat en blanc. Aquesta part depèn de tu completar!

## Especificació

Completar la implementació de `plurality.c`de manera que el programa simuli una elecció de vot plural.

-   Completa la `vote`funció.
    -   `vote`pren un sol argument, un `string`anomenat `name`, que representa el nom del candidat que ha estat votat.
    -   Si `name`coincideix amb un dels noms dels candidats a les eleccions, actualitzeu el total de vots d'aquest candidat per tenir en compte el nou vot. La `vote`funció en aquest cas hauria de tornar `true`per indicar una votació correcta.
    -   Si `name`no coincideix amb el nom de cap dels candidats a les eleccions, no haurien de canviar els totals de vots i la `vote`funció hauria de tornar `false`per indicar una papereta no vàlida.
    -   Podeu suposar que no hi ha dos candidats que tindran el mateix nom.
-   Completa la `print_winner`funció.
    -   La funció ha d'imprimir el nom del candidat que ha rebut més vots a les eleccions i després imprimir una nova línia.
    -   És possible que l'elecció acabi en empat si diversos candidats tenen cadascun el màxim de vots. En aquest cas, hauríeu de publicar els noms de cadascun dels candidats guanyadors, cadascun en una línia separada.

No hauríeu de modificar res més `plurality.c`que les implementacions de les funcions `vote`i `print_winner`(i la inclusió de fitxers de capçalera addicionals, si ho voleu).

## Ús

El vostre programa s'ha de comportar segons els exemples següents.

```
$ ./plurality Alice Bob
Number of voters: 3
Vote: Alice
Vote: Bob
Vote: Alice
Alice
```

```
$ ./plurality Alice Bob
Number of voters: 3
Vote: Alice
Vote: Charlie
Invalid vote.
Vote: Alice
Alice
```

```
$ ./plurality Alice Bob Charlie
Number of voters: 5
Vote: Alice
Vote: Charlie
Vote: Bob
Vote: Bob
Vote: Alice
Alice
Bob
```

## Tutorial

<iframe allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" data-video="" src="https://www.youtube.com/embed/ftOapzDjEb8?modestbranding=0&amp;rel=0&amp;showinfo=0" data-ruffle-polyfilled="" scrolling="no" id="iFrameResizer0"></iframe>

## Prova

Assegureu-vos de provar el vostre codi per assegurar-vos que gestiona...

-   Una elecció amb qualsevol nombre de candidats (fins al `MAX`de `9`)
-   Votar a un candidat pel seu nom
-   Vots no vàlids per als candidats que no estan a la votació
-   Impressió del guanyador de les eleccions si només n'hi ha un
-   Impressió del guanyador de l'elecció si hi ha diversos guanyadors

Executeu el següent per avaluar la correcció del vostre codi amb `check50`. Però assegureu-vos de compilar-lo i provar-lo vosaltres mateixos també!

```
check50 cs50/problems/2023/x/plurality
```

Executeu el següent per avaluar l'estil del vostre codi amb `style50`.
