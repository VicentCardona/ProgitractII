## Cançons

![Logotip de Spotify Wrapped '22](https://cs50.harvard.edu/x/2024/psets/7/songs/wrapped.png)

## Problema a resoldre

Escriu consultes SQL per respondre preguntes sobre una base de dades de les 100 cançons més reproduïdes a [Spotify](https://en.wikipedia.org/wiki/Spotify) el 2018.

## Començant

Per a aquest problema, utilitzareu una base de dades anomenada songs.db.

Descarrega el codi de distribució

Obriu el [codi VS.](https://cs50.dev/)

Comenceu fent clic dins de la finestra de la vostra terminal i, a continuació, executeu `cd`\-lo sol. Hauríeu de trobar que la seva "indicació" s'assembla a la següent.
``` 
$
```
Feu clic dins d'aquesta finestra de terminal i, a continuació, executeu

```
wget https://cdn.cs50.net/2023/fall/psets/7/songs.zip
```

seguit d'Enter per baixar un ZIP anomenat `songs.zip`al vostre espai de codi. Aneu amb compte de no passar per alt l'espai entre `wget`i l'URL següent, o qualsevol altre caràcter!

Ara executa
```
unzip songs.zip
```

per crear una carpeta anomenada `songs`. Ja no necessiteu el fitxer ZIP, així que podeu executar-lo
```
rm songs.zip
```
i responeu amb "y" seguit d'Enter a la sol·licitud per eliminar el fitxer ZIP que heu baixat.

Ara escriviu
```
cd songs
```
seguit d'Enter per moure't a (és a dir, obrir) aquest directori. La vostra sol·licitud ara hauria de semblar-se a la següent.
```
songs/ $
```
Si tot ha tingut èxit, hauríeu d'executar
```
ls
```

i hauríeu de veure 8 fitxers .sql, `songs.db`, i `answers.txt`.

Si trobeu cap problema, torneu a seguir aquests mateixos passos i comproveu si podeu determinar on us heu equivocat!

## Comprensió

Se us proporciona un fitxer anomenat `songs.db`, una base de dades SQLite que emmagatzema dades de [Spotify](https://developer.spotify.com/documentation/web-api/) sobre cançons i els seus artistes. Aquest conjunt de dades conté les 100 millors cançons reproduïdes a Spotify el 2018. En una finestra de terminal, executeu-vos `sqlite3 songs.db`perquè pugueu començar a executar consultes a la base de dades.

En primer lloc, quan `sqlite3`se us demani que proporcioneu una consulta, escriviu `.schema`i premeu Intro. Això generarà les declaracions `CREATE TABLE` que s'han utilitzat per generar cadascuna de les taules de la base de dades. En examinar aquestes afirmacions, podeu identificar les columnes presents a cada taula.

Observeu que tots `artist`tenen un `id`i un `name`. Tingueu en compte, també, que cada cançó té un `name`, un `artist_id`(corresponent al `id`de l'artista de la cançó), així com valors de ballabilitat, energia, tonalitat, sonoritat, parla (presència de paraules pronunciades en una pista), valència, tempo i durada de la cançó (mesurada en mil·lisegons).

El repte que teniu per davant és escriure consultes SQL per respondre a una varietat de preguntes diferents seleccionant dades d'una o més d'aquestes taules. Després de fer-ho, reflexionareu sobre les maneres en què Spotify pot utilitzar aquestes mateixes dades a la seva campanya anual [de Spotify Wrapped](https://en.wikipedia.org/wiki/Spotify_Wrapped) per caracteritzar els hàbits dels oients.

## [Detalls d'implementació](https://cs50.harvard.edu/x/2024/psets/7/songs/#implementation-details)

Per a cadascun dels problemes següents, hauríeu d'escriure una única consulta SQL que produeixi els resultats especificats per cada problema. La vostra resposta ha de prendre la forma d'una única consulta SQL, tot i que podeu agrupar altres consultes dins de la vostra consulta. **No hauríeu** d' assumir res sobre les `id`cançons o artistes concrets: les vostres consultes haurien de ser precises encara que la `id`de qualsevol cançó o persona en particular fos diferent. Finalment, cada consulta hauria de retornar només les dades necessàries per respondre la pregunta: si el problema només us demana que escriviu els noms de les cançons, per exemple, aleshores la vostra consulta no hauria de mostrar també el tempo de cada cançó.

1.  A `1.sql`, escriviu una consulta SQL per llistar els noms de totes les cançons de la base de dades.
    -   La vostra consulta hauria de sortir una taula amb una sola columna per al nom de cada cançó.
2.  A `2.sql`, escriviu una consulta SQL per llistar els noms de totes les cançons en ordre creixent de tempo.
    -   La vostra consulta hauria de sortir una taula amb una sola columna per al nom de cada cançó.
3.  A `3.sql`, escriviu una consulta SQL per llistar els noms de les 5 cançons més llargues, en ordre descendent de durada.
    -   La vostra consulta hauria de sortir una taula amb una sola columna per al nom de cada cançó.
4.  A `4.sql`, escriviu una consulta SQL que enumera els noms de les cançons que tinguin capacitat de ballar, energia i valència superiors a 0,75.
    -   La vostra consulta hauria de sortir una taula amb una sola columna per al nom de cada cançó.
5.  A `5.sql`, escriviu una consulta SQL que retorni l'energia mitjana de totes les cançons.
    -   La vostra consulta hauria de generar una taula amb una sola columna i una sola fila que contingui l'energia mitjana.
6.  A `6.sql`, escriviu una consulta SQL que enumere els noms de les cançons que són de Post Malone.
    -   La vostra consulta hauria de sortir una taula amb una sola columna per al nom de cada cançó.
    -   No hauríeu de fer cap suposició sobre què `artist_id`és el de Post Malone.
7.  A `7.sql`, escriviu una consulta SQL que retorni l'energia mitjana de les cançons que són de Drake.
    -   La vostra consulta hauria de generar una taula amb una sola columna i una sola fila que contingui l'energia mitjana.
    -   No hauríeu de fer cap suposició sobre què `artist_id`és el de Drake.
8.  A `8.sql`, escriviu una consulta SQL que enumere els noms de les cançons que inclouen altres artistes.
    -   Les cançons que inclouen altres artistes inclouran "feat". en el nom de la cançó.
    -   La vostra consulta hauria de sortir una taula amb una sola columna per al nom de cada cançó.

## [Pistes](https://cs50.harvard.edu/x/2024/psets/7/songs/#hints)

Consulteu [aquesta referència de paraules clau SQL](https://www.w3schools.com/sql/sql_ref_keywords.asp) per obtenir algunes sintaxis SQL que poden ser útils!


## [Spotify Wrapped](https://cs50.harvard.edu/x/2024/psets/7/songs/#spotify-wrapped)

[Spotify Wrapped](https://en.wikipedia.org/wiki/Spotify_Wrapped) és una funció que presenta les 100 cançons més reproduïdes dels usuaris de Spotify l'any passat. El 2021, Spotify Wrapped va calcular una ["Aura d'àudio"](https://newsroom.spotify.com/2021-12-01/learn-more-about-the-audio-aura-in-your-spotify-2021-wrapped-with-aura-reader-mystic-michaela/) per a cada usuari, una "lectura de \[els seus\] dos estats d'ànim més destacats tal com ho dictaven \[les seves\] millors cançons i artistes de l'any". Suposem que Spotify determina una aura d'àudio observant l'energia mitjana, la valència i la capacitat de ballar de les 100 millors cançons d'una persona de l'any passat. A `answers.txt`, reflexiona sobre les preguntes següents:

-   Si `songs.db`conté les 100 millors cançons d'un oient del 2018, com caracteritzaríeu la seva aura d'àudio?
-   Hipòtesis sobre per què la manera com has calculat aquesta aura pot _no_ ser molt representativa de l'oient. Quines maneres millors de calcular aquesta aura proposaríeu?

Assegureu-vos d'enviar-lo `answers.txt`juntament amb cadascun dels vostres `.sql`fitxers!

## [Com provar](https://cs50.harvard.edu/x/2024/psets/7/songs/#how-to-test)
```
check50 cs50/problems/2024/x/songs
```

### [Correcció](https://cs50.harvard.edu/x/2024/psets/7/songs/#correctness)

```
check50 cs50/problems/2024/x/songs
```

## Agraïments

Conjunt de dades de [Kaggle](https://www.kaggle.com/nadintamer/top-spotify-tracks-of-2018) .

# Crèdits
#### Autor:  Vicent Cardona
#### Departament Tecnologia [Ies Quartó de Portmany](http://iesquartodeportmany.es/)
#### Febrer 2024


Llicència Creative Commons [Reconeixement-NoComercial-CompartirIgual 4.0 Internacional](https://creativecommons.org/licenses/by-nc-sa/4.0/) (CC BY-NC-SA 4.0).

Material adaptat del curs  [Introducció a la informàtica CS50](https://cs50.harvard.edu/x/2023/) compartit amb la mateixa llicència.
