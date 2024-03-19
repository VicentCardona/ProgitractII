# HTML, CSS, Javascript
## Encaminadors (Routers)
-   Per encaminar les dades d'un lloc a un altre, hem de prendre _decisions d'encaminament_ . És a dir, algú ha de programar com es transfereixen les dades del punt A al punt B.
-   Us podeu imaginar com les dades podrien agafar diversos camins des del punt A i del punt B, de manera que quan un encaminador està congestionat, les dades poden fluir per un altre camí. _Els paquets_ de dades es transfereixen d'un encaminador a un altre, d'un ordinador a un altre.
-   _TCP/IP_ són dos protocols que permeten als ordinadors transferir dades entre ells a través d'Internet.
-   _IP_ o _protocol d'Internet_ és una manera per la qual els ordinadors es poden identificar entre ells a través d'Internet. Cada ordinador té una adreça única al món. Les adreces són d'aquesta forma:
    
-   Els nombres van de `0`a `255`. Les adreces IP són de 32 bits, el que significa que aquestes adreces podrien allotjar més de 4 mil milions d'adreces. Les versions més noves de l'adreça IP, que implementen 128 bits, poden allotjar molts més ordinadors!
-   Al món real, els servidors ens fan molta feina.
-   Els paquets s'estructuren de la següent manera:
    
    ![art ascii d'un paquet](https://cs50.harvard.edu/x/2024/notes/8/cs50Week8Slide014.png "paquets")
    
-   Els paquets estan estandarditzats. La font i la destinació es mantenen dins de cada paquet.
-   _TCP_ , o protocol de control de transmissió, s'utilitza per distingir els serveis web entre si. Per exemple, `80`s'utilitza per indicar HTTP i `443`s'utilitza per denotar HTTPS. Aquests números són _números de port_ .
-   Quan s'envia informació d'una ubicació a una altra, s'envia una adreça IP d'origen, una adreça IP de destinació i un número de port TCP.
-   Aquests protocols també s'utilitzen per fragmentar fitxers grans en diverses parts o paquets. Per exemple, una foto gran d'un gat es pot enviar en diversos paquets. Quan es perd un paquet, TCP/IP pot sol·licitar de nou els paquets que falten al servidor d'origen.
-   TCP reconeixerà quan totes les dades s'han transmès i rebut.

## DNS

-   Seria molt tediós si haguéssiu de recordar una adreça IP per visitar un lloc web.
-   _DNS_ , o _sistemes de noms de domini_ , és una col·lecció de servidors a Internet que s'utilitzen per encaminar adreces de llocs web com _harvard.edu_ a una adreça IP específica.
-   El DNS només conté una taula o base de dades que enllaça noms de domini específics i totalment qualificats amb adreces IP específiques.

## HTTP

-   _HTTP_ o _protocol de transferència d'hipertext_ és un protocol a nivell d'aplicació que els desenvolupadors utilitzen per crear coses potents i útils mitjançant la transferència de dades d'un lloc a un altre.
-   Quan veieu una adreça com la que `https://www.example.com`esteu visitant implícitament amb una `/`al final.
-   El _camí_ és el que existeix després d'aquesta barra. Per exemple, `https://www.example.com/folder/file.html`visita `example.com`i navega a la `folder`carpeta i després visita el fitxer anomenat `file.html`.
-   S'anomena `.com`domini _de primer nivell_ que s'utilitza per indicar la ubicació o el tipus d'organització associada a aquesta adreça.
-   `https`en aquesta adreça hi ha el protocol que s'utilitza per connectar-se a aquesta adreça web. Per protocol, entenem que HTTP utilitza `GET`o `POST` _sol·licita_ informació d'un servidor. Per exemple, podeu iniciar Google Chrome, fer clic amb el botó dret i fer clic a `inspect`. Quan obriu `developer tools`i visiteu `Network`, seleccionant `Preserve log`, veureu `Request Headers`. Veureu mencions de `GET`. Això també és possible en altres navegadors, utilitzant mètodes lleugerament diferents.
-   Per exemple, quan emet una sol·licitud GET, el vostre ordinador pot enviar el següent a un servidor:
    
    ```
      GET / HTTP/2
      Host: www.harvard.edu
    ```
    
    Tingueu en compte que això sol·licita mitjançant HTTP el contingut que es publica a www.harvard.edu
    
-   En general, després de fer una sol·licitud a un servidor, rebreu el següent a `Response Headers`:
    
    ```
      HTTP/2 200
      Content-Type: text/html
    ```
    
-   Aquest enfocament per inspeccionar aquests registres pot ser una mica més complicat del que cal. Podeu analitzar el treball dels protocols HTTP a [cs50.dev](https://cs50.dev/) . Per exemple, escriviu el següent a la finestra del vostre terminal:
    
    ```
      curl -I https://www.harvard.edu/
    ```
    
    Observeu que la sortida d'aquesta ordre retorna tots els valors de capçalera de les respostes del servidor.
    
-   Mitjançant les eines de desenvolupament del vostre navegador web, podeu veure totes les sol·licituds HTTP quan navegueu al lloc web anterior.
-   A més, executeu l'ordre següent a la finestra del vostre terminal:
    
    ```
      curl -I https://harvard.edu
    ```
    
    Tingueu en compte que veureu una `301`resposta, proporcionant una pista a un navegador d'on pot trobar el lloc web correcte.
    
-   De la mateixa manera, executeu el següent a la finestra del vostre terminal:
    
    ```
      curl -I http://www.harvard.edu/
    ```
    
    Observeu que l' `s`entrada `https`s'ha eliminat. La resposta del servidor mostrarà que la resposta és `301`, és a dir, que el lloc web s'ha mogut permanentment.
    
-   Similar a `301`, un codi de `404`significa que no s'ha trobat un URL especificat. Hi ha molts altres codis de resposta, com ara:
    
    ```
      200 OK
      301 Moved Permanently
      302 Found
      304 Not Modified
      304 Temporary Redirect
      401 Unauthorized
      403 Forbidden
      404 Not Found
      418 I'm a Teapot
      500 Internal Server Error
      503 Service Unavailable
    ```
    
-   Val la pena esmentar que `500`els errors sempre són culpa vostra com a desenvolupador. Això serà especialment important per al conjunt de problemes de la setmana vinent i, potencialment, per al vostre projecte final!

## HTML

-   _El llenguatge de marques_ _HTML_ o d'hipertext està format per _etiquetes_ , cadascuna de les quals pot tenir alguns _atributs_ que el descriuen.
-   Al terminal, escriviu `code hello.html`i escriviu el codi de la següent manera:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates HTML -->
    
    <html lang="en">
        <head>
            <title>hello, title</title>
        </head>
        <body>
            hello, body
        </body>
    </html>
    ```
    
    Observeu que l' `html`etiqueta obre i tanca aquest fitxer. A més, observeu l' `lang`atribut, que modifica el comportament de l' `html`etiqueta. A més, tingueu en compte que hi ha `head`etiquetes i `body`etiquetes. El sagnat no és necessari, però suggereix una jerarquia.
    
-   Podeu enviar el vostre codi escrivint `http-server`. Aquest servei ara està disponible en un URL molt llarg. Si hi feu clic, podeu visitar el lloc web amb el vostre propi codi.
-   Quan visiteu aquest URL, observeu que el nom del fitxer `hello.html`apareix al final d'aquest URL. A més, tingueu en compte, segons l'URL, que el servidor serveix a través del port 8080.
-   La jerarquia d'etiquetes es pot representar de la següent manera:
    
    ![codi html al costat d'una jerarquia que mostra els nodes pare i fill](https://cs50.harvard.edu/x/2024/notes/8/cs50Week8Slide065.png "DOM")
    
-   El coneixement d'aquesta jerarquia serà útil més endavant a mesura que aprenem JavaScript.
-   El navegador llegirà el vostre fitxer HTML de dalt a baix i d'esquerra a dreta.
-   Com que els espais en blanc i el sagnat s'ignoren de manera efectiva en HTML, haureu d'utilitzar `<p>`etiquetes de paràgraf per obrir i tancar un paràgraf. Tingueu en compte el següent:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates paragraphs -->
    
    <html lang="en">
        <head>
            <title>paragraphs</title>
        </head>
        <body>
            <p>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus convallis scelerisque quam, vel hendrerit lectus viverra eu. Praesent posuere eget lectus ut faucibus. Etiam eu velit laoreet, gravida lorem in, viverra est. Cras ut purus neque. In porttitor non lorem id lobortis. Mauris gravida metus libero, quis maximus dui porta at. Donec lacinia felis consectetur venenatis scelerisque. Nulla eu nisl sollicitudin, varius velit sit amet, vehicula erat. Curabitur sollicitudin felis sit amet orci mattis, a tempus nulla pulvinar. Aliquam erat volutpat.
            </p>
            <p>
                Mauris ut dui in eros semper hendrerit. Morbi vel elit mi. Sed sit amet ex non quam dignissim dignissim et vel arcu. Pellentesque eget elementum orci. Morbi ac cursus ex. Pellentesque quis turpis blandit orci dapibus semper sed non nunc. Nulla et dolor nec lacus finibus volutpat. Sed non lorem diam. Donec feugiat interdum interdum. Vivamus et justo in enim blandit fermentum vel at elit. Phasellus eu ante vitae ligula varius aliquet. Etiam id posuere nibh.
            </p>
            <p>
                Aenean venenatis convallis ante a rhoncus. Nullam in metus vel diam vehicula tincidunt. Donec lacinia metus sem, sit amet egestas elit blandit sit amet. Nunc egestas sem quis nisl mattis semper. Pellentesque ut magna congue lorem eleifend sodales. Donec tortor tortor, aliquam vitae mollis sed, interdum ut lectus. Mauris non purus quis ipsum lacinia tincidunt.
            </p>
            <p>
                Integer at justo lacinia libero blandit aliquam ut ut dui. Quisque tincidunt facilisis venenatis. Nullam dictum odio quis lorem luctus, vel malesuada dolor luctus. Aenean placerat faucibus enim a facilisis. Maecenas eleifend quis massa sed eleifend. Ut ultricies, dui ac vulputate hendrerit, ex metus iaculis diam, vitae fermentum libero dui et ante. Phasellus suscipit, arcu ut consequat sagittis, massa urna accumsan massa, eu aliquet nulla lorem vitae arcu. Pellentesque rutrum felis et metus porta semper. Nam ac consectetur mauris.
            </p>
            <p>
                Suspendisse rutrum vestibulum odio, sed venenatis purus condimentum sed. Morbi ornare tincidunt augue eu auctor. Vivamus sagittis ac lectus at aliquet. Nulla urna mauris, interdum non nibh in, vehicula porta enim. Donec et posuere sapien. Pellentesque ultrices scelerisque ipsum, vel fermentum nibh tincidunt et. Proin gravida porta ipsum nec scelerisque. Vestibulum fringilla erat at turpis laoreet, nec hendrerit nisi scelerisque.
            </p>
            <p>
                Sed quis malesuada mi. Nam id purus quis augue sagittis pharetra. Nulla facilisi. Maecenas vel fringilla ante. Cras tristique, arcu sit amet blandit auctor, urna elit ultricies lacus, a malesuada eros dui id massa. Aliquam sem odio, pretium vel cursus eget, scelerisque at urna. Vestibulum posuere a turpis consectetur consectetur. Cras consequat, risus quis tempor egestas, nulla ipsum ornare erat, nec accumsan nibh lorem nec risus. Integer at iaculis lacus. Integer congue nunc massa, quis molestie felis pellentesque vestibulum. Nulla odio tortor, aliquam nec quam in, ornare aliquet sapien.
            </p>
        </body>
    </html>
    ```
    
    Tingueu en compte que els paràgrafs comencen amb una `<p>`etiqueta i acaben amb una `</p>`etiqueta.
    
-   HTML permet la representació d'encapçalaments:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates headings (for chapters, sections, subsections, etc.) -->
    
    <html lang="en">
    
        <head>
            <title>headings</title>
        </head>
    
        <body>
    
            <h1>One</h1>
            <p>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus convallis scelerisque quam, vel hendrerit lectus viverra eu. Praesent posuere eget lectus ut faucibus. Etiam eu velit laoreet, gravida lorem in, viverra est. Cras ut purus neque. In porttitor non lorem id lobortis. Mauris gravida metus libero, quis maximus dui porta at. Donec lacinia felis consectetur venenatis scelerisque. Nulla eu nisl sollicitudin, varius velit sit amet, vehicula erat. Curabitur sollicitudin felis sit amet orci mattis, a tempus nulla pulvinar. Aliquam erat volutpat.
            </p>
    
            <h2>Two</h2>
            <p>
                Mauris ut dui in eros semper hendrerit. Morbi vel elit mi. Sed sit amet ex non quam dignissim dignissim et vel arcu. Pellentesque eget elementum orci. Morbi ac cursus ex. Pellentesque quis turpis blandit orci dapibus semper sed non nunc. Nulla et dolor nec lacus finibus volutpat. Sed non lorem diam. Donec feugiat interdum interdum. Vivamus et justo in enim blandit fermentum vel at elit. Phasellus eu ante vitae ligula varius aliquet. Etiam id posuere nibh.
            </p>
    
            <h3>Three</h3>
            <p>
                Aenean venenatis convallis ante a rhoncus. Nullam in metus vel diam vehicula tincidunt. Donec lacinia metus sem, sit amet egestas elit blandit sit amet. Nunc egestas sem quis nisl mattis semper. Pellentesque ut magna congue lorem eleifend sodales. Donec tortor tortor, aliquam vitae mollis sed, interdum ut lectus. Mauris non purus quis ipsum lacinia tincidunt.
            </p>
    
            <h4>Four</h4>
            <p>
                Integer at justo lacinia libero blandit aliquam ut ut dui. Quisque tincidunt facilisis venenatis. Nullam dictum odio quis lorem luctus, vel malesuada dolor luctus. Aenean placerat faucibus enim a facilisis. Maecenas eleifend quis massa sed eleifend. Ut ultricies, dui ac vulputate hendrerit, ex metus iaculis diam, vitae fermentum libero dui et ante. Phasellus suscipit, arcu ut consequat sagittis, massa urna accumsan massa, eu aliquet nulla lorem vitae arcu. Pellentesque rutrum felis et metus porta semper. Nam ac consectetur mauris.
            </p>
    
            <h5>Five</h5>
            <p>
                Suspendisse rutrum vestibulum odio, sed venenatis purus condimentum sed. Morbi ornare tincidunt augue eu auctor. Vivamus sagittis ac lectus at aliquet. Nulla urna mauris, interdum non nibh in, vehicula porta enim. Donec et posuere sapien. Pellentesque ultrices scelerisque ipsum, vel fermentum nibh tincidunt et. Proin gravida porta ipsum nec scelerisque. Vestibulum fringilla erat at turpis laoreet, nec hendrerit nisi scelerisque.
            </p>
    
            <h6>Six</h6>
            <p>
                Sed quis malesuada mi. Nam id purus quis augue sagittis pharetra. Nulla facilisi. Maecenas vel fringilla ante. Cras tristique, arcu sit amet blandit auctor, urna elit ultricies lacus, a malesuada eros dui id massa. Aliquam sem odio, pretium vel cursus eget, scelerisque at urna. Vestibulum posuere a turpis consectetur consectetur. Cras consequat, risus quis tempor egestas, nulla ipsum ornare erat, nec accumsan nibh lorem nec risus. Integer at iaculis lacus. Integer congue nunc massa, quis molestie felis pellentesque vestibulum. Nulla odio tortor, aliquam nec quam in, ornare aliquet sapien.
            </p>
    
        </body>
    
    </html>
    ```
    
    Observeu que `<h1>`, `<h2>`, i `<h3>`denoten diferents nivells d'encapçalaments.
    
-   També podem crear llistes no ordenades dins d'HTML:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates (ordered) lists -->
    
    <html lang="en">
        <head>
            <title>list</title>
        </head>
        <body>
            <ul>
                <li>foo</li>
                <li>bar</li>
                <li>baz</li>
            </ul>
        </body>
    </html>
    ```
    
    Observeu que l' `<ul>`etiqueta crea una llista no ordenada que conté tres elements.
    
-   També podem crear llistes ordenades dins d'HTML:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates (ordered) lists -->
    
    <html lang="en">
        <head>
            <title>list</title>
        </head>
        <body>
            <ol>
                <li>foo</li>
                <li>bar</li>
                <li>baz</li>
            </ol>
        </body>
    </html>
    ```
    
    Observeu que l' `<ol>`etiqueta crea una llista ordenada que conté tres elements.
    
-   També podem crear una taula en HTML:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates table -->
    
    <html lang="en">
        <head>
            <title>table</title>
        </head>
        <body>
            <table>
                <tr>
                    <td>1</td>
                    <td>2</td>
                    <td>3</td>
                </tr>
                <tr>
                    <td>4</td>
                    <td>5</td>
                    <td>6</td>
                </tr>
                <tr>
                    <td>7</td>
                    <td>8</td>
                    <td>9</td>
                </tr>
                <tr>
                    <td>*</td>
                    <td>0</td>
                    <td>#</td>
                </tr>
            </table>
        </body>
    </html>
    ```
    
    Les taules també tenen etiquetes que obren i tanquen cada element. A més, tingueu en compte la sintaxi dels comentaris en HTML.
    
-   Les imatges també es poden utilitzar dins d'HTML:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates image -->
    
    <html lang="en">
        <head>
            <title>image</title>
        </head>
        <body>
            <img alt="photo of bridge" src="bridge.png">
        </body>
    </html>
    ```
    
    Observeu que `src="bridge.png"`indica el camí on es pot localitzar el fitxer d'imatge.
    
-   Els vídeos també es poden incloure en HTML:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates video -->
    
    <html lang="en">
        <head>
            <title>video</title>
        </head>
        <body>
            <video controls muted>
                <source src="video.mp4" type="video/mp4">
            </video>
        </body>
    </html>
    ```
    
    Tingueu en compte que l' `type`atribut indica que es tracta d'un vídeo del tipus `mp4`. A més, observeu com `controls`i `muted`es passen a `video`.
    
-   També podeu enllaçar entre diverses pàgines web:
-   
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates link -->
    
    <html lang="en">
        <head>
            <title>link</title>
        </head>
        <body>
           Visit <a href="https://www.harvard.edu">Harvard</a>.
        </body>
    </html>
    ```
    
    Tingueu en compte que l' etiqueta _d'ancoratge_`<a>` o s'utilitza per fer un text enllaçable.`Harvard`
    
-   Les metaetiquetes s'utilitzen per contenir informació sobre les dades dins del fitxer HTML. Tingueu en compte el següent:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates responsive design -->
    
    <html lang="en">
        <head>
            <meta name="viewport" content="initial-scale=1, width=device-width">
            <title>meta</title>
        </head>
        <body>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus convallis scelerisque quam, vel hendrerit lectus viverra eu. Praesent posuere eget lectus ut faucibus. Etiam eu velit laoreet, gravida lorem in, viverra est. Cras ut purus neque. In porttitor non lorem id lobortis. Mauris gravida metus libero, quis maximus dui porta at. Donec lacinia felis consectetur venenatis scelerisque. Nulla eu nisl sollicitudin, varius velit sit amet, vehicula erat. Curabitur sollicitudin felis sit amet orci mattis, a tempus nulla pulvinar. Aliquam erat volutpat.
        </body>
    </html>
    ```
    
    Tingueu en compte que aquest conjunt d' `meta`atributs fa que aquesta pàgina sigui adaptada per a mòbils.
    
-   Hi ha nombrosos `meta`parells clau-valor que podeu utilitzar:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates Open Graph tags -->
    
    <html lang="en">
        <head>
            <meta property="og:title" content="CS50">
            <meta property="og:description" content="Introduction to the intellectual enterprises of computer science and the art of programming.">
            <meta property="og:image" content="cat.jpg">
            <title>meta</title>
        </head>
        <body>
            ...
        </body>
    </html>
    ```
    
    Tingueu en compte que aquests parells de valors clau es relacionen amb `title`i `description`de la pàgina web.
    
-   També podeu crear formularis que recordin la cerca de Google:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates form -->
    
    <html lang="en">
        <head>
            <title>search</title>
        </head>
        <body>
            <form action="https://www.google.com/search" method="get">
                <input name="q" type="search">
                <input type="submit" value="Google Search">
            </form>
        </body>
    </html>
    ```
    
    Observeu que `form`s'obre una etiqueta i proporciona l'atribut del que `action`necessitarà. `input`S'inclou el camp, passant el nom `q`i el tipus com a `search`.
    
-   Podem millorar aquesta cerca de la següent manera:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates additional form attributes -->
    
    <html lang="en">
        <head>
            <title>search</title>
        </head>
        <body>
            <form action="https://www.google.com/search" method="get">
                <input autocomplete="off" autofocus name="q" placeholder="Query" type="search">
                <button>Google Search</button>
            </form>
        </body>
    </html>
    ```
    
    Observeu que `autocomplete`està girat `off`. `autofocus`està habilitat.
    
-   Hem vist només alguns dels molts elements HTML que podeu afegir al vostre lloc. Si teniu alguna idea per afegir al vostre lloc que encara no hem vist (un botó, un fitxer d'àudio, etc.), proveu a Google "X en HTML" per trobar la sintaxi correcta! De la mateixa manera, podeu utilitzar [cs50.ai](https://cs50.ai/) per ajudar-vos a descobrir més funcions HTML!

##[Expressions regulars

-   _Les expressions regulars_ o _Regular Expressions_ són un mitjà per garantir que les dades proporcionades per l'usuari s'ajustin a un format específic.
-   Podem implementar la nostra pròpia pàgina de registre que utilitza execucions regulars de la següent manera:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates type="email" -->
    
    <html lang="en">
        <head>
            <title>register</title>
        </head>
        <body>
            <form>
                <input autocomplete="off" autofocus name="email" placeholder="Email" type="email">
                <button>Register</button>
            </form>
        </body>
    </html>
    ```
    
    Observeu que l' `input`etiqueta inclou atributs que indiquen que és del tipus `email`. El navegador sap que ha de comprovar que l'entrada és una adreça de correu electrònic.
    
-   Tot i que el navegador utilitza aquests atributs integrats per comprovar si hi ha una adreça de correu electrònic, podem afegir un `pattern`atribut per assegurar-nos que només les dades específiques acabin a l'adreça de correu electrònic:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates pattern attribute -->
    
    <html lang="en">
        <head>
            <title>register</title>
        </head>
        <body>
            <form>
                <input autocomplete="off" autofocus name="email" pattern=".+@.+\.edu" placeholder="Email" type="email">
                <button>Register</button>
            </form>
        </body>
    </html>
    ```
    
    Tingueu en compte que l' `pattern`atribut rep una expressió regular per indicar que l'adreça de correu electrònic ha d'incloure un `@`símbol i un `.edu`.
    
-   Podeu obtenir més informació sobre les expressions regulars a [la documentació de Mozilla](https://cs50.harvard.edu/x/2024/notes/8/developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions) . A més, podeu fer consultes a [cs50.ai](https://cs50.ai/) per obtenir suggeriments.

## CSS

-   `CSS`, o _full d'estil en cascada_ , és un llenguatge de marques que us permet afinar l'estètica dels vostres fitxers HTML.
-   CSS està ple de _propietats_ , que inclouen parells clau-valor.
-   Al terminal, escriviu `code home.html`i escriviu el codi de la següent manera:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates inline CSS with P tags -->
    
    <html lang="en">
        <head>
            <title>css</title>
        </head>
        <body>
            <p style="font-size: large; text-align: center;">
                John Harvard
            </p>
            <p style="font-size: medium; text-align: center;">
                Welcome to my home page!
            </p>
            <p style="font-size: small; text-align: center;">
                Copyright &amp;#169; John Harvard
            </p>
        </body>
    </html>
    ```
    
    Tingueu en compte que alguns `style`atributs es proporcionen a les `<p>`etiquetes. S'estableix `font-size`en `large`, `medium`, o `small`. Després `text-align`es posa al centre.
    
-   Tot i que és correcte, l'anterior no està ben dissenyat. Podem eliminar la redundància modificant el nostre codi de la següent manera:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Removes outer DIV -->
    
    <html lang="en">
        <head>
            <title>css</title>
        </head>
        <body style="text-align: center">
            <div style="font-size: large">
                John Harvard
            </div>
            <div style="font-size: medium">
                Welcome to my home page!
            </div>
            <div style="font-size: small">
                Copyright &amp;#169; John Harvard
            </div>
        </body>
    </html>
    ```
    
    Tingueu en compte que `<div>`les etiquetes s'utilitzen per dividir aquest fitxer HTML en regions específiques. `text-align: center`s'invoca a tot el cos de l'HTML. Com que tot el que hi ha a dins `body`és fill de `body`, l' `center`atribut cau en cascada a aquests nens.
    
-   Resulta que hi ha etiquetes semàntiques més noves que s'inclouen a HTML. Podem modificar el nostre codi de la següent manera:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Uses semantic tags instead of DIVs -->
    
    <html lang="en">
        <head>
            <title>css</title>
        </head>
        <body style="text-align: center">
            <header style="font-size: large">
                John Harvard
            </header>
            <main style="font-size: medium">
                Welcome to my home page!
            </main>
            <footer style="font-size: small">
                Copyright &amp;#169; John Harvard
            </footer>
        </body>
    </html>
    ```
    
    Observeu que els `header`i `footer`tots dos tenen diferents estils assignats.
    
-   Aquesta pràctica de col·locar l'estil i la informació al mateix lloc no és una bona pràctica. Podríem moure els elements d'estil a la part superior del fitxer de la següent manera:
    
    ``` html
    <!-- Demonstrates class selectors -->
    
    <html lang="en">
        <head>
            <style>
    
                .centered
                {
                    text-align: center;
                }
    
                .large
                {
                    font-size: large;
                }
    
                .medium
                {
                    font-size: medium;
                }
    
                .small
                {
                    font-size: small;
                }
    
            </style>
            <title>css</title>
        </head>
        <body class="centered">
            <header class="large">
                John Harvard
            </header>
            <main class="medium">
                Welcome to my home page!
            </main>
            <footer class="small">
                Copyright &amp;#169; John Harvard
            </footer>
        </body>
    </html>
    ```
    
    Observeu que totes les etiquetes d'estil es col·loquen a `head`l'embolcall de l' `style`etiqueta. Observeu també que hem assignat _classes_ , anomenades `centered`, `large`, `medium`, i `small`als nostres elements, i que seleccionem aquestes classes col·locant un punt abans del nom, com en`.centered`
    
-   Resulta que podem moure tot el nostre codi d'estil a un fitxer especial anomenat fitxer _CSS_ . Podem crear un fitxer anomenat `style.css`i enganxar-hi les nostres classes:
    
    ``` css
    .centered
    {
        text-align: center;
    }
    
    .large
    {
        font-size: large;
    }
    
    .medium
    {
        font-size: medium;
    }
    
    .small
    {
        font-size: small;
    }
    ```
    
    Tingueu en compte que això és textualment el que va aparèixer al nostre fitxer HTML.
    
-   Aleshores podem dir al navegador on ha de localitzar el CSS d'aquest fitxer HTML:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates external stylesheets -->
    
    <html lang="en">
        <head>
            <link href="style.css" rel="stylesheet">
            <title>css</title>
        </head>
        <body class="centered">
            <header class="large">
                John Harvard
            </header>
            <main class="medium">
                Welcome to my home page!
            </main>
            <footer class="small">
                Copyright &amp;#169; John Harvard
            </footer>
        </body>
    </html>
    ```
    
    Observeu que `style.css`està enllaçat a aquest fitxer HTML com a full d'estils, indicant al navegador on ha de localitzar els estils que hem creat.
    

## Frameworks

-   De manera similar a les biblioteques de tercers que podem aprofitar a Python, hi ha biblioteques de tercers anomenades _marcs_ que podem utilitzar amb els nostres fitxers HTML.
-   _Bootstrap_ és un d'aquests marcs que podem utilitzar per embellir el nostre HTML i perfeccionar fàcilment els elements de disseny de manera que les nostres pàgines siguin més llegibles.
-   Bootstrap es pot utilitzar afegint l' `link`etiqueta següent al `head`fitxer html:
    
    ``` html
    <head>
          <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
        <title>favorites</title>
    </head>
    ```
    
-   Considereu el següent HTML:
    
    ```html
    <!DOCTYPE html>
    
    <!-- Demonstrates table -->
    
    <html lang="en">
        <head>
            <title>phonebook</title>
        </head>
        <body>
            <table>
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Number</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Carter</td>
                        <td>+1-617-495-1000</td>
                    </tr>
                    <tr>
                        <td>David</td>
                        <td>+1-617-495-1000</td>
                    </tr>
                    <tr>
                        <td>John</td>
                        <td>+1-949-468-2750</td>
                    </tr>
                </tbody>
            </table>
        </body>
    </html>
    ```
    
    Observeu com quan mireu una versió publicada d'aquesta pàgina, és molt clar.
    
-   Ara considereu el següent HTML que implementa l'ús de Bootstrap:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates table with Bootstrap -->
    
    <html lang="en">
        <head>
            <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
            <title>phonebook</title>
        </head>
        <body>
            <table class="table">
                <thead>
                    <tr>
                        <th scope="col">Name</th>
                        <th scope="col">Number</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Carter</td>
                        <td>+1-617-495-1000</td>
                    </tr>
                    <tr>
                        <td>David</td>
                        <td>+1-949-468-2750</td>
                    </tr>
                </tbody>
            </table>
        </body>
    </html>
    ```
    
    Fixeu-vos que aquest lloc web és molt més bonic ara.
    
-   De la mateixa manera, tingueu en compte la següent expansió de la nostra pàgina de cerca creada anteriorment:
    
    ``` html
    <!DOCTYPE html>
    
    <!-- Demonstrates layout with Bootstrap -->
    
    <html lang="en">
        <head>
            <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
            <title>search</title>
        </head>
        <body>
    
            <div class="container-fluid">
    
                <ul class="m-3 nav">
                    <li class="nav-item">
                        <a class="nav-link text-dark" href="https://about.google/">About</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link text-dark" href="https://store.google.com/">Store</a>
                    </li>
                    <li class="nav-item ms-auto">
                        <a class="nav-link text-dark" href="https://www.google.com/gmail/">Gmail</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link text-dark" href="https://www.google.com/imghp">Images</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link text-dark" href="https://www.google.com/intl/en/about/products">
                            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-grid-3x3-gap-fill" viewBox="0 0 16 16">
                                <path d="M1 2a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1V2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1V2zM1 7a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V7zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1V7zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1V7zM1 12a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1v-2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1v-2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1v-2z"/>
                            </svg>
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="btn btn-primary" href="https://accounts.google.com/ServiceLogin" role="button">Sign in</a>
                    </li>
                </ul>
    
                <div class="text-center">
    
                    <!-- https://knowyourmeme.com/memes/happy-cat -->
                    <img alt="Happy Cat" class="img-fluid w-25" src="cat.gif">
    
                    <form action="https://www.google.com/search" class="mt-4" method="get">
                        <input autocomplete="off" autofocus class="form-control form-control-lg mb-4 mx-auto w-50" name="q" placeholder="Query" type="search">
                        <button class="btn btn-light">Google Search</button>
                        <button class="btn btn-light" name="btnI">I'm Feeling Lucky</button>
                    </form>
    
                </div>
    
            </div>
    
        </body>
    </html>
    ```
    
    Aquesta versió de la pàgina està molt estilitzada, gràcies a Bootstrap.
    
-   Podeu obtenir més informació sobre això a la [documentació de Bootstrap](https://getbootstrap.com/docs/) .

## JavaScript

-   JavaScript és un altre llenguatge de programació que permet la interactivitat dins de les pàgines web.
-   Considereu la següent implementació `hello.html`que inclou tant JavaScript com HTML:
    
    ```html
    <!DOCTYPE html> 
    
    <!-- Demonstrates onsubmit -->
    
    <html lang="en">
        <head>
            <script>
    
                function greet()
                {
                    alert('hello, ' + document.querySelector('#name').value);
                }
    
            </script>
            <title>hello</title>
        </head>
        <body>
            <form onsubmit="greet(); return false;">
                <input autocomplete="off" autofocus id="name" placeholder="Name" type="text">
                <input type="submit">
            </form>
        </body>
    </html>
    ```
    
    Observeu com aquest formulari utilitza una `onsubmit`propietat per activar un `script`trobat a la part superior del fitxer. L'script s'utilitza `alert`per crear una finestra emergent d'alerta. `#name.value`va al quadre de text de la pàgina i obté el valor escrit per l'usuari.
    
-   En general, es considera un mal disseny barrejar onsubmit i JavaScript. Podem avançar el nostre codi de la següent manera:
    
    ```html
    <!DOCTYPE html>
    
    <!-- Demonstrates DOMContentLoaded -->
    
    <html lang="en">
        <head>
            <script>
    
                document.addEventListener('DOMContentLoaded', function() {
                    document.querySelector('form').addEventListener('submit', function(e) {
                        alert('hello, ' + document.querySelector('#name').value);
                        e.preventDefault();
                    });
                });
    
            </script>
            <title>hello</title>
        </head>
        <body>
            <form>
                <input autocomplete="off" autofocus id="name" placeholder="Name" type="text">
                <input type="submit">
            </form>
        </body>
    </html>
    ```
    
    Tingueu en compte que aquesta versió del codi crea un `addEventListener`per escoltar el formulari `submit`que s'està activant. Observeu com `DOMContentLoaded`s'assegura que tota la pàgina es carregui abans d'executar el JavaScript.
    
-   JavaScript us permet llegir i modificar dinàmicament el document html carregat a la memòria de manera que l'usuari no necessita tornar a carregar per veure els canvis.
-   Considereu el següent HTML:
    
    ```html
    <!DOCTYPE html>
    
    <!-- Demonstrates programmatic changes to style -->
    
    <html lang="en">
        <head>
            <title>background</title>
        </head>
        <body>
            <button id="red">R</button>
            <button id="green">G</button>
            <button id="blue">B</button>
            <script>
    
                let body = document.querySelector('body');
                document.querySelector('#red').addEventListener('click', function() {
                    body.style.backgroundColor = 'red';
                });
                document.querySelector('#green').addEventListener('click', function() {
                    body.style.backgroundColor = 'green';
                });
                document.querySelector('#blue').addEventListener('click', function() {
                    body.style.backgroundColor = 'blue';
                });
    
            </script>
        </body>
    </html>
    ```
    
    Tingueu en compte que JavaScript escolta quan es fa clic en un botó específic. En fer clic, es canvien determinats atributs d'estil de la pàgina. `body`es defineix com el cos de la pàgina. Aleshores, un oient d'esdeveniments espera que faci clic a un dels botons. Aleshores, es `body.style.backgroundColor`canvia.
    
-   De la mateixa manera, tingueu en compte el següent:
    
    ``` html
    <!DOCTYPE html>
    
    <html lang="en">
        <head>
            <script>
    
                // Toggles visibility of greeting
                function blink()
                {
                    let body = document.querySelector('body');
                    if (body.style.visibility == 'hidden')
                    {
                        body.style.visibility = 'visible';
                    }
                    else
                    {
                        body.style.visibility = 'hidden';
                    }
                }
    
                // Blink every 500ms
                window.setInterval(blink, 500);
    
            </script>
            <title>blink</title>
        </head>
        <body>
            hello, world
        </body>
    </html>
    ```
    
    Aquest exemple parpelleja un text a un interval determinat. Observeu que `window.setInterval`admet dos arguments: una funció a cridar i un període d'espera (en mil·lisegons) entre les trucades de funció.
    
-   Tingueu en compte el següent:
    
    ``` html
    <!DOCTYPE html>
    
    <html lang="en">
    
        <head>
            <title>autocomplete</title>
        </head>
    
        <body>
    
            <input autocomplete="off" autofocus placeholder="Query" type="text">
    
            <ul></ul>
    
            <script src="large.js"></script>
            <script>
          
                let input = document.querySelector('input');
                input.addEventListener('keyup', function(event) {
                    let html = '';
                    if (input.value) {
                        for (word of WORDS) {
                            if (word.startsWith(input.value)) {
                                html += `<li>${word}</li>`;
                            }
                        }
                    }
                    document.querySelector('ul').innerHTML = html;
                });
    
            </script>
    
        </body>
    </html>
    ```
    
    Aquesta és una implementació de JavaScript d'autocompletar. Això s'extreu d'un fitxer (no representat aquí) anomenat `large.js`que és una llista de paraules.
    
-   Curiosament, també podem geolocalitzar mitjançant JavaScript:

    ``` html
    <!DOCTYPE html>
    
    <html lang="en">
        <head>
            <title>geolocation</title>
        </head>
        <body>
            <script>
              
                navigator.geolocation.getCurrentPosition(function(position) {
                    document.write(position.coords.latitude + ", " + position.coords.longitude);
                });
    
            </script>
        </body>
    </html>
    ```
    
    Fixeu-vos que `navigator.geolocation`s'acostuma a `getCurrentPosition`. Això no funcionarà si el vostre ordinador o navegador no permet el seguiment de la ubicació.
    
-   Les capacitats de JavaScript són moltes i es poden trobar a la [documentació de JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) .

## Resumint
En aquesta lliçó, heu après a crear els vostres propis fitxers HTML, estilitzar-los, aprofitar marcs de tercers i utilitzar JavaScript. En concret, hem parlat...

-   TCP/IP
-   DNS
-   HTML
-   Expressions regulars.
-   CSS
-   Marcs
-   JavaScript

Ens veiem a la propera!
