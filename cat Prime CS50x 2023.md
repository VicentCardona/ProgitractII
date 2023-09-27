## [Primer](https://cs50.harvard.edu/x/2023/problems/1/prime/#prime)

## [Objectius d'aprenentatge](https://cs50.harvard.edu/x/2023/problems/1/prime/#learning-goals)

-   Practica l'ús `for`de bucles
-   Utilitzant mòdul
-   Creació d'una funció booleana

![nombres primers](https://cs50.harvard.edu/x/2023/problems/1/prime/prime-numbers.jpg)

## [Fons](https://cs50.harvard.edu/x/2023/problems/1/prime/#background)

[Els nombres primers](https://en.wikipedia.org/wiki/Prime_number) es defineixen com a nombres enters superiors a 1, els únics factors dels quals són l'1 i ell mateix. Per tant, 3 és primer perquè els seus únics factors són 1 i 3, mentre que 4 és compost i no primer, perquè és el producte de 2 × 2. En aquest laboratori escriureu un algorisme per generar tots els nombres primers en un interval especificat per la usuari.

-   Pistes
    
    -   El mòdul pot ser útil, ja que produeix la resta en dividir dos nombres enters.
    -   Per definició, 1 no és un nombre primer.
    -   Només hi ha un nombre primer parell, el 2.
    

## [Demostració](https://cs50.harvard.edu/x/2023/problems/1/prime/#demo)

![PrimeGif](https://cs50.harvard.edu/x/2023/problems/1/prime/primeDemo.gif)

## [Començant](https://cs50.harvard.edu/x/2023/problems/1/prime/#getting-started)

1.  Inicieu sessió a [cs50.dev](https://cs50.dev/) amb el vostre compte de GitHub.
2.  Feu clic dins de la finestra del terminal i executeu `cd`.
3.  A la `$`sol·licitud, escriviu`mkdir prime`
4.  Ara executa`cd prime`
5.  A continuació, copieu i enganxeu `wget https://cdn.cs50.net/2022/fall/labs/1/prime.c`al vostre terminal per descarregar el codi de distribució d'aquest laboratori.
6.  Heu de completar la funció booleana, `prime`, que prova si un nombre és primer i retorna cert si ho és, i fals si no ho és.

## [Detalls d'implementació](https://cs50.harvard.edu/x/2023/problems/1/prime/#implementation-details)

La manera més senzilla de comprovar si un nombre és primer és intentar dividir-lo per cada nombre des del 2 fins al nombre en si, però sense incloure. Si algun nombre es divideix en ell sense resta, aquest nombre no és primer.

La `main`funció del codi de distribució conté un `for`bucle que itera per l'interval especificat per l'usuari, amb els dos extrems inclosos. Per exemple, si l'usuari escriu `1`for `min`i `100`for `max`, el `for`bucle provarà cada nombre, de l'1 al 100. Cadascun d'aquests nombres es passa a una funció, `prime`, que implementareu per retornar qualsevol `true`o `false`en funció de si el nombre és primer.

## [Pregunta de pensament](https://cs50.harvard.edu/x/2023/problems/1/prime/#thought-question)

-   Pots fer que l'algorisme de cerca de primers sigui més eficient que comprovar si un nombre és divisible per tots els nombres entre 2 i 1 menys que ell mateix? Pots pensar en una altra manera de generar nombres primers?

## [Com provar el vostre codi](https://cs50.harvard.edu/x/2023/problems/1/prime/#how-to-test-your-code)

El vostre programa s'ha de comportar segons els exemples següents.

```
prime/ $ ./prime
Minimum: 1
Maximum: 100
2
3
5
7
11
13
17
19
23
29
31
37
41
43
47
53
59
61
67
71
73
79
83
89
97
```

Podeu comprovar el vostre codi mitjançant `check50`, un programa que CS50 utilitzarà per provar el vostre codi quan l'envieu, escrivint el següent a la `$`sol·licitud. Però assegureu-vos de provar-ho vosaltres mateixos també!

```
check50 cs50/labs/2023/x/prime
```

Les emoticones verdes signifiquen que el vostre programa ha superat una prova! Els cenys vermells indicaran que el vostre programa ha sortit alguna cosa inesperada. Visiteu l'URL que `check50`surt per veure l'entrada `check50`lliurada al vostre programa, quina sortida esperava i quina sortida va donar realment el vostre programa.

Per avaluar que l'estil del vostre codi (sagnis i espaiat) és correcte, escriviu el següent a la `$`sol·licitud.

## [Com enviar](https://cs50.harvard.edu/x/2023/problems/1/prime/#how-to-submit)

No cal enviar! Aquest és un problema de pràctica opcional.