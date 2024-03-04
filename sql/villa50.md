## Fiftyville

## Problema a resoldre

Hi ha hagut un robatori a Fiftyville! Ni més ni menys que un ànec de plàstic! La ciutat de Fiftyville us ha cridat a resoldre el misteri 🕵 de l'ànec robat. 
Les autoritats creuen que el lladre va robar l'ànec i després, poc després, va agafar un vol fora de la ciutat 🛫amb l'ajuda d'un còmplice. El vostre objectiu és identificar:

-   Qui és el lladre,
-   A quina ciutat va escapar el lladre
-   Qui és el còmplice del lladre que els va ajudar a escapar

Tot el que sabeu és que el robatori **va tenir lloc el 28 de juliol de 2023** i que va **tenir lloc al carrer Humphrey** .

Com faràs per resoldre aquest misteri? Les autoritats de Fiftyville han agafat alguns dels registres de la ciutat de l'època del robatori i han preparat una base de dades SQLite per a tu, `fiftyville.db`que conté taules de dades de tota la ciutat. Podeu consultar aquesta taula mitjançant consultes SQL `SELECT` per accedir a les dades del vostre interès. Utilitzant només la informació de la base de dades, la vostra tasca és resoldre el misteri.

<iframe width="560" height="315" src="https://www.youtube.com/embed/S5Glfe6UeXQ?si=-KMogeFEwyzXWpG_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Començant

Per a aquest problema, utilitzareu una base de dades que us ha proporcionat el personal de CS50.

Descarrega el codi de distribució

Inicieu sessió a [cs50.dev](https://cs50.dev/) , feu clic a la finestra del vostre terminal i executeu `cd` sol. Hauríeu de trobar que la sol·licitud de la vostra finestra de terminal s'assembla a la següent:

```
$
```
A continuació, executeu

```
wget https://cdn.cs50.net/2023/fall/psets/7/fiftyville.zip
```

per descarregar un ZIP cridat `fiftyville.zip`al vostre espai de codi.

Després executar
```
unzip fiftyville.zip

```

per crear una carpeta anomenada `fiftyville`. Ja no necessiteu el fitxer ZIP, així que podeu executar-lo
```
rm fiftyville.zip
```
i responeu amb "y" seguit d'Enter a la sol·licitud per eliminar el fitxer ZIP que heu baixat.

Ara escriviu
```
cd fiftyville
```
seguit d'Enter per moure't a (és a dir, obrir) aquest directori. La vostra sol·licitud ara hauria de semblar-se a la següent.
```
fiftyville/$
```
Executeu `ls` sol i hauríeu de veure uns quants fitxers:

```
answers.txt  fiftyville.db  log.sql
```

Si trobeu cap problema, torneu a seguir aquests mateixos passos i comproveu si podeu determinar on us heu equivocat!

## Especificació

Per a aquest problema, tan important com resoldre el misteri en si és el procés que feu servir per resoldre el misteri. A `log.sql`, manteniu un registre de totes les consultes SQL que executeu a la base de dades. A sobre de cada consulta, etiqueteu cadascuna amb un comentari (en SQL, els comentaris són les línies que comencen per `--`) que descriguin per què esteu executant la consulta i/o quina informació espereu obtenir d'aquesta consulta en particular. Podeu utilitzar els comentaris al fitxer de registre per afegir notes addicionals sobre el vostre procés de pensament mentre resoleu el misteri: en última instància, aquest fitxer hauria de servir com a prova del procés que heu utilitzat per identificar el lladre!

A mesura que escriviu les vostres consultes, podeu notar que algunes d'elles poden arribar a ser força complexes. Per ajudar a mantenir les vostres consultes llegibles, consulteu els principis del bon estil a [sqlstyle.guide](https://www.sqlstyle.guide/) . La secció [de sagnat](https://www.sqlstyle.guide/#indentation) pot ser especialment útil!

Un cop resolt el misteri, completa cadascuna de les preguntes `answers.txt`escrivint el nom del lladre, la ciutat a la qual va escapar el lladre i el nom del còmplice del lladre que els va ajudar a escapar de la ciutat. (Assegureu-vos de no canviar cap text existent al fitxer ni afegir cap altra línia al fitxer!)

En última instància, hauríeu d'enviar tant els vostres fitxers `log.sql`com els vostres `answers.txt`.

## Pistes

-   Executeu `sqlite3 fiftyville.db`per començar a executar consultes a la base de dades.
    -   Durant l'execució `sqlite3`, l'execució `.tables`llistarà totes les taules de la base de dades.
    -   Mentre s'executa `sqlite3`, executant `.schema TABLE_NAME`, on `TABLE_NAME`és el nom d'una taula a la base de dades, us mostrarà l' `CREATE TABLE`ordre utilitzada per crear la taula. Això pot ser útil per saber quines columnes consultar!
-   Potser us serà útil començar amb la taula `crime_scene_reports`. Comenceu per buscar un informe de l'escena del crim que coincideixi amb la data i la ubicació del crim.
-   Consulteu [aquesta referència de paraules clau SQL](https://www.w3schools.com/sql/sql_ref_keywords.asp) per obtenir algunes sintaxis SQL que poden ser útils!



## Correcció

```
check50 cs50/problems/2024/x/fiftyville
```

## Agraïments

Inspirat en un altre cas a [SQL City](https://mystery.knightlab.com/) .

# Crèdits
#### Autor:  Vicent Cardona
#### Departament Tecnologia [Ies Quartó de Portmany](http://iesquartodeportmany.es/)
#### Març 2024

Llicència Creative Commons [Reconeixement-NoComercial-CompartirIgual 4.0 Internacional](https://creativecommons.org/licenses/by-nc-sa/4.0/) (CC BY-NC-SA 4.0).

Material adaptat del curs  [Introducció a la informàtica CS50](https://cs50.harvard.edu/x/2023/) compartit amb la mateixa llicència.
