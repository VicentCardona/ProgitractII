# Algorismes

## Benvingut!

-   Al començament del curs, vam introduir la idea d'un *algorisme* .
-   Aquesta setmana, ampliarem la nostra comprensió dels algorismes a través del pseudocodi i en el propi codi.
-   A més, anem a considerar l'eficiència d'aquests algorismes. De fet, anirem construint sobre la nostra comprensió de com utilitzar alguns dels conceptes *de nivell inferior* que hem estat treballant per crear algorismes.

## Algorismes

-   Recordeu que previament us van presentar la idea d'una *matriu* , blocs de memòria que estan un al costat de l'altre.
-   Podeu imaginar metafòricament una *array* com una sèrie de set armariets vermells de la següent manera:
    
    ![Set taquilles vermelles una al costat de l'altra](https://cs50.harvard.edu/x/2023/notes/3/cs50Week3Slide018.png "taquilles")
    
-   Ens podem imaginar que tenim el problema essencial de voler saber: "El número 50 està dins d'una *array*?"
-   Potencialment podem facilitar la nostra *array* a un algorisme, en el qual aquest cercarà a través dels nostres armariets per veure si el número 50 està darrere d'una de les portes: retornant el valor vertader o fals.
    
    ![set taquilles vermelles apuntant a una caixa buida.  De la caixa buida surt i la sortida de bool](https://cs50.harvard.edu/x/2023/notes/3/cs50Week3Slide022.png "taquilles com a algorisme")
    
-   Podem imaginar diverses instruccions que podem proporcionar al nostre algorisme per dur a terme aquesta tasca de la següent manera:
    
    ```
    Per a cada porta d'esquerra a dreta
        Si 50 està darrera la porta
            Retorna "true"
    Retorna false
    ```
    
    Tingueu en compte que les instruccions anteriors s'anomenen *pseudocodi* : una versió llegible per l'home de les instruccions que podríem proporcionar a l'ordinador.
    
-   Un informàtic podria traduir aquest pseudocodi de la següent manera:
    
    ```
    For i from 0 to n-1
        If 50 is behind doors[i]
            Return true
    Return false
    ```
    
    Tingueu en compte que l'anterior encara no és codi, però és una aproximació força propera a com podria semblar el codi final.
    
-   *La cerca binària* és un *algorisme de cerca* que es podria utilitzar en la nostra tasca de trobar el 50.
-   Suposant que els valors dins dels armariets s'han organitzat de més petit a més gran, el pseudocodi per a la cerca binària apareixerà de la següent manera:
    
    ```
    Si no hi ha cap porta
        Retorna "false"
    Si 50 està darrera la porta d'enmig
        Retorna "true"
    "Else" si 50 < la porta d'enmig
        busca a la meitat esquerra
    "Else" si 50 > la porta d'enmig
        busca a la meitat dreta
    ```
    
-   Utilitzant la nomenclatura del codi, podem modificar encara més el nostre algorisme de la següent manera:
    
    ```
    If no doors
        Return false
    If 50 is behind doors[middle]
        Return true
    Else if 50 < doors[middle]
        Search doors[0] through doors[middle-1]
    Else if 50 > doors[middle]
        Search doors[middle+1] through doors[n-1]
    ```
    
    Tingueu en compte que, mirant aquesta aproximació del codi, gairebé us podeu imaginar com podria semblar això en el codi real.
    

## Temps d'execució

-   *El temps d'execució* implica una anàlisi utilitzant la notació *O gran* . Mireu el gràfic següent:
    
    ![gràfic amb: "mida del problema" com a eix x;  "temps per resoldre" com a eix y;  línia recta vermella i pronunciada des de l'origen fins a la part superior del gràfic propera al groc, línia recta menys pronunciada des de l'origen fins a la part superior del gràfic, ambdues etiquetades amb "O(n)";  línia corba verda que es fa cada cop menys pronunciada des de l'origen fins a la dreta del gràfic amb l'etiqueta "O(log n)](https://cs50.harvard.edu/x/2023/notes/3/cs50Week3Slide042.png "gran o gràfica")
    
-   Al gràfic anterior, el primer algorisme es troba en $O(n)$. El segon també es troba a $O(n)$. El tercer es troba a $O(log n)$.
-   És la forma de la corba que mostra l'eficiència d'un algorisme. Alguns dels temps de funcionament habituals que podem veure són:
    
    -   \\(O(n^2)\\)
    -   \\(O(n \\log n)\\)
    -   \\(O(n)\\)
    -   \\(O(\\log n)\\)
    -   \\(O(1)\\)
-   Dels temps de funcionament anteriors, \\(O(n^2)\\) es considera el pitjor temps de funcionament, \\(O(1)\\) és el més ràpid.
-   La cerca lineal era d'ordre \\(O(n)\\) perquè podia prendre _n_ passos en el pitjor dels casos per executar-se.
-   La cerca binària era d'ordre \\(O(\\log n)\\) perquè es necessitarien cada cop menys passos fins i tot en el pitjor dels casos.
-   Els programadors estan interessats tant en el pitjor cas, o _límit superior_ , com en el millor cas, o _límit inferior_ .
-   El símbol \\(\\Omega\\) s'utilitza per indicar el millor cas d'un algorisme, com ara \\(\\Omega(\\log n)\\).
-   El símbol \\(\\Theta\\) s'utilitza per indicar on el límit superior i el límit inferior són iguals, on els temps d'execució del millor cas i del pitjor dels casos són els mateixos.

## [Cerca lineal i binària](https://cs50.harvard.edu/x/2023/notes/3/#linear-and-binary-search)

-   Podeu implementar la cerca lineal nosaltres mateixos escrivint `code search.c`a la finestra de la vostra terminal i escrivint el codi de la següent manera:
    
    ```
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        // An array of integers
        int numbers[] = {20, 500, 10, 5, 100, 1, 50};
    
        // Search for number
        int n = get_int("Number: ");
        for (int i = 0; i < 7; i++)
        {
            if (numbers[i] == n)
            {
                printf("Found\n");
                return 0;
            }
        }
        printf("Not found\n");
        return 1;
    }
    ```
    
    Observeu que la línia que comença per `int numbers[]`ens permet definir els valors de cada element de la matriu a mesura que la creem. Aleshores, en el `for`bucle, tenim una implementació de la cerca lineal.
    
-   Ara hem implementat la cerca lineal nosaltres mateixos en C!
-   Què passaria si volguéssim cercar una cadena dins d'una matriu? Modifiqueu el vostre codi de la següent manera:
    
    ```
    #include <cs50.h>
    #include <stdio.h>
    #include <string.h>
    
    int main(void)
    {
        // An array of strings
        string strings[] = {"battleship", "boot", "cannon", "iron", "thimble", "top hat"};
    
        // Search for string
        string s = get_string("String: ");
        for (int i = 0; i < 6; i++)
        {
            if (strcmp(strings[i], s) == 0)
            {
                printf("Found\n");
                return 0;
            }
        }
        printf("Not found\n");
        return 1;
    }
    ```
    
    Tingueu en compte que no podem utilitzar `==`com en la nostra iteració anterior d'aquest programa. En canvi, hem d'utilitzar `strcmp`, que prové de la `string.h`biblioteca.
    
-   De fet, executar aquest codi ens permet iterar sobre aquesta matriu de cadenes per veure si hi havia una determinada cadena. Tanmateix, si veieu un _error de segmentació_ , on el vostre programa ha tocat una part de la memòria a la qual no hauria de tenir accés, assegureu-vos que heu `i < 6`indicat més amunt en lloc de `i < 7`.
    
-   Podem combinar aquestes idees tant de nombres com de cadenes en un sol programa. Escriviu `code phonebook.c`a la finestra del vostre terminal i escriviu el codi de la següent manera:
    
    ```
    #include <cs50.h>
    #include <stdio.h>
    #include <string.h>
    
    int main(void)
    {
        // Arrays of strings
        string names[] = {"Carter", "David"};
        string numbers[] = {"+1-617-495-1000", "+1-949-468-2750"};
    
        // Search for name
        string name = get_string("Name: ");
        for (int i = 0; i < 2; i++)
        {
            if (strcmp(names[i], name) == 0)
            {
                printf("Found %s\n", numbers[i]);
                return 0;
            }
        }
        printf("Not found\n");
        return 1;
    }
    ```
    
    Tingueu en compte que el número de Carter comença amb `+1-617`i el número de telèfon de David comença amb "1-949". Per tant, `names[0]`és Carter i és `numbers[0]`el nombre de Carter.
    
-   Tot i que aquest codi funciona, hi ha nombroses ineficiències. De fet, hi ha la possibilitat que els noms i els números de les persones no es corresponguin. No estaria bé si poguéssim crear el nostre propi tipus de dades on poguéssim associar una persona amb el número de telèfon?

## [Estructures de dades](https://cs50.harvard.edu/x/2023/notes/3/#data-structures)

-   Resulta que C permet una manera per la qual podem crear els nostres propis tipus de dades mitjançant un fitxer `struct`. Modifiqueu el vostre codi de la següent manera:
    
    ```
    #include <cs50.h>
    #include <stdio.h>
    #include <string.h>
    
    typedef struct
    {
        string name;
        string number;
    }
    person;
    
    int main(void)
    {
        person people[2];
    
        people[0].name = "Carter";
        people[0].number = "+1-617-495-1000";
    
        people[1].name = "David";
        people[1].number = "+1-949-468-2750";
    
        // Search for name
        string name = get_string("Name: ");
        for (int i = 0; i < 2; i++)
        {
            if (strcmp(people[i].name, name) == 0)
            {
                printf("Found %s\n", people[i].number);
                return 0;
            }
        }
        printf("Not found\n");
        return 1;
    }
    ```
    
    Tingueu en compte que el codi comença on es defineix `typedef struct`un nou tipus de dades anomenat `person`. Dins d'a hi `person`ha una cadena trucada `name`i un `string`nombre cridat. A la `main`funció, comenceu creant una matriu anomenada `people`que sigui de tipus `person`que tingui una mida de 2. A continuació, actualitzem els noms i números de telèfon de les dues persones de la nostra `people`matriu. El més important, observeu com la _notació de punts,_ com ara, `people[0].name`ens permet accedir `person`a la ubicació 0 i assignar un nom a aquesta persona.
    

## [Classificació](https://cs50.harvard.edu/x/2023/notes/3/#sorting)

-   _L'ordenació_ és l'acció d'agafar una llista de valors no ordenada i transformar aquesta llista en una de ordenada.
-   Quan s'ordena una llista, cercar-la és molt menys imposant a l'ordinador. Recordeu que podem utilitzar la cerca binària en una llista ordenada, però no en una no ordenada.
-   Resulta que hi ha molts tipus diferents d'algorismes d'ordenació.
-   _L'ordenació de selecció_ és un d'aquests algorismes de cerca.
-   L'algorisme per a l'ordenació de selecció en pseudocodi és:
    
    ```
    For i from 0 to n–1
        Find smallest number between numbers[i] and numbers[n-1]
        Swap smallest number with numbers[i]
    ```
    
-   Considereu la llista sense ordenar de la següent manera:
    
-   L'ordenació de selecció començarà buscant el nombre més petit de la llista i canviarà aquest número amb la nostra posició actual a la llista. En aquest cas, el zero es localitza i es mou a la nostra posició actual.
    
-   Ara, el nostre problema s'ha reduït ja que sabem que almenys el començament de la nostra llista està ordenat. Així que podem repetir el que vam fer, començant pel segon número de la llista:
    
-   1 és el nombre més petit ara, així que l'intercanviarem pel segon nombre. Ho repetirem de nou...
    
-   … I un altre cop…
    
-   … I un altre cop…
    
-   … I un altre cop …
    
-   etcètera.
-   _L'ordenació de bombolles_ és un altre algorisme d'ordenació que funciona intercanviant elements repetidament per "bombolles" elements més grans fins al final.
-   El pseudocodi per a l'ordenació de bombolles és:
    
    ```
    Repeat n-1 times
    For i from 0 to n–2
        If numbers[i] and numbers[i+1] out of order
            Swap them
    ```
    
-   Començarem amb la nostra llista no ordenada, però aquesta vegada mirarem parells de números i els canviarem si estan fora d'ordre:
    
    ```
    5 2 7 4 1 6 3 0
    ^ ^
    2 5 7 4 1 6 3 0
      ^ ^
    2 5 7 4 1 6 3 0
        ^ ^
    2 5 4 7 1 6 3 0
          ^ ^
    2 5 4 1 7 6 3 0
            ^ ^
    2 5 4 1 6 7 3 0
              ^ ^
    2 5 4 1 6 3 7 0
                ^ ^
    2 5 4 1 6 3 0 7
    ```
    
-   Ara, el nombre més alt és tot a la dreta, així que hem millorat el nostre problema. Ho repetirem de nou:
    
    ```
    2 5 4 1 6 3 0 | 7
    ^ ^
    2 5 4 1 6 3 0 | 7
      ^ ^
    2 4 5 1 6 3 0 | 7
        ^ ^
    2 4 1 5 6 3 0 | 7
          ^ ^
    2 4 1 5 6 3 0 | 7
            ^ ^
    2 4 1 5 3 6 0 | 7
              ^ ^
    2 4 1 5 3 0 6 | 7
    ```
    
-   Ara els dos valors més grans es troben a la dreta. Tornarem a repetir:
    
    ```
      2 4 1 5 3 0 | 6 7
      ^ ^
      2 4 1 5 3 0 | 6 7
        ^ ^
      2 1 4 5 3 0 | 6 7
          ^ ^
      2 1 4 5 3 0 | 6 7
            ^ ^
      2 1 4 3 5 0 | 6 7
              ^ ^
      2 1 4 3 0 5 | 6 7
    ```
    
-   … I un altre cop …
    
    ```
      2 1 4 3 0 | 5 6 7
      ^ ^
      1 2 4 3 0 | 5 6 7
        ^ ^
      1 2 3 4 0 | 5 6 7
          ^ ^
      1 2 3 4 0 | 5 6 7
            ^ ^
      1 2 3 0 4 | 5 6 7
    ```
    
-   … I un altre cop …
    
    ```
      1 2 3 0 | 4 5 6 7
      ^ ^
      1 2 3 0 | 4 5 6 7
        ^ ^
      1 2 3 0 | 4 5 6 7
          ^ ^
      1 2 0 3 | 4 5 6 7
    ```
    
-   … I un altre cop …
    
    ```
      1 2 0 | 3 4 5 6 7
      ^ ^
      1 2 0 | 3 4 5 6 7
        ^ ^
      1 0 2 | 3 4 5 6 7
    ```
    
-   … i finalment …
    
    ```
      1 0 | 2 3 4 5 6 7
      ^ ^
      0 1 | 2 3 4 5 6 7
    ```
    
-   Tingueu en compte que, a mesura que anem recorrent la nostra llista, sabem que cada cop més s'ordena, de manera que només hem de mirar els parells de nombres que encara no s'han ordenat.
-   Analitzant l'ordre de selecció, només vam fer set comparacions. Representant això matemàticament, on _n_ representa el nombre de casos, es podria dir que l'ordenació de selecció es pot analitzar com:
    
    ```
      (n-1)+(n-2)+(n-3)+ ... + 1
    ```
    
    o, més simplement \\(n^2/2 - n/2\\).
    
-   Tenint en compte que l'anàlisi matemàtica, n <sup><span><span>2</span></span></sup> és realment el factor més influent per determinar l'eficiència d'aquest algorisme. Per tant, es considera que l'ordenació per selecció és de l'ordre de \\(O(n^2)\\) en el pitjor dels casos en què tots els valors no estan ordenats. Fins i tot quan tots els valors estiguin ordenats, es farà el mateix nombre de passos. Per tant, el millor cas es pot assenyalar com \\(\\Omega(n^2)\\). Atès que tant els casos de límit superior com de límit inferior són els mateixos, l'eficiència d'aquest algorisme en el seu conjunt es pot considerar \\(\\Theta(n^2)\\).
-   Analitzant l'ordenació de bombolles, el pitjor dels casos és \\(O(n^2)\\). El millor dels casos és \\(\\Omega(n)\\).
-   Podeu [visualitzar](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html) una comparació d'aquests algorismes.

## [Recursió](https://cs50.harvard.edu/x/2023/notes/3/#recursion)

-   Com podríem millorar la nostra eficiència en la nostra classificació?
-   _La recursència_ és un concepte dins de la programació on una funció s'anomena a si mateixa. Això ho vam veure abans quan vam veure...
    
    ```
    If no doors
        Return false
    If number behind middle door
        Return true
    Else if number < middle door
        Search left half
    Else if number > middle door
        Search right half
    ```
    
    Tingueu en compte que estem demanant `search`iteracions cada cop més petites d'aquest problema.
    
-   De la mateixa manera, al nostre pseudocodi per a la setmana 0, podeu veure on es va implementar la recursivitat:
    
    ```
    1  Pick up phone book
    2  Open to middle of phone book
    3  Look at page
    4  If person is on page
    5      Call person
    6  Else if person is earlier in book
    7      Open to middle of left half of book
    8      Go back to line 3
    9  Else if person is later in book
    10     Open to middle of right half of book
    11     Go back to line 3
    12 Else
    13     Quit
    ```
    
-   Penseu en com la setmana 1 volíem crear una estructura piramidal de la següent manera:
    
-   Per implementar-ho mitjançant recursivitat, escriviu `code recursion.c`a la vostra finestra de terminal i escriviu el codi de la següent manera:
    
    ```
    #include <cs50.h>
    #include <stdio.h>
    
    void draw(int n);
    
    int main(void)
    {
        draw(1);
    }
    
    void draw(int n)
    {
        for (int i = 0; i < n; i++)
        {
            printf("#");
        }
        printf("\n");
    
        draw(n + 1);
    }
    ```
    
    Observeu que la funció de dibuix s'anomena a si mateixa. A més, tingueu en compte que el vostre codi pot quedar atrapat en un bucle infinit. Per trencar aquest bucle, si us quedeu encallat, premeu `ctrl-c`el teclat. La raó per la qual això crea un bucle infinit és que no hi ha res que digui que el programa acabi. No hi ha cap cas on es faci el programa.
    
-   Podem corregir el nostre codi de la següent manera:
    
    ```
    #include <cs50.h>
    #include <stdio.h>
    
    void draw(int n);
    
    int main(void)
    {
        // Get height of pyramid
        int height = get_int("Height: ");
    
        // Draw pyramid
        draw(height);
    }
    
    void draw(int n)
    {
        // If nothing to draw
        if (n <= 0)
        {
            return;
        }
    
        // Draw pyramid of height n - 1
        draw(n - 1);
    
        // Draw one more row of width n
        for (int i = 0; i < n; i++)
        {
            printf("#");
        }
        printf("\n");
    }
    ```
    
    Tingueu en compte que el _cas base_ garantirà que el codi no s'executi per sempre. La línia `if (n <= 0)`acaba la recursivitat perquè el problema s'ha resolt. Cada vegada `draw`que es diu a si mateix, s'anomena per `n-1`. En algun moment, `n-1`serà igual a `0`, la qual cosa farà que la `draw`funció torni i el programa finalitzarà.
    

## [Fusionar Ordenar](https://cs50.harvard.edu/x/2023/notes/3/#merge-sort)

-   Ara podem aprofitar la recursivitat en la nostra recerca d'un algorisme d'ordenació més eficient i implementar el que s'anomena _merge sort_ , un algorisme d'ordenació molt eficient.
-   El pseudocodi per a l'ordenació de combinació és força curt:
    
    ```
    If only one number
        Quit
    Else
        Sort left half of number
        Sort right half of number
        Merge sorted halves
    ```
    
-   Considereu la següent llista de números:
    
-   En primer lloc, l'ordenació combinada pregunta: "Aquest és un número?" La resposta és "no", de manera que l'algorisme continua.
    
-   En segon lloc, l'ordenació combinada dividirà els números pel mig (o tan a prop com pugui) i ordenarà la meitat esquerra dels números.
    
-   En tercer lloc, l'ordenació combinada miraria aquests números a l'esquerra i preguntaria: "Aquest és un número?" Com que la resposta és no, llavors dividiria els números de l'esquerra pel mig.
    
-   En quart lloc, l'ordenació de combinació tornarà a preguntar "és aquest un número?" Aquesta vegada la resposta és sí! Per tant, sortirà d'aquesta tasca i tornarà a l'última tasca que estava executant en aquest moment:
    
-   En cinquè lloc, l'ordenació combinada ordenarà els números de l'esquerra.
    
-   Ara, tornem a on vam deixar el pseudocodi ara que s'ha ordenat el costat esquerre. Un procés similar dels passos 3-5 es produirà amb els números de la dreta. Això donarà lloc a:
    
-   Ara les dues meitats estan ordenades. Finalment, l'algorisme fusionarà els dos costats. Mirarà el primer número a l'esquerra i el primer número a la dreta. Posarà primer el nombre més petit i després el segon més petit. L'algorisme repetirà això per a tots els números, donant com a resultat:
    
-   L'ordenació de combinació s'ha completat i el programa es tanca.
-   L'ordenació combinada és un algorisme d'ordenació molt eficient amb el pitjor cas de \\(O(n \\log n)\\). El millor dels casos segueix sent \\(\\Omega(n \\log n)\\) perquè l'algorisme encara ha de visitar cada lloc de la llista. Per tant, l'ordenació de combinació també és \\(\\Theta(n \\log n)\\) ja que el millor i el pitjor són els mateixos.
-   Es va compartir una [visualització](https://www.youtube.com/watch?v=ZZuD6iUe3Pc) final .

## [Resumint](https://cs50.harvard.edu/x/2023/notes/3/#summing-up)

En aquesta lliçó, heu après sobre el pensament algorítmic i la creació dels vostres propis tipus de dades. Concretament, has après...

-   Algorismes.
-   _Notació O_ gran .
-   Cerca binària i cerca lineal.
-   Diversos algorismes d'ordenació, com ara l'ordenació per bombolles, l'ordenació per selecció i l'ordenació per fusió.
-   Recursió.

Ens veiem a la propera!
