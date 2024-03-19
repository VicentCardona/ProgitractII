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

## [HTML](https://cs50.harvard.edu/x/2024/notes/8/#html)

-   _El llenguatge de marques_ _HTML_ o d'hipertext està format per _etiquetes_ , cadascuna de les quals pot tenir alguns _atributs_ que el descriuen.
-   Al terminal, escriviu `code hello.html`i escriviu el codi de la següent manera:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates HTML --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;hello, title&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            hello, body
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu que l' `html`etiqueta obre i tanca aquest fitxer. A més, observeu l' `lang`atribut, que modifica el comportament de l' `html`etiqueta. A més, tingueu en compte que hi ha `head`etiquetes i `body`etiquetes. El sagnat no és necessari, però suggereix una jerarquia.
    
-   Podeu enviar el vostre codi escrivint `http-server`. Aquest servei ara està disponible en un URL molt llarg. Si hi feu clic, podeu visitar el lloc web amb el vostre propi codi.
-   Quan visiteu aquest URL, observeu que el nom del fitxer `hello.html`apareix al final d'aquest URL. A més, tingueu en compte, segons l'URL, que el servidor serveix a través del port 8080.
-   La jerarquia d'etiquetes es pot representar de la següent manera:
    
    ![codi html al costat d'una jerarquia que mostra els nodes pare i fill](https://cs50.harvard.edu/x/2024/notes/8/cs50Week8Slide065.png "DOM")
    
-   El coneixement d'aquesta jerarquia serà útil més endavant a mesura que aprenem JavaScript.
-   El navegador llegirà el vostre fitxer HTML de dalt a baix i d'esquerra a dreta.
-   Com que els espais en blanc i el sagnat s'ignoren de manera efectiva en HTML, haureu d'utilitzar `<p>`etiquetes de paràgraf per obrir i tancar un paràgraf. Tingueu en compte el següent:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates paragraphs --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;paragraphs&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;p&gt;
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus convallis scelerisque quam, vel hendrerit lectus viverra eu. Praesent posuere eget lectus ut faucibus. Etiam eu velit laoreet, gravida lorem in, viverra est. Cras ut purus neque. In porttitor non lorem id lobortis. Mauris gravida metus libero, quis maximus dui porta at. Donec lacinia felis consectetur venenatis scelerisque. Nulla eu nisl sollicitudin, varius velit sit amet, vehicula erat. Curabitur sollicitudin felis sit amet orci mattis, a tempus nulla pulvinar. Aliquam erat volutpat.
            &lt;/p&gt;
            &lt;p&gt;
                Mauris ut dui in eros semper hendrerit. Morbi vel elit mi. Sed sit amet ex non quam dignissim dignissim et vel arcu. Pellentesque eget elementum orci. Morbi ac cursus ex. Pellentesque quis turpis blandit orci dapibus semper sed non nunc. Nulla et dolor nec lacus finibus volutpat. Sed non lorem diam. Donec feugiat interdum interdum. Vivamus et justo in enim blandit fermentum vel at elit. Phasellus eu ante vitae ligula varius aliquet. Etiam id posuere nibh.
            &lt;/p&gt;
            &lt;p&gt;
                Aenean venenatis convallis ante a rhoncus. Nullam in metus vel diam vehicula tincidunt. Donec lacinia metus sem, sit amet egestas elit blandit sit amet. Nunc egestas sem quis nisl mattis semper. Pellentesque ut magna congue lorem eleifend sodales. Donec tortor tortor, aliquam vitae mollis sed, interdum ut lectus. Mauris non purus quis ipsum lacinia tincidunt.
            &lt;/p&gt;
            &lt;p&gt;
                Integer at justo lacinia libero blandit aliquam ut ut dui. Quisque tincidunt facilisis venenatis. Nullam dictum odio quis lorem luctus, vel malesuada dolor luctus. Aenean placerat faucibus enim a facilisis. Maecenas eleifend quis massa sed eleifend. Ut ultricies, dui ac vulputate hendrerit, ex metus iaculis diam, vitae fermentum libero dui et ante. Phasellus suscipit, arcu ut consequat sagittis, massa urna accumsan massa, eu aliquet nulla lorem vitae arcu. Pellentesque rutrum felis et metus porta semper. Nam ac consectetur mauris.
            &lt;/p&gt;
            &lt;p&gt;
                Suspendisse rutrum vestibulum odio, sed venenatis purus condimentum sed. Morbi ornare tincidunt augue eu auctor. Vivamus sagittis ac lectus at aliquet. Nulla urna mauris, interdum non nibh in, vehicula porta enim. Donec et posuere sapien. Pellentesque ultrices scelerisque ipsum, vel fermentum nibh tincidunt et. Proin gravida porta ipsum nec scelerisque. Vestibulum fringilla erat at turpis laoreet, nec hendrerit nisi scelerisque.
            &lt;/p&gt;
            &lt;p&gt;
                Sed quis malesuada mi. Nam id purus quis augue sagittis pharetra. Nulla facilisi. Maecenas vel fringilla ante. Cras tristique, arcu sit amet blandit auctor, urna elit ultricies lacus, a malesuada eros dui id massa. Aliquam sem odio, pretium vel cursus eget, scelerisque at urna. Vestibulum posuere a turpis consectetur consectetur. Cras consequat, risus quis tempor egestas, nulla ipsum ornare erat, nec accumsan nibh lorem nec risus. Integer at iaculis lacus. Integer congue nunc massa, quis molestie felis pellentesque vestibulum. Nulla odio tortor, aliquam nec quam in, ornare aliquet sapien.
            &lt;/p&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Tingueu en compte que els paràgrafs comencen amb una `<p>`etiqueta i acaben amb una `</p>`etiqueta.
    
-   HTML permet la representació d'encapçalaments:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates headings (for chapters, sections, subsections, etc.) --&gt;
    
    &lt;html lang="en"&gt;
    
        &lt;head&gt;
            &lt;title&gt;headings&lt;/title&gt;
        &lt;/head&gt;
    
        &lt;body&gt;
    
            &lt;h1&gt;One&lt;/h1&gt;
            &lt;p&gt;
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus convallis scelerisque quam, vel hendrerit lectus viverra eu. Praesent posuere eget lectus ut faucibus. Etiam eu velit laoreet, gravida lorem in, viverra est. Cras ut purus neque. In porttitor non lorem id lobortis. Mauris gravida metus libero, quis maximus dui porta at. Donec lacinia felis consectetur venenatis scelerisque. Nulla eu nisl sollicitudin, varius velit sit amet, vehicula erat. Curabitur sollicitudin felis sit amet orci mattis, a tempus nulla pulvinar. Aliquam erat volutpat.
            &lt;/p&gt;
    
            &lt;h2&gt;Two&lt;/h2&gt;
            &lt;p&gt;
                Mauris ut dui in eros semper hendrerit. Morbi vel elit mi. Sed sit amet ex non quam dignissim dignissim et vel arcu. Pellentesque eget elementum orci. Morbi ac cursus ex. Pellentesque quis turpis blandit orci dapibus semper sed non nunc. Nulla et dolor nec lacus finibus volutpat. Sed non lorem diam. Donec feugiat interdum interdum. Vivamus et justo in enim blandit fermentum vel at elit. Phasellus eu ante vitae ligula varius aliquet. Etiam id posuere nibh.
            &lt;/p&gt;
    
            &lt;h3&gt;Three&lt;/h3&gt;
            &lt;p&gt;
                Aenean venenatis convallis ante a rhoncus. Nullam in metus vel diam vehicula tincidunt. Donec lacinia metus sem, sit amet egestas elit blandit sit amet. Nunc egestas sem quis nisl mattis semper. Pellentesque ut magna congue lorem eleifend sodales. Donec tortor tortor, aliquam vitae mollis sed, interdum ut lectus. Mauris non purus quis ipsum lacinia tincidunt.
            &lt;/p&gt;
    
            &lt;h4&gt;Four&lt;/h4&gt;
            &lt;p&gt;
                Integer at justo lacinia libero blandit aliquam ut ut dui. Quisque tincidunt facilisis venenatis. Nullam dictum odio quis lorem luctus, vel malesuada dolor luctus. Aenean placerat faucibus enim a facilisis. Maecenas eleifend quis massa sed eleifend. Ut ultricies, dui ac vulputate hendrerit, ex metus iaculis diam, vitae fermentum libero dui et ante. Phasellus suscipit, arcu ut consequat sagittis, massa urna accumsan massa, eu aliquet nulla lorem vitae arcu. Pellentesque rutrum felis et metus porta semper. Nam ac consectetur mauris.
            &lt;/p&gt;
    
            &lt;h5&gt;Five&lt;/h5&gt;
            &lt;p&gt;
                Suspendisse rutrum vestibulum odio, sed venenatis purus condimentum sed. Morbi ornare tincidunt augue eu auctor. Vivamus sagittis ac lectus at aliquet. Nulla urna mauris, interdum non nibh in, vehicula porta enim. Donec et posuere sapien. Pellentesque ultrices scelerisque ipsum, vel fermentum nibh tincidunt et. Proin gravida porta ipsum nec scelerisque. Vestibulum fringilla erat at turpis laoreet, nec hendrerit nisi scelerisque.
            &lt;/p&gt;
    
            &lt;h6&gt;Six&lt;/h6&gt;
            &lt;p&gt;
                Sed quis malesuada mi. Nam id purus quis augue sagittis pharetra. Nulla facilisi. Maecenas vel fringilla ante. Cras tristique, arcu sit amet blandit auctor, urna elit ultricies lacus, a malesuada eros dui id massa. Aliquam sem odio, pretium vel cursus eget, scelerisque at urna. Vestibulum posuere a turpis consectetur consectetur. Cras consequat, risus quis tempor egestas, nulla ipsum ornare erat, nec accumsan nibh lorem nec risus. Integer at iaculis lacus. Integer congue nunc massa, quis molestie felis pellentesque vestibulum. Nulla odio tortor, aliquam nec quam in, ornare aliquet sapien.
            &lt;/p&gt;
    
        &lt;/body&gt;
    
    &lt;/html&gt;
    ```
    
    Observeu que `<h1>`, `<h2>`, i `<h3>`denoten diferents nivells d'encapçalaments.
    
-   També podem crear llistes no ordenades dins d'HTML:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates (ordered) lists --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;list&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;ul&gt;
                &lt;li&gt;foo&lt;/li&gt;
                &lt;li&gt;bar&lt;/li&gt;
                &lt;li&gt;baz&lt;/li&gt;
            &lt;/ul&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu que l' `<ul>`etiqueta crea una llista no ordenada que conté tres elements.
    
-   També podem crear llistes ordenades dins d'HTML:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates (ordered) lists --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;list&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;ol&gt;
                &lt;li&gt;foo&lt;/li&gt;
                &lt;li&gt;bar&lt;/li&gt;
                &lt;li&gt;baz&lt;/li&gt;
            &lt;/ol&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu que l' `<ol>`etiqueta crea una llista ordenada que conté tres elements.
    
-   També podem crear una taula en HTML:
    
    ``` html
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates table --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;table&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;table&gt;
                &lt;tr&gt;
                    &lt;td&gt;1&lt;/td&gt;
                    &lt;td&gt;2&lt;/td&gt;
                    &lt;td&gt;3&lt;/td&gt;
                &lt;/tr&gt;
                &lt;tr&gt;
                    &lt;td&gt;4&lt;/td&gt;
                    &lt;td&gt;5&lt;/td&gt;
                    &lt;td&gt;6&lt;/td&gt;
                &lt;/tr&gt;
                &lt;tr&gt;
                    &lt;td&gt;7&lt;/td&gt;
                    &lt;td&gt;8&lt;/td&gt;
                    &lt;td&gt;9&lt;/td&gt;
                &lt;/tr&gt;
                &lt;tr&gt;
                    &lt;td&gt;*&lt;/td&gt;
                    &lt;td&gt;0&lt;/td&gt;
                    &lt;td&gt;#&lt;/td&gt;
                &lt;/tr&gt;
            &lt;/table&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Les taules també tenen etiquetes que obren i tanquen cada element. A més, tingueu en compte la sintaxi dels comentaris en HTML.
    
-   Les imatges també es poden utilitzar dins d'HTML:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates image --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;image&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;img alt="photo of bridge" src="bridge.png"&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu que `src="bridge.png"`indica el camí on es pot localitzar el fitxer d'imatge.
    
-   Els vídeos també es poden incloure en HTML:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates video --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;video&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;video controls muted&gt;
                &lt;source src="video.mp4" type="video/mp4"&gt;
            &lt;/video&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Tingueu en compte que l' `type`atribut indica que es tracta d'un vídeo del tipus `mp4`. A més, observeu com `controls`i `muted`es passen a `video`.
    
-   També podeu enllaçar entre diverses pàgines web:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates link --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;link&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
           Visit &lt;a href="https://www.harvard.edu"&gt;Harvard&lt;/a&gt;.
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Tingueu en compte que l' etiqueta _d'ancoratge_`<a>` o s'utilitza per fer un text enllaçable.`Harvard`
    
-   Les metaetiquetes s'utilitzen per contenir informació sobre les dades dins del fitxer HTML. Tingueu en compte el següent:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates responsive design --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;meta name="viewport" content="initial-scale=1, width=device-width"&gt;
            &lt;title&gt;meta&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus convallis scelerisque quam, vel hendrerit lectus viverra eu. Praesent posuere eget lectus ut faucibus. Etiam eu velit laoreet, gravida lorem in, viverra est. Cras ut purus neque. In porttitor non lorem id lobortis. Mauris gravida metus libero, quis maximus dui porta at. Donec lacinia felis consectetur venenatis scelerisque. Nulla eu nisl sollicitudin, varius velit sit amet, vehicula erat. Curabitur sollicitudin felis sit amet orci mattis, a tempus nulla pulvinar. Aliquam erat volutpat.
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Tingueu en compte que aquest conjunt d' `meta`atributs fa que aquesta pàgina sigui adaptada per a mòbils.
    
-   Hi ha nombrosos `meta`parells clau-valor que podeu utilitzar:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates Open Graph tags --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;meta property="og:title" content="CS50"&gt;
            &lt;meta property="og:description" content="Introduction to the intellectual enterprises of computer science and the art of programming."&gt;
            &lt;meta property="og:image" content="cat.jpg"&gt;
            &lt;title&gt;meta&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            ...
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Tingueu en compte que aquests parells de valors clau es relacionen amb `title`i `description`de la pàgina web.
    
-   També podeu crear formularis que recordin la cerca de Google:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates form --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;search&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;form action="https://www.google.com/search" method="get"&gt;
                &lt;input name="q" type="search"&gt;
                &lt;input type="submit" value="Google Search"&gt;
            &lt;/form&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu que `form`s'obre una etiqueta i proporciona l'atribut del que `action`necessitarà. `input`S'inclou el camp, passant el nom `q`i el tipus com a `search`.
    
-   Podem millorar aquesta cerca de la següent manera:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates additional form attributes --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;search&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;form action="https://www.google.com/search" method="get"&gt;
                &lt;input autocomplete="off" autofocus name="q" placeholder="Query" type="search"&gt;
                &lt;button&gt;Google Search&lt;/button&gt;
            &lt;/form&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu que `autocomplete`està girat `off`. `autofocus`està habilitat.
    
-   Hem vist només alguns dels molts elements HTML que podeu afegir al vostre lloc. Si teniu alguna idea per afegir al vostre lloc que encara no hem vist (un botó, un fitxer d'àudio, etc.), proveu a Google "X en HTML" per trobar la sintaxi correcta! De la mateixa manera, podeu utilitzar [cs50.ai](https://cs50.ai/) per ajudar-vos a descobrir més funcions HTML!

## [Expressions regulars](https://cs50.harvard.edu/x/2024/notes/8/#regular-expressions)

-   _Les expressions regulars_ o _expressions regulars_ són un mitjà per garantir que les dades proporcionades per l'usuari s'ajustin a un format específic.
-   Podem implementar la nostra pròpia pàgina de registre que utilitza execucions regulars de la següent manera:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates type="email" --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;register&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;form&gt;
                &lt;input autocomplete="off" autofocus name="email" placeholder="Email" type="email"&gt;
                &lt;button&gt;Register&lt;/button&gt;
            &lt;/form&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu que l' `input`etiqueta inclou atributs que indiquen que és del tipus `email`. El navegador sap que ha de comprovar que l'entrada és una adreça de correu electrònic.
    
-   Tot i que el navegador utilitza aquests atributs integrats per comprovar si hi ha una adreça de correu electrònic, podem afegir un `pattern`atribut per assegurar-nos que només les dades específiques acabin a l'adreça de correu electrònic:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates pattern attribute --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;register&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;form&gt;
                &lt;input autocomplete="off" autofocus name="email" pattern=".+@.+\.edu" placeholder="Email" type="email"&gt;
                &lt;button&gt;Register&lt;/button&gt;
            &lt;/form&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Tingueu en compte que l' `pattern`atribut rep una expressió regular per indicar que l'adreça de correu electrònic ha d'incloure un `@`símbol i un `.edu`.
    
-   Podeu obtenir més informació sobre les expressions regulars a [la documentació de Mozilla](https://cs50.harvard.edu/x/2024/notes/8/developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions) . A més, podeu fer consultes a [cs50.ai](https://cs50.ai/) per obtenir suggeriments.

## [CSS](https://cs50.harvard.edu/x/2024/notes/8/#css)

-   `CSS`, o _full d'estil en cascada_ , és un llenguatge de marques que us permet afinar l'estètica dels vostres fitxers HTML.
-   CSS està ple de _propietats_ , que inclouen parells clau-valor.
-   Al terminal, escriviu `code home.html`i escriviu el codi de la següent manera:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates inline CSS with P tags --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;css&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;p style="font-size: large; text-align: center;"&gt;
                John Harvard
            &lt;/p&gt;
            &lt;p style="font-size: medium; text-align: center;"&gt;
                Welcome to my home page!
            &lt;/p&gt;
            &lt;p style="font-size: small; text-align: center;"&gt;
                Copyright &amp;#169; John Harvard
            &lt;/p&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Tingueu en compte que alguns `style`atributs es proporcionen a les `<p>`etiquetes. S'estableix `font-size`en `large`, `medium`, o `small`. Després `text-align`es posa al centre.
    
-   Tot i que és correcte, l'anterior no està ben dissenyat. Podem eliminar la redundància modificant el nostre codi de la següent manera:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Removes outer DIV --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;css&lt;/title&gt;
        &lt;/head&gt;
        &lt;body style="text-align: center"&gt;
            &lt;div style="font-size: large"&gt;
                John Harvard
            &lt;/div&gt;
            &lt;div style="font-size: medium"&gt;
                Welcome to my home page!
            &lt;/div&gt;
            &lt;div style="font-size: small"&gt;
                Copyright &amp;#169; John Harvard
            &lt;/div&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Tingueu en compte que `<div>`les etiquetes s'utilitzen per dividir aquest fitxer HTML en regions específiques. `text-align: center`s'invoca a tot el cos de l'HTML. Com que tot el que hi ha a dins `body`és fill de `body`, l' `center`atribut cau en cascada a aquests nens.
    
-   Resulta que hi ha etiquetes semàntiques més noves que s'inclouen a HTML. Podem modificar el nostre codi de la següent manera:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Uses semantic tags instead of DIVs --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;css&lt;/title&gt;
        &lt;/head&gt;
        &lt;body style="text-align: center"&gt;
            &lt;header style="font-size: large"&gt;
                John Harvard
            &lt;/header&gt;
            &lt;main style="font-size: medium"&gt;
                Welcome to my home page!
            &lt;/main&gt;
            &lt;footer style="font-size: small"&gt;
                Copyright &amp;#169; John Harvard
            &lt;/footer&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu que els `header`i `footer`tots dos tenen diferents estils assignats.
    
-   Aquesta pràctica de col·locar l'estil i la informació al mateix lloc no és una bona pràctica. Podríem moure els elements d'estil a la part superior del fitxer de la següent manera:
    
    ```
    &lt;!-- Demonstrates class selectors --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;style&gt;
    
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
    
            &lt;/style&gt;
            &lt;title&gt;css&lt;/title&gt;
        &lt;/head&gt;
        &lt;body class="centered"&gt;
            &lt;header class="large"&gt;
                John Harvard
            &lt;/header&gt;
            &lt;main class="medium"&gt;
                Welcome to my home page!
            &lt;/main&gt;
            &lt;footer class="small"&gt;
                Copyright &amp;#169; John Harvard
            &lt;/footer&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu que totes les etiquetes d'estil es col·loquen a `head`l'embolcall de l' `style`etiqueta. Observeu també que hem assignat _classes_ , anomenades `centered`, `large`, `medium`, i `small`als nostres elements, i que seleccionem aquestes classes col·locant un punt abans del nom, com en`.centered`
    
-   Resulta que podem moure tot el nostre codi d'estil a un fitxer especial anomenat fitxer _CSS_ . Podem crear un fitxer anomenat `style.css`i enganxar-hi les nostres classes:
    
    ```
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
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates external stylesheets --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;link href="style.css" rel="stylesheet"&gt;
            &lt;title&gt;css&lt;/title&gt;
        &lt;/head&gt;
        &lt;body class="centered"&gt;
            &lt;header class="large"&gt;
                John Harvard
            &lt;/header&gt;
            &lt;main class="medium"&gt;
                Welcome to my home page!
            &lt;/main&gt;
            &lt;footer class="small"&gt;
                Copyright &amp;#169; John Harvard
            &lt;/footer&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu que `style.css`està enllaçat a aquest fitxer HTML com a full d'estils, indicant al navegador on ha de localitzar els estils que hem creat.
    

## [Marcs](https://cs50.harvard.edu/x/2024/notes/8/#frameworks)

-   De manera similar a les biblioteques de tercers que podem aprofitar a Python, hi ha biblioteques de tercers anomenades _marcs_ que podem utilitzar amb els nostres fitxers HTML.
-   _Bootstrap_ és un d'aquests marcs que podem utilitzar per embellir el nostre HTML i perfeccionar fàcilment els elements de disseny de manera que les nostres pàgines siguin més llegibles.
-   Bootstrap es pot utilitzar afegint l' `link`etiqueta següent al `head`fitxer html:
    
    ```
    &lt;head&gt;
          &lt;link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous"&gt;
        &lt;title&gt;favorites&lt;/title&gt;
    &lt;/head&gt;
    ```
    
-   Considereu el següent HTML:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates table --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;phonebook&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;table&gt;
                &lt;thead&gt;
                    &lt;tr&gt;
                        &lt;th&gt;Name&lt;/th&gt;
                        &lt;th&gt;Number&lt;/th&gt;
                    &lt;/tr&gt;
                &lt;/thead&gt;
                &lt;tbody&gt;
                    &lt;tr&gt;
                        &lt;td&gt;Carter&lt;/td&gt;
                        &lt;td&gt;+1-617-495-1000&lt;/td&gt;
                    &lt;/tr&gt;
                    &lt;tr&gt;
                        &lt;td&gt;David&lt;/td&gt;
                        &lt;td&gt;+1-617-495-1000&lt;/td&gt;
                    &lt;/tr&gt;
                    &lt;tr&gt;
                        &lt;td&gt;John&lt;/td&gt;
                        &lt;td&gt;+1-949-468-2750&lt;/td&gt;
                    &lt;/tr&gt;
                &lt;/tbody&gt;
            &lt;/table&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu com quan mireu una versió publicada d'aquesta pàgina, és molt clar.
    
-   Ara considereu el següent HTML que implementa l'ús de Bootstrap:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates table with Bootstrap --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous"&gt;
            &lt;title&gt;phonebook&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;table class="table"&gt;
                &lt;thead&gt;
                    &lt;tr&gt;
                        &lt;th scope="col"&gt;Name&lt;/th&gt;
                        &lt;th scope="col"&gt;Number&lt;/th&gt;
                    &lt;/tr&gt;
                &lt;/thead&gt;
                &lt;tbody&gt;
                    &lt;tr&gt;
                        &lt;td&gt;Carter&lt;/td&gt;
                        &lt;td&gt;+1-617-495-1000&lt;/td&gt;
                    &lt;/tr&gt;
                    &lt;tr&gt;
                        &lt;td&gt;David&lt;/td&gt;
                        &lt;td&gt;+1-949-468-2750&lt;/td&gt;
                    &lt;/tr&gt;
                &lt;/tbody&gt;
            &lt;/table&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Fixeu-vos que aquest lloc web és molt més bonic ara.
    
-   De la mateixa manera, tingueu en compte la següent expansió de la nostra pàgina de cerca creada anteriorment:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates layout with Bootstrap --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous"&gt;
            &lt;title&gt;search&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
    
            &lt;div class="container-fluid"&gt;
    
                &lt;ul class="m-3 nav"&gt;
                    &lt;li class="nav-item"&gt;
                        &lt;a class="nav-link text-dark" href="https://about.google/"&gt;About&lt;/a&gt;
                    &lt;/li&gt;
                    &lt;li class="nav-item"&gt;
                        &lt;a class="nav-link text-dark" href="https://store.google.com/"&gt;Store&lt;/a&gt;
                    &lt;/li&gt;
                    &lt;li class="nav-item ms-auto"&gt;
                        &lt;a class="nav-link text-dark" href="https://www.google.com/gmail/"&gt;Gmail&lt;/a&gt;
                    &lt;/li&gt;
                    &lt;li class="nav-item"&gt;
                        &lt;a class="nav-link text-dark" href="https://www.google.com/imghp"&gt;Images&lt;/a&gt;
                    &lt;/li&gt;
                    &lt;li class="nav-item"&gt;
                        &lt;a class="nav-link text-dark" href="https://www.google.com/intl/en/about/products"&gt;
                            &lt;svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-grid-3x3-gap-fill" viewBox="0 0 16 16"&gt;
                                &lt;path d="M1 2a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1V2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1V2zM1 7a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V7zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1V7zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1V7zM1 12a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1v-2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1v-2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1v-2z"/&gt;
                            &lt;/svg&gt;
                        &lt;/a&gt;
                    &lt;/li&gt;
                    &lt;li class="nav-item"&gt;
                        &lt;a class="btn btn-primary" href="https://accounts.google.com/ServiceLogin" role="button"&gt;Sign in&lt;/a&gt;
                    &lt;/li&gt;
                &lt;/ul&gt;
    
                &lt;div class="text-center"&gt;
    
                    &lt;!-- https://knowyourmeme.com/memes/happy-cat --&gt;
                    &lt;img alt="Happy Cat" class="img-fluid w-25" src="cat.gif"&gt;
    
                    &lt;form action="https://www.google.com/search" class="mt-4" method="get"&gt;
                        &lt;input autocomplete="off" autofocus class="form-control form-control-lg mb-4 mx-auto w-50" name="q" placeholder="Query" type="search"&gt;
                        &lt;button class="btn btn-light"&gt;Google Search&lt;/button&gt;
                        &lt;button class="btn btn-light" name="btnI"&gt;I'm Feeling Lucky&lt;/button&gt;
                    &lt;/form&gt;
    
                &lt;/div&gt;
    
            &lt;/div&gt;
    
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Aquesta versió de la pàgina està molt estilitzada, gràcies a Bootstrap.
    
-   Podeu obtenir més informació sobre això a la [documentació de Bootstrap](https://getbootstrap.com/docs/) .

## [JavaScript](https://cs50.harvard.edu/x/2024/notes/8/#javascript)

-   JavaScript és un altre llenguatge de programació que permet la interactivitat dins de les pàgines web.
-   Considereu la següent implementació `hello.html`que inclou tant JavaScript com HTML:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates onsubmit --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;script&gt;
    
                function greet()
                {
                    alert('hello, ' + document.querySelector('#name').value);
                }
    
            &lt;/script&gt;
            &lt;title&gt;hello&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;form onsubmit="greet(); return false;"&gt;
                &lt;input autocomplete="off" autofocus id="name" placeholder="Name" type="text"&gt;
                &lt;input type="submit"&gt;
            &lt;/form&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Observeu com aquest formulari utilitza una `onsubmit`propietat per activar un `script`trobat a la part superior del fitxer. L'script s'utilitza `alert`per crear una finestra emergent d'alerta. `#name.value`va al quadre de text de la pàgina i obté el valor escrit per l'usuari.
    
-   En general, es considera un mal disseny barrejar onsubmit i JavaScript. Podem avançar el nostre codi de la següent manera:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates DOMContentLoaded --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;script&gt;
    
                document.addEventListener('DOMContentLoaded', function() {
                    document.querySelector('form').addEventListener('submit', function(e) {
                        alert('hello, ' + document.querySelector('#name').value);
                        e.preventDefault();
                    });
                });
    
            &lt;/script&gt;
            &lt;title&gt;hello&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;form&gt;
                &lt;input autocomplete="off" autofocus id="name" placeholder="Name" type="text"&gt;
                &lt;input type="submit"&gt;
            &lt;/form&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Tingueu en compte que aquesta versió del codi crea un `addEventListener`per escoltar el formulari `submit`que s'està activant. Observeu com `DOMContentLoaded`s'assegura que tota la pàgina es carregui abans d'executar el JavaScript.
    
-   JavaScript us permet llegir i modificar dinàmicament el document html carregat a la memòria de manera que l'usuari no necessita tornar a carregar per veure els canvis.
-   Considereu el següent HTML:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;!-- Demonstrates programmatic changes to style --&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;background&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;button id="red"&gt;R&lt;/button&gt;
            &lt;button id="green"&gt;G&lt;/button&gt;
            &lt;button id="blue"&gt;B&lt;/button&gt;
            &lt;script&gt;
    
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
    
            &lt;/script&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Tingueu en compte que JavaScript escolta quan es fa clic en un botó específic. En fer clic, es canvien determinats atributs d'estil de la pàgina. `body`es defineix com el cos de la pàgina. Aleshores, un oient d'esdeveniments espera que faci clic a un dels botons. Aleshores, es `body.style.backgroundColor`canvia.
    
-   De la mateixa manera, tingueu en compte el següent:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;script&gt;
    
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
    
            &lt;/script&gt;
            &lt;title&gt;blink&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            hello, world
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Aquest exemple parpelleja un text a un interval determinat. Observeu que `window.setInterval`admet dos arguments: una funció a cridar i un període d'espera (en mil·lisegons) entre les trucades de funció.
    
-   Tingueu en compte el següent:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;html lang="en"&gt;
    
        &lt;head&gt;
            &lt;title&gt;autocomplete&lt;/title&gt;
        &lt;/head&gt;
    
        &lt;body&gt;
    
            &lt;input autocomplete="off" autofocus placeholder="Query" type="text"&gt;
    
            &lt;ul&gt;&lt;/ul&gt;
    
            &lt;script src="large.js"&gt;&lt;/script&gt;
            &lt;script&gt;
          
                let input = document.querySelector('input');
                input.addEventListener('keyup', function(event) {
                    let html = '';
                    if (input.value) {
                        for (word of WORDS) {
                            if (word.startsWith(input.value)) {
                                html += `&lt;li&gt;${word}&lt;/li&gt;`;
                            }
                        }
                    }
                    document.querySelector('ul').innerHTML = html;
                });
    
            &lt;/script&gt;
    
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Aquesta és una implementació de JavaScript d'autocompletar. Això s'extreu d'un fitxer (no representat aquí) anomenat `large.js`que és una llista de paraules.
    
-   Curiosament, també podem geolocalitzar mitjançant JavaScript:
    
    ```
    &lt;!DOCTYPE html&gt;
    
    &lt;html lang="en"&gt;
        &lt;head&gt;
            &lt;title&gt;geolocation&lt;/title&gt;
        &lt;/head&gt;
        &lt;body&gt;
            &lt;script&gt;
              
                navigator.geolocation.getCurrentPosition(function(position) {
                    document.write(position.coords.latitude + ", " + position.coords.longitude);
                });
    
            &lt;/script&gt;
        &lt;/body&gt;
    &lt;/html&gt;
    ```
    
    Fixeu-vos que `navigator.geolocation`s'acostuma a `getCurrentPosition`. Això no funcionarà si el vostre ordinador o navegador no permet el seguiment de la ubicació.
    
-   Les capacitats de JavaScript són moltes i es poden trobar a la [documentació de JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) .

## [Resumint](https://cs50.harvard.edu/x/2024/notes/8/#summing-up)

En aquesta lliçó, heu après a crear els vostres propis fitxers HTML, estilitzar-los, aprofitar marcs de tercers i utilitzar JavaScript. En concret, hem parlat...

-   TCP/IP
-   DNS
-   HTML
-   Expressions regulars.
-   CSS
-   Marcs
-   JavaScript

Ens veiem a la propera!
