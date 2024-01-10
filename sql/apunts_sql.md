-   Les setmanes anteriors, us vam presentar Python, un llenguatge de programació d'alt nivell que utilitzava els mateixos blocs de construcció que vam aprendre en C. Tanmateix, vam introduir aquest nou llenguatge no amb el propòsit d'aprendre "només un altre llenguatge". En canvi, ho fem perquè algunes eines són millors per a algunes feines i no tan bones per a altres!
-   Aquesta setmana, continuarem amb més sintaxis relacionades amb Python.
-   A més, integrarem aquest coneixement amb les dades.
-   Finalment, parlarem de _SQL_ o _Structured Query Language_ on _Query_ es tradueiux com a "consulta".

## Base de dades d'arxiu pla (Flat-File Database)

-   Com probablement heu vist abans, les dades sovint es poden descriure en patrons de columnes i files.
-   Els fulls de càlcul com els creats a Microsoft Excel i Google Sheets es poden enviar a fitxers `csv` o _comma separated values_.
-   Si mireu un fitxer `csv`, notareu que el fitxer és pla perquè totes les nostres dades s'emmagatzemen en una única taula representada per un fitxer de text. Anomenem aquesta forma de dades _base de dades d'arxiu pla_.
-   Python inclou suport natiu per a fitxers `csv`.
-   Primer, descarregueu [favorites.csv](https://cdn.cs50.net/2023/fall/lectures/7/src7/favorites/favorites.csv) i pengeu-lo a l'explorador de fitxers, executeu `code favorites.py` i escriviu el codi de la manera següent:
```  pyhthon
# Imprimeix tots els llenguatges favorits usant csv.reader

import csv

# Obre fitxer CSV
with open("favorites.csv", "r") as arxiu:

    # crea lectura
    lector = csv.reader(arxiu)

    # Salta la fila d'encapçalament 
    next(lector)
    # Itera a l'arxiu CSV, imprimint cada favorit.
    for row in reader:
        print(row[1])
```   
