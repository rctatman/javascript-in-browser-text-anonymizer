# Why do I want to learn js?

* people are starting to do ML in js kind of a lot
* most popular language in the world; used everywhere
* allows for greater privacy in ML models

# Learning goal

I want a webpage where a user can enter text & have it "anonymized" (not true anonymizatoin) directly in the browser without having it sent to a server.

* build a privacy perserving in-browser text anonymiser
  * pronoun replacement
    * rule-based lookup (using a list of pronouns?)
    * ended up using POS tagging 
  * detect & remove proper names
    * using capitalization
    * using some sort of lookup 
    * learned NER (named entity recogntion)
  * some sort of seq to seq model to automate anonymization

## Steps

1. [X] figure out how to get javascipt running locally (already installed via web browser)
  1. have a file
  2. write whatever the javascript hello world looks like it in
  3. it's a webpage now?
2. find a way to get the user to supply text
3. a very simple transformation on that text (all lowercase)
4. a more complex transformation (replacing x with somethign else)
  1. pronoun replacement by rule
5. how to store/read in other supporting data
  1. I'm pretty sure this is what json is for
6. Continue to work on/improve anonymization stuff (in keeping with the learning goal above)
7. make it look a bit prettier
8. deploy it somewhere so people can use it
  1. make sure it is privacy perserving

## Things to learn about

* how to set up a local developer environment
  * how to install javascript (apparently it's already in all browswer so I have it installed already)
  * how to use npm (node package manager)
  * how to make it show up in a browser locally? 
  * can I use it in vscode?
  * can is use it in jupyter? is there a js kernel?
    * note: might could be good for local development, prob not for final deployment
* ecosystem
  * what ML packages are avaliable?
    * https://ml5js.org/, tf.js
* general object oriented stuff
  * how does inherience work, etc.
  * how do i tell if something is a class/method etc?
  * is there a capital. scheme I should know about? 
* string manipulation
  * how do I get the text in? 
  * how to pass text out?
  * how to i print stuff in the middle of a block of code?
* relationship to HTML
  * drawing funcationality? (they mention it here: https://p5js.org/)
* optimization/antipatterns to avoid
  * are there are any specific processes that are very slow/memory hungry
  *  semicolons :( (not required!)
* application development in general
* all the stuff I don't know I don't know

# Progress updates

## Day 1: June 14

* [X] Get dev environment set up
  * [HTML Preview](https://marketplace.visualstudio.com/items?itemName=george-alisson.html-preview-vscode)
* [X] Hello world
  * guess before stream: plain text on a html page?
  * yep! javascript is run from within an HTML page; you can show the output by writing it to document or overwriting an existing HTML element
  * document is the head node for an HTML page, all commands will be attributes (?) of it
* [X] Learn about into different frameworks
  * node.js: (i think) a way to run your scripts all server-side, let you have have the same stuff cross-platform; I don't think it will be very useful for this project b/c I want it to work all client side 
  * react: front end library to make UIs & stuff like that. JSX & props & components are react things (react seems to have a very distinct vocabulary it doesn't share with base JS)
    * JSX: JavaScript XML, used for formatting javascript stuff in react (can also use regular javascript)
    * props: react version of function arguments and html attributes, lets you pass data between compontents
    * component: can be either a function or a class
  * Angular: Google web app framework, built on typescript + node.js + some other stuff
    * typescript: strictly typed lang that's a superset of javaScript, from MS
  * Apparently web app frameworks are really happy to cut new major versions


## Day 2: June 15

* [X] Make a text input box & then print the same text back out
* [X] String manipulation (all lower case?)
* Look up things we run across:
  * wasm
    * seems super low level implimentaion of web stuff, maybe not super relevent to me right now
  * canonical reference for javascript? Looks like there are a few, but [the Mozilla one](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/About) says it's a complete reference
    * ecma international (the governing body that sets standardizations for client-side scripting langauges including JavaScript)
  * [Hoisting](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)
    * functions can be used above where they're declared in your code (since they're loaded into memory first)
    * you can use variables above where you declare them the first time but ONLY if you declare them using var (const & let won't work, and while initalizing also serves as a declartion it doesn't load the variable into memory during compiling)

## Day 3: June 16

* [X] JavaScript NLP packages?
  * POS tagging? [This package](https://github.com/dariusk/pos-js) looks like a good start
  * Try to install using npm
  * Need install npm first; [installed node(https://nodejs.org/en/download/)
  * TODO: how to look up matching string in a hierachical iterable object (not sure what the output of pos.Tagger().tag() looks like)
    * from chat: output might be a list of lists? search time complexity might be very bad <.<
* Anything to look up:
  * do I have to use node to use NPM? Answer: I'm doing it, seems like the easiest way
  * JavaScript loops (there are seven of them & apparently you can misapply them to the wrong sort of object and make your life hard)
    * For... in: loops over enumerable properties of the object
    * for... of: loops over iterable objects (e.g. arrays)  


## Day 4: June 17
* [X] Get the pos-js package up & running
  * tried: importing files directly from the old Google version (doesn't require node)
  * ran into not being able to see the console logs: trying to launch broswer let to a werid windows error
* [X] Pronoun replacement!
  * lookup table? (easier to include more pronouns)
  * ended up just looping through the POS tagged text & replacing dependent on the POS tag (all personal pronouns -> they)
* things to look up
  * prototype? the way that javascript handles inheritence: objectConstructor.ptotype.whatever gets passed onto to objects constructed using objectConstructor
  * script tags: in the html, tell the compiler (??) to go grab (and run?) a specific script. More deets [here](https://shawnr.gitbooks.io/practical-introduction-to-javascript/content/basic-syntax/41-adding-javascript-to-an-html-file.html)
  * imports only needed for stuff that's been exported first


Graveyard: 

<div id="result_pos"></div>

function test_pos() {
    var words = new pos.Lexer().lex('This is some sample text. This text can contain multiple sentences.');
    var tagger = new pos.Tagger();
    var taggedWords = tagger.tag(words);
    /* for (i in taggedWords) {
        var taggedWord = taggedWords[i];
        var word = taggedWord[0];
        var tag = taggedWord[1];
        console.log(word + " /" + tag);
    } */

    var taggedWord = taggedWords[0]
    document.getElementById('result_pos').innerHTML = taggedWord;
}

document.getElementById('return').addEventListener('click', test_pos);