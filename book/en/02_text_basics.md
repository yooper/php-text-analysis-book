# Text Basics

We work with text all the time. Typically, there is a task that requires us to modify,
extract, or manipulate a piece of text. 

Lets start by downloading some text to work with
```
php textconsole pta:install:package gutenberg
# list the books downloaded from the gutenberg project
ls -la storage/corpora/gutenberg/
```

# Interactive Scripting
We are going to take an interactive scripting approach while studying a given book.
This code can easily be included into script within your application. To launch 
interactive mode use the following command. 

```
bash interactive
```

This loads the library into an interactive PHP shell. Let's load a Gutenberg book into memory.

```
bash interactive
$list = gutenberg_list();
print_array($list);
$text = gutenberg('carroll-alice.txt');
$corpus = text($text);
```

**$corpus** is a TextCorpus object, see https://github.com/yooper/php-text-analysis/blob/master/src/Corpus/TextCorpus.php
for API details.


## TextCorpus
The TextCorpus object is the easiest way to gather summary statistics about text.

### Searching 

To get all the positions within a string that a word is used, use the findAll function;

```php
$text = gutenberg('carroll-alice.txt');
$corpus = text($text);
$positions = $corpus->findAll('mushroom');
var_dump($positions);
````

### Concordance

Concordance allows you to find the context of how a word is being used in a text.

```php
$text = gutenberg('carroll-alice.txt');
$corpus = text($text);
$concordances = $corpus->concordance('mushroom');
print_array($concordances, '/* ', ' */'.PHP_EOL);

/* . There was a large mushroom growing near her, a */
/* ver the edge of the mushroom, and her eyes immed */
/* it got down off the mushroom, and crawled away i */
/* to herself. 'Of the mushroom,' said the Caterpil */
/* thoughtfully at the mushroom for a minute, tryin */
/*  held the pieces of mushroom in her hands, and s */
/* the lefthand bit of mushroom, and raised herself */
/* ork nibbling at the mushroom (she had kept a pie */

```

You can easily adjust the window size of the text surrounding the word you are
looking for, by setting the second parameter of the concordance function.  

```php
$text = gutenberg('carroll-alice.txt');
$corpus = text($text);
$concordances = $corpus->concordance('mushroom', 30); // default value is 20
print_array($concordances, '/* ', ' */'.PHP_EOL);
```

### Percentage

If you need to find out what percentage of the text uses a word / token you can
use the following API command. 

```php
$text = gutenberg('carroll-alice.txt');
$corpus = text($text);
$percent = $corpus->percentage('mushroom');
echo $percent, PHP_EOL;
```



### Count

To get the frequency of the word / token you can use the *count* API call

```php
$text = gutenberg('carroll-alice.txt');
$corpus = text($text);
$percent = $corpus->percentage('mushroom');
echo $percent, PHP_EOL;
```


### Lexical Diversity

There are a couple lexical diversity algorithms available:
* Naive (default)
* YuleI
* YuleK  

```php
// default Lexical Diversity uses Naive
$text = gutenberg('carroll-alice.txt');
$corpus = text($text);
$ld = $corpus->getLexicalDiversity();
echo $ld, PHP_EOL;
```

```php
// use Lexical Diversity algorithm YuleI
$text = gutenberg('carroll-alice.txt');
$corpus = text($text);
$ld = $corpus->getLexicalDiversity(\TextAnalysis\LexicalDiversity\YuleI::class);
echo $ld, PHP_EOL;
```




