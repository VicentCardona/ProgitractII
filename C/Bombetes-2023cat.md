

## Bombetes no tan trencades


![captura de pantalla de la conferència de la setmana 2 amb tira de bombetes](https://cs50.harvard.edu/x/2023/psets/2/bulbs/binary_bulbs.jpg)

Cada seqüència de bombetes, apagades i enceses codifica un missatge en _binari_ , l'idioma que els ordinadors "parlen". L'objectiu d'aquest programa seria fer missatges secrets.

## Començant

Obriu el [codi VS.](https://cs50.dev/)

Comenceu fent clic dins de la finestra de la vostra terminal i, a continuació, executeu `cd`, sense res. Hauríeu de trobar que la seva "indicació" s'assembla a la següent.
```
$
```

Feu clic dins d'aquesta finestra de terminal i, a continuació, executeu

```
wget https://cdn.cs50.net/2022/fall/psets/2/bulbs.zip
```

seguit, premeu enter per baixar un ZIP anomenat `bulbs.zip`al vostre espai de codi. Aneu amb compte de no passar per alt l'espai entre `wget`i l'URL següent, o qualsevol altre caràcter!

Ara executa
```
unzip bulbs.zip
```

per crear una carpeta anomenada `bulbs`. Ja no necessiteu el fitxer ZIP, així que podeu executar
```
rm  bulbs.zip
```
i responeu amb "y" seguit d'Enter a la sol·licitud per eliminar el fitxer ZIP que heu baixat.

Ara escriviu
```
cd bulbs
```
seguit d'Enter per moure't a (és a dir, obrir) aquest directori. La vostra sol·licitud ara hauria de semblar-se a la següent.
```
bulbs/$
```
Si tot ha anat be, hauríeu d'executar
```
ls
```
i veureu un fitxer anomenat `bulbs.c`. L'execució `code bulbs.c`hauria d'obrir el fitxer on escriureu el codi per a aquest problema. Si no, torna sobre els teus passos i mira si pots determinar on t'has equivocat!

## Detalls d'implementació

Per escriure el nostre programa, primer haurem de pensar en **les bases** .

### Les bases

La _base_ més simple és la base-1, o _unaria_ ; per escriure un nombre, _N_ , en base 1, simplement escriurem _N_ `1`s consecutius. Així, el nombre `4`en base 1 s'escriuria com a `1111`, i el nombre `12`com a `111111111111`. Penseu en això com comptar amb els dits o comptar una puntuació amb marques en un tauler.

Podeu veure per què la base-1 no s'utilitza gaire avui dia. (Els números es fan bastant llargs!) En canvi, una convenció comuna és la base 10, o _decimal_ . En base 10, cada _dígit_ es multiplica per una potència de 10, per tal de representar nombres més grans. Per exemple, `123` és l'abreviatura de $123 = 1 \cdot 10^2 + 2 \cdot 10^1 + 3 \cdot 10^0$.

Canviar la base és tan senzill com canviar el $10$ anterior per un nombre diferent. Per exemple, si heu escrit `123`en base 4, el nombre que realment estaries escrivint és $123 = 1 \cdot 4^2 + 2 \cdot 4^1 + 3 \cdot 4^0$, que és igual al nombre decimal $27$.

Els ordinadors, però, utilitzen base-2 o _binary_ . En binari, escriure `123`seria un error, ja que els nombres binaris només poden tenir `0`s i `1`s. Però el procés d'esbrinar exactament quin nombre decimal representa un nombre binari és exactament el mateix. Per exemple, el nombre `10101`en base 2 representa $1 \cdot 2^4 + 0 \cdot 2^3 + 1 \cdot 2^2 + 0 \cdot 2^1 + 1 \cdot 2^0$, que és igual al nombre decimal $21$.

### Codificació d'un missatge

Les bombetes només poden estar enceses o apagades. En altres paraules, les bombetes representen dos estats possibles; o la bombeta està encesa o la bombeta està apagada, de la mateixa manera que els nombres binaris són 1 o 0. Haurem de trobar una manera de codificar el text com una seqüència de nombres binaris.

Escrivim un programa anomenat `bulbs`que pren un missatge i el converteix en un conjunt de bombetes que podríem mostrar a un públic desprevingut. Ho farem en dos passos:

-   El primer pas consisteix a convertir el text en nombres decimals. Suposem que volem codificar el missatge `HI!`. Afortunadament, ja tenim una convenció establerta sobre com fer-ho, [ASCII](https://asciitable.com/) . Observeu que `H`es representa amb el nombre decimal `72`, `I`es representa amb `73`, i `!`es representa per `33`.
-   El següent pas consisteix a prendre els nostres números decimals (com ara `72`, `73`, i `33`) i convertir-los en nombres binaris equivalents, que només utilitzen 0 i 1. Per tal de tenir un nombre consistent de bits en cadascun dels nostres nombres binaris, suposem que cada decimal es representa amb 8 bits. `72`és `01001000`, `73`és `01001001`i `33`és `00100001`.

Finalment, interpretarem aquests nombres binaris com a instruccions per a unes bombetes; 0 està apagat, 1 està activat. (Trobareu que `bulbs.c`inclou una funció `print_bulb` que s'ha implementat per a vosaltres, que inclou un `0`o `1`i emet emoji que representen bombetes.)

Aquí teniu un exemple de com podria funcionar el programa completat. Imprimirem un byte per línia per a més claredat.
```
# ./bulbs
Message: HI!
⚫🟡⚫⚫🟡⚫⚫⚫
⚫🟡⚫⚫🟡⚫⚫🟡
⚫⚫🟡⚫⚫⚫⚫🟡
```

Per comprovar el nostre treball, podem llegir una bombeta que està encesa ( ![🟡](https://twemoji.maxcdn.com/v/14.0.2/72x72/1f7e1.png)) com a `1`i una bombeta que està apagada ( ![⚫](https://twemoji.maxcdn.com/v/14.0.2/72x72/26ab.png)) com a `0`. Llavors es `HI!` es converteix

```
01001000
01001001
00100001
```

que és precisament el que esperàvem.

Un altre exemple:

```
$./bulbs
Message: HI MOM
⚫🟡⚫⚫🟡⚫⚫⚫
⚫🟡⚫⚫🟡⚫⚫🟡
⚫⚫🟡⚫⚫⚫⚫⚫
⚫🟡⚫⚫🟡🟡⚫🟡
⚫🟡⚫⚫🟡🟡🟡🟡
⚫🟡⚫⚫🟡🟡⚫🟡
```


Tingueu en compte que tots els caràcters s'inclouen a les instruccions de la bombeta, inclosos els caràcters no alfabètics com els espais ( `00100000`).

## Especificació

Dissenyeu i implementeu un programa, `bulbs`, que converteixi el text en instruccions per a la tira de bombetes de la següent manera.
-   Implementeu el vostre programa en un fitxer anomenat `bulbs.c`.
-   El vostre programa primer ha de demanar un missatge a l'usuari amb `get_string`.
-   Aleshores, el vostre programa ha de convertir el donat `string`en una sèrie de nombres binaris de 8 bits, un per a cada caràcter de la cadena.
-   Podeu utilitzar la funció `print_bulb` proporcionada per imprimir una sèrie de `0`s i `1`s com una sèrie d'emojis grocs i negres, que representen bombetes encès i apagat.
-   Cada "byte" de 8 símbols s'hauria d'imprimir en la seva pròpia línia; haurà d'haver un `\n`després de cada darrer "byte" de 8 simbols.
<details>
<summary> Pistes per a decimal a binari</summary>
<br>
Farem un exemple amb el nombre 4. Com convertiríeu 4 en binari? Comenceu tenint en compte el bit més a la dreta, el que, si està activat, afegeix 1 al nombre que estem representant. Necessites aquest bit per estar en 1? Dividiu 4 per 2 per esbrinar:

$4 / 2 = 2$

2 es divideix uniformement en 4, la qual cosa ens indica que no hi ha cap resta d'1 de què preocupar-se. Podem deixar aquesta part més dreta apagada amb seguretat, aleshores:

```
0
```

Que hi ha del següent bit ara? el que està just a l'esquerra del que hem descovert? Per comprovar, anem a seguir un procès similar, pero agafant-ho des d'on ho hem deixat... en el pas anterior, hem dividit 4 per 2 i hem obtingut 2. Ara, 2 es divideix per igual en 2? ho fa, així que no hi ha resta de 2 que ens preocupi:
```
00
```
Ara continuem una mica més. Desprès de dividir 2 per 2, ens queda 1. Dividint 1 per 2 queda una resta d'1. Això vol dir que necessitarem "encendre" aquest bit:
```
100
```
Ara, que hem dividit el nostre nombre fins a 0, no necesite més bits per a representar. Donat conta que hem descovert els bits que representen 4, en l'ordre oposat en el que els imprimim... necesitarem una estructura que ens guardi aquests bits per a poder-los imprimir més endavant.Per suposat, en el vostre codi haureu de treballar amb 'char's de 8 bit, així que hauras de calcular cada 0.

Quan comprovem les restes, el l'operador de mòdul('%') ens es molt útil! '4%2', per exemple, retorna 0, el que vol dir que 2 dividit entre 4 te una resta de 0.
</details>
## Com provar el vostre codi

El vostre programa hauria de comportar-se segons els exemples anteriors. Podeu comprovar el vostre codi mitjançant `check50`, un programa que CS50 utilitzarà per provar el vostre codi quan l'envieu, escrivint el següent al terminal. Però assegureu-vos de provar-ho vosaltres mateixos també!

```
check50 cs50/problems/2023/x/bulbs
```

Per avaluar l'estil del vostre codi, escriviu el següent al terminal:
```
style50 bulbs.c
```

## Com enviar
Entrega al classroom captura d'haver complert la prova 'check50' i entrega el programa.
