## [Apunts Arrays](https://cs50.harvard.edu/x/2023/notes/2/#lecture-2)


-   [Compilant](https://cs50.harvard.edu/x/2023/notes/2/#compiling)
-   [Depuració](https://cs50.harvard.edu/x/2023/notes/2/#debugging)
-   [Arrays](https://cs50.harvard.edu/x/2023/notes/2/#arrays)
-   [Cordes](https://cs50.harvard.edu/x/2023/notes/2/#strings)
-   [Arguments de la línia d'ordres](https://cs50.harvard.edu/x/2023/notes/2/#command-line-arguments)
-   [Estat de sortida](https://cs50.harvard.edu/x/2023/notes/2/#exit-status)
-   [Criptografia](https://cs50.harvard.edu/x/2023/notes/2/#cryptography)
-   [Resumint](https://cs50.harvard.edu/x/2023/notes/2/#summing-up)



## [Compilant](https://cs50.harvard.edu/x/2023/notes/2/#compiling)

-   _L'encriptació_ és l'acte d'ocultar el text senzill de mirades indiscretes. _desxifrar_ , doncs, és l'acte d'agafar un fragment de text xifrat i tornar-lo a una forma llegible per l'home.
-   Un fragment de text xifrat pot semblar el següent:
    
    ![xifratge](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide008.png "xifratge")
    
-   Recordeu que la setmana passada vau conèixer un _compilador_ , un programa informàtic especialitzat que converteix _el codi font_ en _codi màquina_ que un ordinador pot entendre.
-   Per exemple, és possible que tingueu un programa informàtic semblant a aquest:
    
    ```C
    #include <stdio.h>
    
    int main(void)
    {
        printf("hello, world\n");
    }
    ```
    
-   Un compilador agafarà el codi anterior i el convertirà en el següent codi màquina:
    
    ![codi màquina](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide012.png "codi màquina")
    
-   _VS Code_ , l'entorn de programació que us ofereix com a estudiant de CS50, utilitza un compilador anomenat `clang`llenguatge _c_ .
-   Si haguéssiu d'escriure `make hello`, executa una ordre que executa clang per crear un fitxer de sortida que podeu executar com a usuari.
-   VS Code s'ha preprogramat de manera que `make`executarà nombrosos arguments de línia d'ordres juntament amb clang per a la vostra comoditat com a usuari.
-   Considereu el codi següent:
    
    ```C
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string name = get_string("What's your name? ");
        printf("hello, %s\n", name);
    }
    ```
    
-   Podeu intentar entrar a la finestra del terminal: `clang -o hello hello.c`. Us trobareu un error que indica que clang no sap on trobar la `cs50.h`biblioteca.
-   Tornant a intentar compilar aquest codi, executeu l'ordre següent a la finestra del terminal: `clang -o hello hello.c -lcs50`. Això permetrà al compilador accedir a la `cs50.h`biblioteca.
-   Si s'executa a la finestra del terminal `./hello`, el vostre programa s'executarà tal com s'ha previst.
-   Tot i que l'anterior s'ofereix com a il·lustració, de manera que pugueu entendre més profundament el procés i el concepte de compilació de codi, fer servir `make`a CS50 està perfectament bé i l'expectativa!
-   La compilació implica passos importants, inclosos els següents:
    
    -   En primer lloc, _el preprocessament_ és on els fitxers de capçalera del vostre codi, designats per un `#`(com ara `#include \<cs50.h\>`) es copien i enganxen de manera efectiva al vostre fitxer. Durant aquest pas, el codi de `cs50.h`es copia al vostre programa. De la mateixa manera, de la mateixa manera que el vostre codi conté `#include \<stdio.h\>`, el codi contingut en `stdio.h`algun lloc de l'ordinador es copia al vostre programa. Aquest pas es pot visualitzar de la següent manera:
    
    ```C
    ...
    string get_string(string prompt);
    int printf(string format, ...);
    ...
    
    int main(void)
    {
        string name = get_string("What's your name? ");
        printf("hello, %s\n", name);
    }
    ```
    
    -   En segon lloc, _la compilació_ és on el vostre programa es converteix en codi ensamblador. Aquest pas es pot visualitzar de la següent manera:
        
        ![compilant](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide033.png "compilant")
        
    -   En tercer lloc, _el "ensemblament"_ implica que el compilador converteixi el vostre codi de muntatge en codi màquina. Aquest pas es pot visualitzar de la següent manera:
        
        ![muntatge](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide038.png "muntatge")
        
    -   Finalment, durant el pas _de vincular_ , el codi de les biblioteques incloses també es converteix en codi màquina i es combina amb el vostre codi. Aleshores s'emet el fitxer executable final.
        
        ![enllaçant](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide049.png "enllaçant")
        

## [Depuració](https://cs50.harvard.edu/x/2023/notes/2/#debugging)

-   Tothom comet errors durant la codificació.
-   Considereu la següent imatge de la setmana passada:
    
    ![mario](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide061.png "mario")
    
-   Tingueu en compte el codi següent que té un error inserit a propòsit:
    
    ```C
    #include <stdio.h>
    
    int main(void)
    {
        for (int i = 0; i <= 3; i++)
        {
            printf("#\n");
        }
    }
    ```
    
-   Escriviu `code buggy0.c`a la finestra del terminal i escriviu el codi anterior.
-   Amb aquest codi, apareixen quatre maons en comptes dels tres previstos.
-   `printf`és una manera molt útil de depurar el vostre codi. Podeu modificar el vostre codi de la següent manera:
    
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        for (int i = 0; i <= 3; i++)
        {
            printf("i es %i\n", i);
            printf("#\n");
        }
    }
    ```
    
-   En executar aquest codi, veureu nombroses declaracions, com ara `i es 0`, `i es 1`, `i es 2`i `i es 3`. En veure això, potser us adoneu que cal corregir el codi addicional de la següent manera:
    
    ```C
    #include <stdio.h>
    
    int main(void)
    {
        for (int i = 0; i < 3; i++)
        {
            printf("#\n");
        }
    }
    ```
    
    Tingueu en compte que `<=`s'ha substituït per `<`.
    
-   Una segona eina de depuració s'anomena depurador _,_ una eina de programari creada pels programadors per ajudar a localitzar errors en el codi.
-   A VS Code, se us ha proporcionat un depurador preconfigurat.
-   Per utilitzar aquest depurador, primer establiu un _punt d'interrupció_ fent clic a l'esquerra d'una línia del vostre codi, just a l'esquerra del número de línia. Quan hi feu clic, veureu que apareix un punt vermell. Imagineu-ho com un senyal de stop, demanant al compilador que s'aturi de manera que pugueu considerar què passa en aquesta part del vostre codi.
    
    ![punt de ruptura](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Debugging.png "punt de ruptura")
    
-   En segon lloc, córrer `debug50 ./buggy0`. Notareu que després que el depurador actui, una línia del vostre codi s'il·luminarà amb un color semblant a l'or. Literalment, el codi s'ha _aturat_ en aquesta línia de codi. Observeu a l'extrem superior esquerre com es mostren totes les variables locals, inclosa `i`, que té un valor actual de `0`. A la part superior de la finestra, podeu fer clic al `step over`botó i es continuarà movent pel vostre codi. Observeu com augmenta el valor de `i`.
-   Tot i que aquesta eina no us mostrarà on és el vostre error, us ajudarà a frenar i veure com s'executa el vostre codi pas a pas.
    
-   Per il·lustrar un tercer mitjà de depuració, inicieu un fitxer nou executant-lo `code buggy1.c`a la finestra del vostre terminal. Escriu el teu codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int get_negative_int(void);
    
    int main(void)
    {
        int i = get_negative_int();
        printf("%i\n", i);
    }
    
    // Prompt user for positive integer
    int get_negative_int(void)
    {
        int n;
        do
        {
            n = get_int("Negative Integer: ");
        }
        while (n < 0);
        return n;
    }
    ```
    
    L'avís `get_negative_int`està dissenyat per obtenir un nombre enter negatiu de l'usuari.
    
-   En execució `make buggy1`, notareu que no funciona com es pretén. Accepta nombres enters positius i sembla ignorar els negatius.
-   Com abans, establiu un punt d'interrupció en una línia del vostre codi. Millor establir un punt d'interrupció a `int i = get_negative_int`. Ara, corre `debug50 buggy1`.
-   A diferència d'abans, quan utilitzeu el `step over`botó a la part superior de la finestra, feu servir el `step into`botó. Això portarà el depurador a la vostra `get_negative_int`funció. Observeu com fer-ho us mostrarà que, de fet, esteu atrapats en el `do while`bucle.
-   Amb aquest coneixement, podríeu considerar per què esteu atrapats en aquest bucle, el que us portarà a editar el vostre codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int get_negative_int(void);
    
    int main(void)
    {
        int i = get_negative_int();
        printf("%i\n", i);
    }
    
    // Prompt user for positive integer
    int get_negative_int(void)
    {
        int n;
        do
        {
            n = get_int("Negative Integer: ");
        }
        while (n >= 0);
        return n;
    }
    ```
    
    `n < 0`S'ha canviat l'avís .
    
-   Una darrera forma de depuració s'anomena _depuració d'ànec de goma_ . Quan tingueu problemes amb el vostre codi, considereu com parlar en veu alta a, literalment, un ànec de goma sobre el problema del codi. Si prefereixes no parlar amb un petit ànec de plàstic, pots parlar amb un humà a prop teu! No cal que entenguin com programar: parlar amb ells és una oportunitat perquè parleu del vostre codi.
    
    ![ànec](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide070.png "ànec")
    

## [Arrays](https://cs50.harvard.edu/x/2023/notes/2/#arrays)

-   A la setmana 0, vam parlar de _tipus de dades_ com ara `bool`, `int`, `char`, `string`, etc.
-   Cada tipus de dades requereix una certa quantitat de recursos del sistema:
    -   `bool`1 byte
    -   `int`4 bytes
    -   `long`8 bytes
    -   `float`4 bytes
    -   `double`8 bytes
    -   `char`1 byte
    -   `string`? bytes
-   Dins del vostre ordinador, teniu una quantitat finita de memòria disponible.
    
    ![memòria](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide084.png "memòria")
    
-   Físicament, a la memòria del vostre ordinador, podeu imaginar com s'emmagatzemen tipus específics de dades al vostre ordinador. Us podríeu imaginar que un `char`, que només requereix 1 byte de memòria, pot tenir el següent aspecte:
    
    ![1 byte](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide087.png "1 byte")
    
-   De la mateixa manera, un `int`, que requereix 4 bytes, podria tenir el següent aspecte:
    
    ![4 bytes](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide088.png "4 bytes")
    
-   Podem crear un programa que explori aquests conceptes. Dins del terminal, escriviu `code scores.c`i escriviu el codi de la següent manera:
    
    ```
    #include <stdio.h>
    
    int main(void)
    {
        // Scores
        int score1 = 72;
        int score2 = 73;
        int score3 = 33;
    
        // Print average
        printf("Average: %f\n", (score1 + score2 + score3) / 3.0);
    }
    ```
    
    Observeu que el nombre de la dreta és un valor de coma flotant de `3.0`, de manera que el càlcul es representa com a valor de coma flotant al final.
    
-   En execució `make scores`, el programa s'executa.
-   Us podeu imaginar com s'emmagatzemen aquestes variables a la memòria:
    
    ![puntuacions a la memòria](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide098.png "puntuacions a la memòria")
    
-   _Les matrius_ són una manera d'emmagatzemar dades adossades a la memòria de manera que aquestes dades siguin fàcilment accessibles.
-   `int scores[3]`és una manera de dir-li al compilador que us proporcioni tres llocs adossats en memòria de mida `int`per emmagatzemar tres `scores`. Tenint en compte el nostre programa, podeu revisar el vostre codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        // Scores
        int scores[3];
        scores[0] = 72;
        scores[1] = 73;
        scores[2] = 33;
    
        // Print average
        printf("Average: %f\n", (scores[0] + scores[1] + scores[2]) / 3.0);
    }
    ```
    
    Observeu que `score[0]`examina el valor en aquesta ubicació de memòria per `indexing into`la matriu trucada `scores`a la ubicació `0`per veure quin valor hi ha emmagatzemat.
    
-   Podeu veure com si bé el codi anterior funciona, encara hi ha una oportunitat per millorar el nostre codi. Reviseu el vostre codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        // Get scores
        int scores[3];
        for (int i = 0; i < 3; i++)
        {
            scores[i] = get_int("Score: ");
        }
    
        // Print average
        printf("Average: %f\n", (scores[0] + scores[1] + scores[2]) / 3.0);
    }
    ```
    
    Observeu com ens indexem `scores`fent servir `scores[i]`on ens `i`proporciona el `for`bucle.
    
-   Podem simplificar o _abstraure_ el càlcul de la mitjana. Modifiqueu el vostre codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    // Constant
    const int N = 3;
    
    // Prototype
    float average(int length, int array[]);
    
    int main(void)
    {
        // Get scores
        int scores[N];
        for (int i = 0; i < N; i++)
        {
            scores[i] = get_int("Score: ");
        }
    
        // Print average
        printf("Average: %f\n", average(N, scores));
    }
    
    float average(int length, int array[])
    {
        // Calculate average
        int sum = 0;
        for (int i = 0; i < length; i++)
        {
            sum += array[i];
        }
        return sum / (float) length;
    }
    ```
    
    Observeu que es declara una nova funció cridada `average`. A més, observeu que es declara a `const`o un valor constant de . `N`El més important, observeu com `average`pren la funció `int array[]`, el que significa que el compilador passa una matriu a aquesta funció.
    
-   Les matrius no només poden ser contenidors: es poden passar entre funcions.

## [Strings](https://cs50.harvard.edu/x/2023/notes/2/#strings)

-   A `string`és simplement una matriu de variables de tipus `char`: una matriu de caràcters.
-   Tenint en compte la imatge següent, podeu veure com una cadena és una matriu de caràcters que comença amb el primer caràcter i acaba amb un caràcter especial anomenat `NUL character`:
    
    ![hola amb terminador](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide116.png "hola amb terminador")
    
-   Imaginant-ho en decimal, la vostra matriu seria el següent:
    
    ![hola amb decimal](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide117.png "hola amb decimal")
    
-   Implementant això al vostre propi codi, escriviu `code hi.c`a la finestra del terminal i escriviu el codi de la següent manera:
    
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        char c1 = 'H';
        char c2 = 'I';
        char c3 = '!';
    
        printf("%i %i %i\n", c1, c2, c3);
    }
    ```
    
    Tingueu en compte que això sortirà els valors decimals de cada caràcter.
    
-   Per entendre millor com `string`funciona un, reviseu el vostre codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string s = "HI!";
        printf("%i %i %i\n", s[0], s[1], s[2]);
    }
    ```
    
    Observeu com la `printf`instrucció presenta tres valors de la nostra matriu anomenat `s`.
    
-   Imaginem que volem dir tots dos `HI!`i `BYE!`. Modifiqueu el vostre codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string s = "HI!";
        string t = "BYE!";
    
        printf("%s\n", s);
        printf("%s\n", t);
    }
    ```
    
    Observeu que en aquest exemple es declaren i s'utilitzen dues cadenes.
    
-   Podeu visualitzar-ho de la següent manera:
    
    ![hola i adéu](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide126.png "hola i adéu")
    
-   Podem millorar encara més aquest codi. Modifiqueu el vostre codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string words[2];
    
        words[0] = "HI!";
        words[1] = "BYE!";
    
        printf("%s\n", words[0]);
        printf("%s\n", words[1]);
    }
    ```
    
    Observeu que ambdues cadenes s'emmagatzemen dins d'una única matriu de tipus `string`.
    
-   Un problema comú dins de la programació, i potser en C més específicament, és descobrir la longitud d'una matriu. Com podríem implementar això en codi? Escriviu `code length.c`a la finestra del terminal i el codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        // Prompt for user's name
        string name = get_string("Name: ");
    
        // Count number of characters up until '\0' (aka NUL)
        int n = 0;
        while (name[n] != '\0')
        {
            n++;
        }
        printf("%i\n", n);
    }
    ```
    
    Tingueu en compte que aquest codi fa un bucle fins que `NUL`es troba el caràcter.
    
-   Com que aquest és un problema tan comú dins de la programació, altres programadors han creat codi a la `string.h`biblioteca per trobar la longitud d'una cadena. Podeu trobar la longitud d'una cadena modificant el vostre codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    #include <string.h>
    
    int main(void)
    {
        // Prompt for user's name
        string name = get_string("Name: ");
        int length = strlen(name);
        printf("%i\n", length);
    }
    ```
    
    Tingueu en compte que aquest codi utilitza la `string.h`biblioteca, declarada a la part superior del fitxer. A més, utilitza una funció d'aquesta biblioteca anomenada `strlen`, que calcula la longitud de la cadena que se li passa.
    
-   `ctype.h`és una altra biblioteca que és força útil. Imagineu que volíem crear un programa que convertís tots els caràcters minúscules en majúscules. A la finestra del terminal escriviu `code uppercase.c`i escriviu el codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    #include <string.h>
    
    int main(void)
    {
        string s = get_string("Before: ");
        printf("After:  ");
        for (int i = 0, n = strlen(s); i < n; i++)
        {
            if (s[i] >= 'a' && s[i] <= 'z')
            {
                printf("%c", s[i] - 32);
            }
            else
            {
                printf("%c", s[i]);
            }
        }
        printf("\n");
    }
    ```
    
    Tingueu en compte que aquest codi _itera_ cada valor de la cadena. El programa mira cada personatge. Si el caràcter és en minúscula, li resta el valor 32 per convertir-lo en majúscules.
    
-   Recordant el nostre treball anterior de la setmana passada, potser recordeu aquest gràfic de valors ASCII:
    
    ![ascii](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide120.png "ascii")
    
-   Quan se n'ha restat un caràcter en minúscula `32`, resulta en una versió en majúscula del mateix caràcter.
-   Tot i que el programa fa el que volem, hi ha una manera més fàcil d'utilitzar la `ctype.h`biblioteca. Modifiqueu el vostre programa de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <ctype.h>
    #include <stdio.h>
    #include <string.h>
    
    int main(void)
    {
        string s = get_string("Before: ");
        printf("After:  ");
        for (int i = 0, n = strlen(s); i < n; i++)
        {
            if (islower(s[i]))
            {
                printf("%c", toupper(s[i]));
            }
            else
            {
                printf("%c", s[i]);
            }
        }
        printf("\n");
    }
    ```
    
    Tingueu en compte que el programa fa servir `islower`per detectar si cada caràcter està en majúscules o minúscules. Aleshores, `toupper`es passa la funció `s[i]`. Cada caràcter (si és minúscula) es converteix en majúscula.
    
-   De nou, mentre aquest programa fa el que es desitja, hi ha una oportunitat de millora. Com diu la documentació dels `ctype.h`estats, `toupper`és prou intel·ligent per saber que si s'aprova el que ja és una lletra majúscula, simplement ho ignorarà. Per tant, ja no necessitem la nostra `if`declaració. Podeu simplificar aquest codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <ctype.h>
    #include <stdio.h>
    #include <string.h>
    
    int main(void)
    {
        string s = get_string("Before: ");
        printf("After:  ");
        for (int i = 0, n = strlen(s); i < n; i++)
        {
            printf("%c", toupper(s[i]));
        }
        printf("\n");
    }
    ```
    
    Tingueu en compte que aquest codi està força simplificat, eliminant la `if`declaració innecessària.
    
-   Podeu llegir sobre totes les capacitats de la `ctype`biblioteca a les [pàgines del manual](https://manual.cs50.io/#ctype.h) .

## [Arguments de la línia d'ordres(Command Line)
](https://cs50.harvard.edu/x/2023/notes/2/#command-line-arguments)

-   `Command-line arguments`són aquells arguments que es passen al vostre programa a la línia d'ordres. Per exemple, totes aquelles sentències que heu escrit després `clang`es consideren arguments de línia d'ordres. Podeu utilitzar aquests arguments als vostres propis programes!
-   A la finestra del terminal, escriviu `code greet.c`i escriviu el codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string name = get_string("What's your name? ");
        printf("hello, %s\n", name);
    }
    ```
    
    Tingueu en compte que això ho diu `hello`a l'usuari.
    
-   Tot i així, no seria bo poder acceptar arguments abans que s'executi el programa? Modifiqueu el vostre codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(int argc, string argv[])
    {
        if (argc == 2)
        {
            printf("hello, %s\n", argv[1]);
        }
        else
        {
            printf("hello, world\n");
        }
    }
    ```
    
    Tingueu en compte que aquest programa coneix tant `argc`, el nombre d'arguments de la línia d'ordres, com `argv`que és una matriu dels caràcters passats com a arguments a la línia d'ordres.
    
-   Per tant, utilitzant la sintaxi d'aquest programa, l'execució `./greet David`donaria com a resultat que el programa digués `hello, David`.

## [Exit Status](https://cs50.harvard.edu/x/2023/notes/2/#exit-status)

-   Quan finalitza un programa, es proporciona un codi de sortida especial a l'ordinador.
-   Quan un programa surt sense error, es proporciona un codi d'estat `0` . Sovint, quan es produeix un error que fa que el programa finalitzi, l'ordinador proporciona un estat de `1`.
-   Podeu escriure un programa de la següent manera que ho il·lustri escrivint `code status.c`i escrivint codi de la següent manera:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(int argc, string argv[])
    {
        if (argc != 2)
        {
            printf("Missing command-line argument\n");
            return 1;
        }
        printf("hello, %s\n", argv[1]);
        return 0;
    }
    ```
    
    Tingueu en compte que si no proporcioneu `./status David`, obtindreu un estat de sortida de `1`. Tanmateix, si proporcioneu `./status David`, obtindreu un estat de sortida de `0`.
    
-   Us podeu imaginar com podeu utilitzar parts del programa anterior per comprovar si un usuari ha proporcionat el nombre correcte d'arguments de línia d'ordres.

## [Criptografia](https://cs50.harvard.edu/x/2023/notes/2/#cryptography)

-   La criptografia és l'art de xifrar i desxifrar un missatge.
-   `plaintext`i a `key`es proporcionen a un `cipher`, donant lloc a text xifrat.
    
    ![criptografia](https://cs50.harvard.edu/x/2023/notes/2/cs50Week2Slide153.png "criptografia")
    
-   La clau és un argument especial passat al xifrat juntament amb el text pla. El xifratge utilitza la clau per prendre decisions sobre com implementar el seu algorisme de xifrat.

## [Resumint](https://cs50.harvard.edu/x/2023/notes/2/#summing-up)

En aquesta lliçó, heu après més detalls sobre la compilació i com s'emmagatzemen les dades en un ordinador. Concretament, has après...

-   En general, com funciona un compilador.
-   Com depurar el vostre codi mitjançant quatre mètodes.
-   Com utilitzar matrius dins del vostre codi.
-   Com les matrius emmagatzemen dades en porcions posteriors de memòria.
-   Com les cadenes són simplement matrius de caràcters.
-   Com interactuar amb les matrius del vostre codi.
-   Com es poden passar els arguments de la línia d'ordres als vostres programes.
-   Els blocs bàsics de la criptografia.

Ens veiem a la propera!