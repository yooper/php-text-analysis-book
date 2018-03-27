# Getting Started

We work with text every single day. And everyday we are hunting through PHP.net or
Stackoverflow looking for solutions for our assigned task. Our task may be as mundane
as extracting the domain from an email address or as sophisticated as extracting 
keywords from text. 

# Getting Started with PHP Text Analysis

You are going to need **composer**, https://getcomposer.org/. Once, *composer* is
installed your life will be infinitely easier doing development in PHP. 


### A New Project
If you are starting a new text analysis project use the following commands. 
```
php composer init
// fill in the questions with place holders
composer require yooper/php-text-analysis
composer install
```
### A Pre Existing Project

If you want to include in an existing project ...

```
composer require yooper/php-text-analysis
composer install
```

### Developing PHP Text Analysis

This is for development of PHP Text Analysis

```
git clone git@github.com:yooper/php-text-analysis.git
cd php-text-analysis/
composer install
# run the unit tests
SKIP_TEST=1 ./vendor/bin/phpunit
```

### Commands
PTA does have some commands for installing Corpora. How those commands integrate
into your project is left to you. 

After you have the command **textconsole** integrated, type:
```
php textconsole
```

to get a list of the available commands. 


**todo** provide example of command integration for Laravel and/or Symfony project


# Installing PTA Corpora
PTA comes with a set of Corpora available for download. A majority of the corpora
were taken from the NLTK project. In order to install a corpus, you must be able
to install them via the **textconsole** command. 

### List Available Corpora
To get a list of the current Corpora available.

```
php textconsole pta:list
```

You will receive back a list of available corpora. 

### Install a Corpus
If you want to install any corpus use the following command:

```
 pta:install:package twitter_samples
```

This will install the corpus into the **storage/corpus/twitter_samples** directory. 

### Installing Stanford's NER and POS Tagger
PTA allows you to easily add NER and POS Tagging using Stanford's prebuilt libraries. 
To use the libraries Java must be installed on your system

```
# install the ner tagger
php textconsole pta:install:package stanford_ner_tagger
# install the pos tagger
php textconsole pta:install:package stanford_pos_tagger
```













