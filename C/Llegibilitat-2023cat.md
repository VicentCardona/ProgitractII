## [Llegibilitat](https://cs50.harvard.edu/x/2023/psets/2/readability/#readability)

Per a aquest problema, implementareu un programa que calcula el nivell de qualificació aproximat necessari per comprendre algun text, segons el següent.

```
$ ./readability
Text: Congratulations! Today is your day. You're off to Great Places! You're off and away!
Grade 3
```

## [Començant](https://cs50.harvard.edu/x/2023/psets/2/readability/#getting-started)

Obriu el [codi VS.](https://cs50.dev/)

Comenceu fent clic dins de la finestra de la vostra terminal i, a continuació, executeu `cd`\-lo sol. Hauríeu de trobar que la seva "indicació" s'assembla a la següent.

Feu clic dins d'aquesta finestra de terminal i, a continuació, executeu

```
wget https://cdn.cs50.net/2022/fall/psets/2/readability.zip
```

seguit d'Enter per baixar un ZIP anomenat `readability.zip`al vostre espai de codi. Aneu amb compte de no passar per alt l'espai entre `wget`i l'URL següent, o qualsevol altre caràcter!

Ara executa

per crear una carpeta anomenada `readability`. Ja no necessiteu el fitxer ZIP, així que podeu executar-lo

i responeu amb "y" seguit d'Enter a la sol·licitud per eliminar el fitxer ZIP que heu baixat.

Ara escriviu

seguit d'Enter per moure't a (és a dir, obrir) aquest directori. La vostra sol·licitud ara hauria de semblar-se a la següent.

Si tot ha tingut èxit, hauríeu d'executar

i vegeu un fitxer anomenat `readability.c`. L'execució `code readability.c`hauria d'obrir el fitxer on escriureu el codi per a aquest conjunt de problemes. Si no, torna sobre els teus passos i mira si pots determinar on t'has equivocat!

## [Fons](https://cs50.harvard.edu/x/2023/psets/2/readability/#background)

Segons [Scholastic ,](https://www.scholastic.com/teachers/teaching-tools/collections/guided-reading-book-lists-for-every-level.html) _la web de Charlotte_ d'EB White es troba entre un nivell de lectura de segon i quart de primària, i _The Giver_ de Lois Lowry es troba entre un nivell de lectura de vuitè i dotzè grau. Què vol dir, però, que un llibre estigui a un nivell de lectura determinat?

Well, in many cases, a human expert might read a book and make a decision on the grade (i.e., year in school) for which they think the book is most appropriate. But an algorithm could likely figure that out too!

So what sorts of traits are characteristic of higher reading levels? Well, longer words probably correlate with higher reading levels. Likewise, longer sentences probably correlate with higher reading levels, too.

A number of “readability tests” have been developed over the years that define formulas for computing the reading level of a text. One such readability test is the _Coleman-Liau index_. The Coleman-Liau index of a text is designed to output that (U.S.) grade level that is needed to understand some text. The formula is

```
index = 0.0588 * L - 0.296 * S - 15.8
```

where `L` is the average number of letters per 100 words in the text, and `S` is the average number of sentences per 100 words in the text.

Let’s write a program called `readability` that takes a text and determines its reading level. For example, if user types in a line of text from Dr. Seuss, the program should behave as follows:

```
$ ./readability
Text: Congratulations! Today is your day. You're off to Great Places! You're off and away!
Grade 3
```

The text the user inputted has 65 letters, 4 sentences, and 14 words. 65 letters per 14 words is an average of about 464.29 letters per 100 words (because 65 / 14 \* 100 = 464.29). And 4 sentences per 14 words is an average of about 28.57 sentences per 100 words (because 4 / 14 \* 100 = 28.57). Plugged into the Coleman-Liau formula, and rounded to the nearest integer, we get an answer of 3 (because 0.0588 \* 464.29 - 0.296 \* 28.57 - 15.8 = 3): so this passage is at a third-grade reading level.

Let’s try another one:

```
$ ./readability
Text: Harry Potter was a highly unusual boy in many ways. For one thing, he hated the summer holidays more than any other time of year. For another, he really wanted to do his homework, but was forced to do it in secret, in the dead of the night. And he also happened to be a wizard.
Grade 5
```

This text has 214 letters, 4 sentences, and 56 words. That comes out to about 382.14 letters per 100 words, and 7.14 sentences per 100 words. Plugged into the Coleman-Liau formula, we get a fifth-grade reading level.

As the average number of letters and words per sentence increases, the Coleman-Liau index gives the text a higher reading level. If you were to take this paragraph, for instance, which has longer words and sentences than either of the prior two examples, the formula would give the text an twelfth-grade reading level.

```
$ ./readability
Text: As the average number of letters and words per sentence increases, the Coleman-Liau index gives the text a higher reading level. If you were to take this paragraph, for instance, which has longer words and sentences than either of the prior two examples, the formula would give the text an twelfth-grade reading level.
Grade 12
```

Watch a Recording

## [Specification](https://cs50.harvard.edu/x/2023/psets/2/readability/#specification)

Design and implement a program, `readability`, that computes the Coleman-Liau index of text.

-   Implement your program in a file called `readability.c` in a directory called `readability`.
-   Your program must prompt the user for a `string` of text using `get_string`.
-   Your program should count the number of letters, words, and sentences in the text. You may assume that a letter is any lowercase character from `a` to `z` or any uppercase character from `A` to `Z`, any sequence of characters separated by spaces should count as a word, and that any occurrence of a period, exclamation point, or question mark indicates the end of a sentence.
-   Your program should print as output `"Grade X"` where `X` is the grade level computed by the Coleman-Liau formula, rounded to the nearest integer.
-   If the resulting index number is 16 or higher (equivalent to or greater than a senior undergraduate reading level), your program should output `"Grade 16+"` instead of giving the exact index number. If the index number is less than 1, your program should output `"Before Grade 1"`.

### [Getting User Input](https://cs50.harvard.edu/x/2023/psets/2/readability/#getting-user-input)

Let’s first write some C code that just gets some text input from the user, and prints it back out. Specifically, implement in `readability.c` a `main` function that prompts the user with `"Text: "` using `get_string` and then prints that same text using `printf`. And remember, as you work through this program, that if you make use of any library functions, be sure to `#include` any corresponding header files.

The program should behave per the below.

```
$ ./readability
Text: In my younger and more vulnerable years my father gave me some advice that I've been turning over in my mind ever since.
In my younger and more vulnerable years my father gave me some advice that I've been turning over in my mind ever since.
```

### [Letters](https://cs50.harvard.edu/x/2023/psets/2/readability/#letters)

Now that you’ve collected input from the user, let’s begin to analyze that input by first counting the number of letters in the text. Consider letters to be uppercase or lowercase alphabetical character, not punctuation, digits, or other symbols.

Add to `readability.c`, below `main`, a function called `count_letters` that takes one argument, a `string` of text, and that returns an `int`, the number of letters in that text. Be sure to add the function’s prototype, too, atop your file, so that `main` knows how to call it. Odds are the prototype should resemble the below:

```
int count_letters(string text)
```

Then call that function in `main` so that, instead of printing out the text itself, your program now prints the number of letters in the text.

The program should now behave per the below.

```
$ ./readability
Text: Alice was beginning to get very tired of sitting by her sister on the bank, and of having nothing to do: once or twice she had peeped into the book her sister was reading, but it had no pictures or conversations in it, "and what is the use of a book," thought Alice "without pictures or conversation?"
235 letters
```

Hint

Declared in `ctype.h` is a function that you might find helpful, per [manual.cs50.io](https://manual.cs50.io/). If you use it, be sure to include that header file atop your own code!

### [Words](https://cs50.harvard.edu/x/2023/psets/2/readability/#words)

The Coleman-Liau index cares not only about the number of letters but also about the number of words in a sentence. For the purpose of this problem, we’ll consider any sequence of characters separated by a space to be a word (so a hyphenated word like `"sister-in-law"` should be considered one word, not three).

Add to `readability.c`, below `main`, a function called `count_words` that takes one argument, a `string` of text, and that returns an `int`, the number of words in that text. Be sure to add the function’s prototype, too, atop your file, so that `main` knows how to call it. (We leave its prototype to you!)

Then call that function in `main` so that your program also prints the number of words in the text.

You may assume that a sentence:

-   will contain at least one word;
-   will not start or end with a space; and
-   will not have multiple spaces in a row.

You are, of course, welcome to attempt a solution that will tolerate multiple spaces between words or indeed, no words!

The program should now behave per the below.

```
$ ./readability
Text: It was a bright cold day in April, and the clocks were striking thirteen. Winston Smith, his chin nuzzled into his breast in an effort to escape the vile wind, slipped quickly through the glass doors of Victory Mansions, though not quickly enough to prevent a swirl of gritty dust from entering along with him.
250 letters
55 words
```

### [Sentences](https://cs50.harvard.edu/x/2023/psets/2/readability/#sentences)

The last piece of information that the Coleman-Liau formula cares about, in addition to the number of letters and words, is the number of sentences. Determining the number of sentences can be surprisingly trickly. You might first imagine that a sentence is just any sequence of characters that ends with a period, but of course sentences could end with an exclamation point or a question mark as well. But of course, not all periods necessarily mean the sentence is over. For instance, consider the sentence below.

```
Mr. and Mrs. Dursley, of number four Privet Drive, were proud to say that they were perfectly normal, thank you very much.
```

This is just a single sentence, but there are three periods! For this problem, we’ll ask you to ignore that subtlety: you should consider any sequence of characters that ends with a `.` or a `!` or a `?` to be a sentence (so for the above “sentence”, you should count it as three sentences). In practice, sentence boundary detection needs to be a little more intelligent to handle these cases, but we’ll not worry about that for now.

Add to `readability.c`, below `main`, a function called `count_sentences` that takes one argument, a `string` of text, and that returns an `int`, the number of sentences in that text. Be sure to add the function’s prototype, too, atop your file, so that `main` knows how to call it. (We again leave its prototype to you!)

Then call that function in `main` so that your program also prints the number of sentences in the text.

The program should now behave per the below.

```
$ ./readability
Text: When he was nearly thirteen, my brother Jem got his arm badly broken at the elbow. When it healed, and Jem's fears of never being able to play football were assuaged, he was seldom self-conscious about his injury. His left arm was somewhat shorter than his right; when he stood or walked, the back of his hand was at right angles to his body, his thumb parallel to his thigh.
295 letters
70 words
3 sentences
```

### [Putting it All Together](https://cs50.harvard.edu/x/2023/psets/2/readability/#putting-it-all-together)

Now it’s time to put all the pieces together! Recall that the Coleman-Liau index is computed using the formula:

```
index = 0.0588 * L - 0.296 * S - 15.8
```

where `L` is the average number of letters per 100 words in the text, and `S` is the average number of sentences per 100 words in the text.

Modify `main` in `readability.c` so that instead of outputting the number of letters, words, and sentences, it instead outputs (only) the grade level as defined by the Coleman-Liau index (e.g. `"Grade 2"` or `"Grade 8" or the like`). Be sure to round the resulting index number to the nearest `int`!

Hints

-   Recall that `round` is declared in `math.h`, per [manual.cs50.io](https://manual.cs50.io/)!
-   Recall that, when dividing values of type `int` in C, the result will also be an `int`, with any remainder (i.e., digits after the decimal point) discarded. Put another way, the result will be “truncated.” You might want to cast your one or more values to `float` before performing division when calculating `L` and `S`!

If the resulting index number is 16 or higher (equivalent to or greater than a senior undergraduate reading level), your program should output `"Grade 16+"` instead of outputting an exact index number. If the index number is less than 1, your program should output `"Before Grade 1"`.

## [Walkthrough](https://cs50.harvard.edu/x/2023/psets/2/readability/#walkthrough)

<iframe allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" data-video="" src="https://www.youtube.com/embed/AOVyZEh9zgE?modestbranding=0&amp;rel=0&amp;showinfo=0" scrolling="no" data-ruffle-polyfilled="" id="iFrameResizer0"></iframe>

## [How to Test Your Code](https://cs50.harvard.edu/x/2023/psets/2/readability/#how-to-test-your-code)

Proveu d'executar el vostre programa amb els textos següents, per assegurar-vos que veieu el nivell de grau especificat. Assegureu-vos de copiar només el text, sense espais addicionals.

-   `One fish. Two fish. Red fish. Blue fish.`(Abans de 1r grau)
-   `Would you like them here or there? I would not like them here or there. I would not like them anywhere.`(2n grau)
-   `Congratulations! Today is your day. You're off to Great Places! You're off and away!`(Grau 3)
-   `Harry Potter was a highly unusual boy in many ways. For one thing, he hated the summer holidays more than any other time of year. For another, he really wanted to do his homework, but was forced to do it in secret, in the dead of the night. And he also happened to be a wizard.`(5è grau)
-   `In my younger and more vulnerable years my father gave me some advice that I've been turning over in my mind ever since.`(7è grau)
-   `Alice was beginning to get very tired of sitting by her sister on the bank, and of having nothing to do: once or twice she had peeped into the book her sister was reading, but it had no pictures or conversations in it, "and what is the use of a book," thought Alice "without pictures or conversation?"`(8è grau)
-   `When he was nearly thirteen, my brother Jem got his arm badly broken at the elbow. When it healed, and Jem's fears of never being able to play football were assuaged, he was seldom self-conscious about his injury. His left arm was somewhat shorter than his right; when he stood or walked, the back of his hand was at right angles to his body, his thumb parallel to his thigh.`(8è grau)
-   `There are more things in Heaven and Earth, Horatio, than are dreamt of in your philosophy.`(9è grau)
-   `It was a bright cold day in April, and the clocks were striking thirteen. Winston Smith, his chin nuzzled into his breast in an effort to escape the vile wind, slipped quickly through the glass doors of Victory Mansions, though not quickly enough to prevent a swirl of gritty dust from entering along with him.`(10è grau)
-   `A large class of computational problems involve the determination of properties of graphs, digraphs, integers, arrays of integers, finite families of finite sets, boolean formulas and elements of other countable domains.`(Grau 16+)

Executeu el següent per avaluar la correcció del vostre codi amb `check50`. Però assegureu-vos de compilar-lo i provar-lo vosaltres mateixos també!

```
check50 cs50/problems/2023/x/readability
```

Executeu el següent per avaluar l'estil del vostre codi amb `style50`.

## [Com enviar](https://cs50.harvard.edu/x/2023/psets/2/readability/#how-to-submit)

Al vostre terminal, executeu el següent per enviar el vostre treball.

```
submit50 cs50/problems/2023/x/readability
```
