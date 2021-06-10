# Why do I want to learn js?

* people are starting to do ML in js kind of a lot
* most popular language in the world; used everywhere
* allows for greater privacy in ML models

# Learning goal

I want a webpage where a use can enter text & have it "anonymized" (not true anonymizatoin) directly in the browser without having it sent to a server.

* build a privacy perserving in-browser text anonymiser
  * pronoun replacement
    * rule-based lookup (using a list of pronouns)
  * detect & remove proper names
    * using capitalization
    * using some sort of lookup 
    * learned NER (named entity recogntion)
  * some sort of seq to seq model to automate anonymization

## Steps

1. figure out how to get javascipt running locally (already installed via web browser)
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