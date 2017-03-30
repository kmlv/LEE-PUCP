# Step-by-step

## required

* mkdocs

* pandoc

* reveal js

## Setting mkdocs 

* `cd` to the dir where you want to start the repo directory

* `mkdocs new Econ100a_w17`

* `cd Econ100a_w17`

* Serve locally: `mkdocs serve`

* Go to [http://127.0.0.1:8000/](http://127.0.0.1:8000/)


## setting up reveal.js

* Create and develop the new .md pages following this http://www.mkdocs.org/#adding-pages

* Copy the reveal.js directory AND the js directory, or follow Eric's tutorial. 



## Publishing

* Push to github repo (add, commit, push)

* `cd docs` and convert md to reveal:
    `pandoc  -t revealjs -V revealjs-url=reveal.js --css=reveal.js/css/theme/simple.css -H reveal.js/js/revealMathJax.js -s S__.md -o S__.html`

* Deploy to github pages from directory that contains /docs. 
    `mkdocs gh-deploy`

## Todo

* Table of contents on mkdocs page

* Margins on Reveal.js

* Slide number in reveal.js slides

