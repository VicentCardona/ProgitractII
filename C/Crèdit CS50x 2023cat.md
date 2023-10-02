## [Crèdit](https://cs50.harvard.edu/x/2023/psets/1/credit/#credit)

## [Començant](https://cs50.harvard.edu/x/2023/psets/1/credit/#getting-started)

Obriu el [codi VS.](https://cs50.dev/)

Comenceu fent clic dins de la finestra de la vostra terminal i, a continuació, executeu `cd`\-lo sol. Hauríeu de trobar que la seva "indicació" s'assembla a la següent.

Feu clic dins d'aquesta finestra de terminal i, a continuació, executeu

```
wget https://cdn.cs50.net/2022/fall/psets/1/credit.zip
```

seguit d'Enter per baixar un ZIP anomenat `credit.zip`al vostre espai de codi. Aneu amb compte de no passar per alt l'espai entre `wget`i l'URL següent, o qualsevol altre caràcter!

Ara executa

per crear una carpeta anomenada `credit`. Ja no necessiteu el fitxer ZIP, així que podeu executar-lo

i responeu amb "y" seguit d'Enter a la sol·licitud per eliminar el fitxer ZIP que heu baixat.

Ara escriviu

seguit d'Enter per moure't a (és a dir, obrir) aquest directori. La vostra sol·licitud ara hauria de semblar-se a la següent.

Si tot ha tingut èxit, hauríeu d'executar

i vegeu un fitxer anomenat `credit.c`. L'execució `code credit.c`hauria d'obrir el fitxer on escriureu el codi per a aquest conjunt de problemes. Si no, torna sobre els teus passos i mira si pots determinar on t'has equivocat!

## [Targetes de crèdit](https://cs50.harvard.edu/x/2023/psets/1/credit/#credit-cards)

Una targeta de crèdit (o dèbit), és clar, és una targeta de plàstic amb la qual pots pagar béns i serveis. En aquesta targeta hi ha imprès un número que també s'emmagatzema en una base de dades en algun lloc, de manera que quan la vostra targeta s'utilitza per comprar alguna cosa, el creditor sàpiga a qui facturar. Hi ha molta gent amb targetes de crèdit en aquest món, de manera que aquests números són bastant llargs: American Express utilitza números de 15 dígits, MasterCard utilitza números de 16 dígits i Visa utilitza números de 13 i 16 dígits. I aquests són nombres decimals (del 0 al 9), no binaris, el que significa, per exemple, que American Express podria imprimir fins a 10 ^ 15 = 1.000.000.000.000.000 de targetes úniques! (Això és, um, un quadrilió.)

De fet, això és una mica exagerat, perquè els números de targeta de crèdit tenen alguna estructura. Tots els números d'American Express comencen amb 34 o 37; la majoria dels números de MasterCard comencen amb 51, 52, 53, 54 o 55 (també tenen altres números inicials potencials dels quals no ens preocuparem per aquest problema); i tots els números de Visa comencen amb 4. Però els números de targeta de crèdit també tenen incorporada una "suma de control", una relació matemàtica entre almenys un nombre i altres. Aquesta suma de comprovació permet als ordinadors (o als humans als quals els agraden les matemàtiques) detectar errors ortogràfics (per exemple, transposicions), si no números fraudulents, sense haver de consultar una base de dades, cosa que pot ser lenta. Per descomptat, un matemàtic deshonest podria crear un nombre fals que, tanmateix, respecti la restricció matemàtica,

## [Algoritme de Luhn](https://cs50.harvard.edu/x/2023/psets/1/credit/#luhns-algorithm)

Aleshores, quina és la fórmula secreta? Bé, la majoria de targetes utilitzen un algorisme inventat per Hans Peter Luhn d'IBM. Segons l'algorisme de Luhn, podeu determinar si un número de targeta de crèdit és (sintàcticament) vàlid de la següent manera:

1.  Multipliqueu tots els altres dígits per 2, començant pel penúltim dígit del número i, a continuació, sumeu els dígits d'aquests productes.
2.  Sumeu la suma a la suma dels dígits que no s'han multiplicat per 2.
3.  Si l'últim dígit del total és 0 (o, de manera més formal, si el mòdul total 10 és congruent amb 0), el nombre és vàlid!

Això és una mica confús, així que provem un exemple amb el visat de David: 4003600000000014.

1.  Per a la discussió, primer subratllem tots els altres dígits, començant pel penúltim dígit del número:
    
    4 0 0 3 6 0 0 0 0 0 0 0 0 0 1 4
    
    D'acord, multipliquem per 2 cadascun dels dígits subratllats:
    
    1•2 + 0•2 + 0•2 + 0•2 + 0•2 + 6•2 + 0•2 + 4•2
    
    Això ens dóna:
    
    2+0+0+0+0+12+0+8
    
    Ara sumem els dígits d'aquests productes (és a dir, no els mateixos productes) junts:
    
    2 + 0 + 0 + 0 + 0 + 1 + 2 + 0 + 8 = 13
    
2.  Ara sumem aquesta suma (13) a la suma dels dígits que no s'han multiplicat per 2 (començant pel final):
    
    13 + 4 + 0 + 0 + 0 + 0 + 0 + 3 + 0 = 20
    
3.  Sí, l'últim dígit d'aquesta suma (20) és un 0, així que la targeta de David és legítima!
    

Per tant, validar els números de targeta de crèdit no és difícil, però es fa una mica tediós a mà. Escrivim un programa.

## [Detalls d'implementació](https://cs50.harvard.edu/x/2023/psets/1/credit/#implementation-details)

Al fitxer anomenat `credit.c`al `credit`directori, escriviu un programa que demani a l'usuari un número de targeta de crèdit i després informi (mitjançant `printf`) si és un número de targeta American Express, MasterCard o Visa vàlid, segons les definicions del format de cadascun d'ells aquí. Perquè puguem automatitzar algunes proves del vostre codi, us demanem que l'última línia de sortida del vostre programa sigui `AMEX\n`o `MASTERCARD\n`o `VISA\n`o `INVALID\n`, ni més ni menys. Per simplificar, podeu suposar que l'entrada de l'usuari serà completament numèrica (és a dir, sense guions, com podria estar imprès en una targeta real) i que no tindrà zeros inicials. Però no suposeu que l'entrada de l'usuari encaixarà en un `int`! És millor utilitzar `get_long`\-lo des de la biblioteca de CS50 per obtenir les aportacions dels usuaris. (Per què?)

Considereu el següent representant de com s'ha de comportar el vostre propi programa quan se li passa un número de targeta de crèdit vàlid (sense guions).

```
$ ./credit
Number: 4003600000000014
VISA
```

Ara, `get_long`ell mateix rebutjarà els guions (i més) de totes maneres:

```
$ ./credit
Number: 4003-6000-0000-0014
Number: foo
Number: 4003600000000014
VISA
```

Però depèn de vostè captar les entrades que no siguin números de targeta de crèdit (per exemple, un número de telèfon), encara que siguin numèrics:

```
$ ./credit
Number: 6176292929
INVALID
```

Proveu el vostre programa amb un munt d'entrades, tant vàlides com no vàlides. (Segur que ho farem!) Aquí teniu alguns [números de targeta](https://developer.paypal.com/api/nvp-soap/payflow/integration-guide/test-transactions/#standard-test-cards) que PayPal recomana per provar.

Si el vostre programa es comporta incorrectament en algunes entrades (o no es compila en absolut), és hora de depurar!

### [Tutorial](https://cs50.harvard.edu/x/2023/psets/1/credit/#walkthrough)

<iframe allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" data-video="" src="https://www.youtube.com/embed/dF7wNjsRBjI?modestbranding=0&amp;rel=0&amp;showinfo=0" data-ruffle-polyfilled="" scrolling="no" id="iFrameResizer0"></iframe>

### [Com provar el vostre codi](https://cs50.harvard.edu/x/2023/psets/1/credit/#how-to-test-your-code)

També podeu executar el següent per avaluar la correcció del vostre codi mitjançant `check50`. Però assegureu-vos de compilar-lo i provar-lo vosaltres mateixos també!

```
check50 cs50/problems/2023/x/credit
```

Executeu el següent per avaluar l'estil del vostre codi amb `style50`.

## [Com enviar](https://cs50.harvard.edu/x/2023/psets/1/credit/#how-to-submit)

Al vostre terminal, executeu el següent per enviar el vostre treball.

```
submit50 cs50/problems/2023/x/credit
```