## Pre-Requisites

You've cloned the repo via:

````sh
$ git clone git@github.com:ithinkihaveacat/beebo-bootstrap.git
````

You've added the correct upstream via:

````sh
$ git remote add upstream https://github.com/twbs/bootstrap
````

You've run `npm install`:

````sh
$ npm install
````

You've installed `grunt`:

````sh
$ npm install -g grunt-cli
````

## Making Changes

Pretty much everything you would want to change is in `less/variables.less`; see [the documentation](http://getbootstrap.com/customize/#less-variables).

## Generating Assets

Pull in the latest changes:

````sh
$ git fetch --all --tags
$ git checkout -b tmp v3.0.3 # latest tag from twbs/bootstrap; git tag | tail -1
$ git checkout master
$ git merge tmp # fix conflicts if necessary (ignore changes in dist/: git theirs dist/css/*)
$ git branch -d tmp
````

Update dependencies:

````sh
$ npm update
````

Generate the assets:

````sh
# generates the assets in dist/
$ grunt dist-css 
$ grunt dist-js
````

(The `dist` target by itself also updates the CSS and JS in the `docs/`
directory...)

## Installation

Copy to appropriate location (edit as required):

````sh
$ grunt dist-css ; and cp dist/css/* ~/workspace/beebo-site/public/css
````
