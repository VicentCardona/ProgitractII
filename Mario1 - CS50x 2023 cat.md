## [Començant](https://cs50.harvard.edu/x/2023/psets/1/mario/less/#getting-started)

Obriu el [codi VS.](https://cs50.dev/)

Comenceu fent clic dins de la finestra de la vostra terminal i, a continuació, executeu `cd`\-lo sol. Hauríeu de trobar que la seva "indicació" s'assembla a la següent.

Feu clic dins d'aquesta finestra de terminal i, a continuació, executeu

```
wget https://cdn.cs50.net/2022/fall/psets/1/mario-less.zip
```

seguit d'Enter per baixar un ZIP anomenat `mario-less.zip`al vostre espai de codi. Aneu amb compte de no passar per alt l'espai entre `wget`i l'URL següent, o qualsevol altre caràcter!

Ara executa

per crear una carpeta anomenada `mario-less`. Ja no necessiteu el fitxer ZIP, així que podeu executar-lo

i responeu amb "y" seguit d'Enter a la sol·licitud per eliminar el fitxer ZIP que heu baixat.

Ara escriviu

seguit d'Enter per moure't a (és a dir, obrir) aquest directori. La vostra sol·licitud ara hauria de semblar-se a la següent.

Si tot ha tingut èxit, hauríeu d'executar

i vegeu un fitxer anomenat `mario.c`. L'execució `code mario.c`hauria d'obrir el fitxer on escriureu el codi per a aquest conjunt de problemes. Si no, torna sobre els teus passos i mira si pots determinar on t'has equivocat!

## [Món 1-1](https://cs50.harvard.edu/x/2023/psets/1/mario/less/#world-1-1)

Cap al final del món 1-1 als Super Mario Brothers de Nintendo, Mario ha d'ascendir a la piràmide de blocs alineada a la dreta, igual que a sota.

![captura de pantalla de Mario saltant per una piràmide alineada a la dreta](https://cs50.harvard.edu/x/2023/psets/1/mario/less/pyramid.png)

Let’s recreate that pyramid in C, albeit in text, using hashes (`#`) for bricks, a la the below. Each hash is a bit taller than it is wide, so the pyramid itself will also be taller than it is wide.

```
       #
      ##
     ###
    ####
   #####
  ######
 #######
########
```

The program we’ll write will be called `mario`. And let’s allow the user to decide just how tall the pyramid should be by first prompting them for a positive integer between, say, 1 and 8, inclusive.

Here’s how the program might work if the user inputs `8` when prompted:

```
$ ./mario
Height: 8
       #
      ##
     ###
    ####
   #####
  ######
 #######
########
```

Here’s how the program might work if the user inputs `4` when prompted:

```
$ ./mario
Height: 4
   #
  ##
 ###
####
```

Here’s how the program might work if the user inputs `2` when prompted:

And here’s how the program might work if the user inputs `1` when prompted:

If the user doesn’t, in fact, input a positive integer between 1 and 8, inclusive, when prompted, the program should re-prompt the user until they cooperate:

```
$ ./mario
Height: -1
Height: 0
Height: 42
Height: 50
Height: 4
   #
  ##
 ###
####
```

How to begin? Let’s approach this problem one step at a time.

## [Walkthrough](https://cs50.harvard.edu/x/2023/psets/1/mario/less/#walkthrough)

<iframe allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" data-video="" src="https://www.youtube.com/embed/NAs4FIWkJ4s?modestbranding=0&amp;rel=0&amp;showinfo=0" data-ruffle-polyfilled="" scrolling="no" id="iFrameResizer0"></iframe>

## [Pseudocode](https://cs50.harvard.edu/x/2023/psets/1/mario/less/#pseudocode)

First, execute

to ensure you’re in your codespace’s default directory.

Then, execute

to change to your `mario-less` directory.

Then, execute

to open the file called `pseudocode.txt` inside that directory.

Write in `pseudocode.txt` some pseudocode that implements this program, even if not (yet!) sure how to write it in code. There’s no one right way to write pseudocode, but short English sentences suffice. Recall how we wrote [pseudocode for finding someone in a phone book](https://docs.google.com/presentation/d/1X3AMSenwZGSE6WxGpzoALAfMg2hmh1LYIJp3N2a1EYI/edit#slide=id.g41907da2bc_0_265). Odds are your pseudocode will use (or imply using!) one or more functions, conditionals, Boolean expressions, loops, and/or variables.

Spoiler

There’s more than one way to do this, so here’s just one!

1.  Prompt user for height
2.  If height is less than 1 or greater than 8 (or not an integer at all), go back one step
3.  Iterate from 1 through height:
    1.  On iteration _i_, print _i_ hashes and then a newline

It’s okay to edit your own after seeing this pseudocode here, but don’t simply copy/paste ours into your own!

## [Prompting for Input](https://cs50.harvard.edu/x/2023/psets/1/mario/less/#prompting-for-input)

Whatever your pseudocode, let’s first write only the C code that prompts (and re-prompts, as needed) the user for input. Open the file called `mario.c` inside of your `mario` directory. (Remember how?)

Now, modify `mario.c` in such a way that it prompts the user for the pyramid’s height, storing their input in a variable, re-prompting the user again and again as needed if their input is not a positive integer between 1 and 8, inclusive. Then, simply print the value of that variable, thereby confirming (for yourself) that you’ve indeed stored the user’s input successfully, a la the below.

```
$ ./mario
Height: -1
Height: 0
Height: 42
Height: 50
Height: 4
Stored: 4
```

Hints

-   Recall that you can compile your program with `make`.
-   Recall that you can print an `int` with `printf` using `%i`.
-   Recall that you can get an integer from the user with `get_int`.
-   Recall that `get_int` is declared in `cs50.h`.
-   Recall that we prompted the user for a positive integer in lecture using a `do while` loop in [`mario.c`](https://cdn.cs50.net/2022/fall/lectures/1/src1/mario8.c?highlight).

## [Building the Opposite](https://cs50.harvard.edu/x/2023/psets/1/mario/less/#building-the-opposite)

Now that your program is (hopefully!) accepting input as prescribed, it’s time for another step.

It turns out it’s a bit easier to build a left-aligned pyramid than right-, a la the below.

```
#
##
###
####
#####
######
#######
########
```

So let’s build a left-aligned pyramid first and then, once that’s working, right-align it instead!

Modify `mario.c` at right such that it no longer simply prints the user’s input but instead prints a left-aligned pyramid of that height.

Hints

-   Keep in mind that a hash is just a character like any other, so you can print it with `printf`.
-   Just as Scratch has a [`repeat`](https://docs.google.com/presentation/d/1mRIN6EDK92NJJlazpFfBNKhxrAQUUxJOJW0UH7knS0g/edit#slide=id.gee4e5a99f9_0_313) block, so does C have a [`for`](https://docs.google.com/presentation/d/1mRIN6EDK92NJJlazpFfBNKhxrAQUUxJOJW0UH7knS0g/edit#slide=id.gee4e5a99f9_0_313) loop, via which you can iterate some number times. Perhaps on each iteration, _i_, you could print that many hashes?
-   You can actually “nest” loops, iterating with one variable (e.g., `i`) in the “outer” loop and another (e.g., `j`) in the “inner” loop. For instance, here’s how you might print a square of height and width `n`, below. Of course, it’s not a square that you want to print!
    
    ```
      for (int i = 0; i < n; i++)
      {
          for (int j = 0; j < n; j++)
          {
              printf("#");
          }
          printf("\n");
      }
    ```

## [Right-Aligning with Dots](https://cs50.harvard.edu/x/2023/psets/1/mario/less/#right-aligning-with-dots)

Let’s now right-align that pyramid by pushing its hashes to the right by prefixing them with dots (i.e., periods), a la the below.

```
.......#
......##
.....###
....####
...#####
..######
.#######
########
```

Modify `mario.c` in such a way that it does exactly that!

Hint

Notice how the number of dots needed on each line is the “opposite” of the number of that line’s hashes. For a pyramid of height 8, like the above, the first line has but 1 hash and thus 7 dots. The bottom line, meanwhile, has 8 hashes and thus 0 dots. Via what formula (or arithmetic, really) could you print that many dots?

### [How to Test Your Code](https://cs50.harvard.edu/x/2023/psets/1/mario/less/#how-to-test-your-code)

Does your code work as prescribed when you input

-   `-1` (or other negative numbers)?
-   `0`?
-   `1` through `8`?
-   `9` or other positive numbers?
-   letters or words?
-   no input at all, when you only hit Enter?

## [Removing the Dots](https://cs50.harvard.edu/x/2023/psets/1/mario/less/#removing-the-dots)

Ara només queda una floritura final! Modifiqueu `mario.c`de tal manera que imprimeixi espais en lloc d'aquests punts!

### [Com provar el vostre codi](https://cs50.harvard.edu/x/2023/psets/1/mario/less/#how-to-test-your-code-1)

Executeu el següent per avaluar la correcció del vostre codi amb `check50`. Però assegureu-vos de compilar-lo i provar-lo vosaltres mateixos també!

```
check50 cs50/problems/2023/x/mario/less
```

Executeu el següent per avaluar l'estil del vostre codi amb `style50`.

Pista

Un espai és només una pressió de la barra espaiadora, de la mateixa manera que un punt és només una pressió de la seva tecla! Només recordeu que això `printf`requereix que els envolteu amb cometes dobles!

## [Com enviar](https://cs50.harvard.edu/x/2023/psets/1/mario/less/#how-to-submit)

Al vostre terminal, executeu el següent per enviar el vostre treball.

```
submit50 cs50/problems/2023/x/mario/less
```