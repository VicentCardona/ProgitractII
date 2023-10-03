## [Efectiu](https://cs50.harvard.edu/x/2023/psets/1/cash/#cash)

## [Començant](https://cs50.harvard.edu/x/2023/psets/1/cash/#getting-started)

Obriu el [codi VS.](https://cs50.dev/)

Comenceu fent clic dins de la finestra de la vostra terminal i, a continuació, executeu `cd`\-lo sol. Hauríeu de trobar que la seva "indicació" s'assembla a la següent.

Feu clic dins d'aquesta finestra de terminal i, a continuació, executeu

```
wget https://cdn.cs50.net/2022/fall/psets/1/cash.zip
```

seguit d'Enter per baixar un ZIP anomenat `cash.zip`al vostre espai de codi. Aneu amb compte de no passar per alt l'espai entre `wget`i l'URL següent, o qualsevol altre caràcter!

Ara executa

per crear una carpeta anomenada `cash`. Ja no necessiteu el fitxer ZIP, així que podeu executar-lo

i responeu amb "y" seguit d'Enter a la sol·licitud per eliminar el fitxer ZIP que heu baixat.

Ara escriviu

seguit d'Enter per moure't a (és a dir, obrir) aquest directori. La vostra sol·licitud ara hauria de semblar-se a la següent.

Si tot ha tingut èxit, hauríeu d'executar

i vegeu un fitxer anomenat `cash.c`. L'execució `code cash.c`hauria d'obrir el fitxer on escriureu el codi per a aquest conjunt de problemes. Si no, torna sobre els teus passos i mira si pots determinar on t'has equivocat!

## [Algorismes cobdiciosos](https://cs50.harvard.edu/x/2023/psets/1/cash/#greedy-algorithms)

![monedes dels EUA](https://cs50.harvard.edu/x/2023/psets/1/cash/coins.jpg)

When making change, odds are you want to minimize the number of coins you’re dispensing for each customer, lest you run out (or annoy the customer!). Fortunately, computer science has given cashiers everywhere ways to minimize numbers of coins due: greedy algorithms.

According to the National Institute of Standards and Technology (NIST), a greedy algorithm is one “that always takes the best immediate, or local, solution while finding an answer. Greedy algorithms find the overall, or globally, optimal solution for some optimization problems, but may find less-than-optimal solutions for some instances of other problems.”

What’s all that mean? Well, suppose that a cashier owes a customer some change and in that cashier’s drawer are quarters (25¢), dimes (10¢), nickels (5¢), and pennies (1¢). The problem to be solved is to decide which coins and how many of each to hand to the customer. Think of a “greedy” cashier as one who wants to take the biggest bite out of this problem as possible with each coin they take out of the drawer. For instance, if some customer is owed 41¢, the biggest first (i.e., best immediate, or local) bite that can be taken is 25¢. (That bite is “best” inasmuch as it gets us closer to 0¢ faster than any other coin would.) Note that a bite of this size would whittle what was a 41¢ problem down to a 16¢ problem, since 41 - 25 = 16. That is, the remainder is a similar but smaller problem. Needless to say, another 25¢ bite would be too big (assuming the cashier prefers not to lose money), and so our greedy cashier would move on to a bite of size 10¢, leaving him or her with a 6¢ problem. At that point, greed calls for one 5¢ bite followed by one 1¢ bite, at which point the problem is solved. The customer receives one quarter, one dime, one nickel, and one penny: four coins in total.

It turns out that this greedy approach (i.e., algorithm) is not only locally optimal but also globally so for America’s currency (and also the European Union’s). That is, so long as a cashier has enough of each coin, this largest-to-smallest approach will yield the fewest coins possible. How few? Well, you tell us!

## [Implementation Details](https://cs50.harvard.edu/x/2023/psets/1/cash/#implementation-details)

In `cash.c`, we’ve implemented most (but not all!) of a program that prompts the user for the number of cents that a customer is owed and then prints the smallest number of coins with which that change can be made. Indeed, `main` is already implemented for you. But notice how `main` calls several functions that aren’t yet implemented! One of those functions, `get_cents`, takes no arguments (as indicated by `void`) and returns an `int`. The rest of the functions all take one argument, an `int`, and also return an `int`. All of them currently return `0` so that the code will compile. But you’ll want to replace every `TODO` and `return 0;` with your own code. Specifically, complete the implementation of those functions as follows:

-   Implement `get_cents` in such a way that the function prompts the user for a number of cents using `get_int` and then returns that number as an `int`. If the user inputs a negative `int`, your code should prompt the user again. (But you don’t need to worry about the user inputting, e.g., a `string`, as `get_int` will take care of that for you.) Odds are you’ll find a `do while` loop of help, as in [`mario.c`](https://cdn.cs50.net/2022/fall/lectures/1/src1/mario8.c?highlight)!
-   Implement `calculate_quarters` in such a way that the function calculates (and returns as an `int`) how many quarters a customer should be given if they’re owed some number of cents. For instance, if `cents` is `25`, then `calculate_quarters` should return `1`. If `cents` is `26` or `49` (or anything in between, then `calculate_quarters` should also return `1`. If `cents` is `50` or `74` (or anything in between), then `calculate_quarters` should return `2`. And so forth.
-   Implement `calculate_dimes` in such a way that the function calculates the same for dimes.
-   Implement `calculate_nickels` in such a way that the function calculates the same for nickels.
-   Implement `calculate_pennies` in such a way that the function calculates the same for pennies.

Note that, unlike functions that only have side effects, functions that return a value should do so explicitly with `return`! Take care not to modify the distribution code itself, only replace the given `TODO`s and the subsequent `return` value! Note too that, recalling the idea of abstraction, each of your calculate functions should accept any value of `cents` , not just those values that the greedy algorithm might suggest. If `cents` is 85, for example, `calculate_dimes` should return 8.

Hint

-   Recall that there are several sample programs in Week 1’s [Source Code](https://cdn.cs50.net/2022/fall/lectures/1/src1/) that illustrate how functions can return a value.

Your program should behave per the examples below.

```
$ ./cash
Change owed: 41
4
```

```
$ ./cash
Change owed: -41
Change owed: foo
Change owed: 41
4
```

### [How to Test Your Code](https://cs50.harvard.edu/x/2023/psets/1/cash/#how-to-test-your-code)

For this program, try testing your code manually–it’s good practice:

-   If you input `-1`, does your program prompts you again?
-   If you input `0`, does your program output `0`?
-   If you input `1`, does your program output `1` (i.e., one penny)?
-   If you input `4`, does your program output `4` (i.e., four pennies)?
-   If you input `5`, does your program output `1` (i.e., one nickel)?
-   If you input `24`, does your program output `6` (i.e., two dimes and four pennies)?
-   If you input `25`, does your program output `1` (i.e., one quarter)?
-   If you input `26`, does your program output `2` (i.e., one quarter and one penny)?
-   Si introduïu `99`, surt el vostre programa `9`(és a dir, tres quarts, dos cèntims i quatre cèntims)?

També podeu executar el següent per avaluar la correcció del vostre codi mitjançant `check50`. Però assegureu-vos de compilar-lo i provar-lo vosaltres mateixos també!

```
check50 cs50/problems/2023/x/cash
```

No es `check50`pot compilar el codi?

Assegureu-vos que només heu modificat aquelles parts del programa marcades com a `TODO`. Si modifiqueu la `main`funció o afegiu alguna variable global, per exemple, és possible que el vostre codi **no es pugui compilar** . `check50`provarà les teves cinc funcions de manera independent, més enllà de comprovar la resposta final.

I executeu el següent per avaluar l'estil del vostre codi amb `style50`.

## [Com enviar](https://cs50.harvard.edu/x/2023/psets/1/cash/#how-to-submit)

Al vostre terminal, executeu el següent per enviar el vostre treball.

```
submit50 cs50/problems/2023/x/cash
```