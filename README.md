# JsNamespaceRails


Rails's asset pipeline compiles all of js file into a single file which is executed on all pages.
There has a problem, some time we want to execute selective code on specific page, but asset pipeline doesn't support.
js-namespace-rails can handle this problem by using it's method to namespace and selectively execute certain javascript depending on which Rails controller action is active.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'js-namespace-rails', github: 'falm/js-namepsace-rails'
```

## Setup

Require js-namespace-rails file in application.js or other bundle,notice js-namespace-rails depends on jquery so you need require 'jquery' before

``` js

//= require jquery
//= require js-namespace-rails

```


## Usage
Assume your project have articles_controller
``` ruby
    class ArticlesController < ApplicationController
		def index
		end
	end
```
And its corresponding js file app/assets/javascripts/articles.js.erb

then you just need to write blew into the js file
``` js
	// app/assets/javascripts/articles.js.erb
	JsSpace.on('articles', {
		init: function(){
			console.log('common logic of article in here');
		},
		index: function(){
			console.log('logic of index action in here');
		}
	});
```

## License
MIT License.




