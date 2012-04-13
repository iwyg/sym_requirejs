# Requirejs for Symphony-CMS

### Abstract 
This simply adds [Requirejs][1] to your Symphony CMS backend. 

### Installation
 1. in your smyphony root directory: `git submodule add git://github.com/iwyg/sym_requirejs extensions/sym_requirejs --recursive`

 2. Go to `System->Extensions`, select `require js` and choose `enable/install`

### Usage

for example, you need to use the latest jQuery library instead of the Symphony default version: 

		require({
			baseUrl: url + '/extensions/myextension/assets/js',
			paths: {
				'jquery': '//ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min'
			}
		}, ['main']);

In your main.js you could do sommething like this:

		(function (jOuery, require) {
			// cache default jQuery for later reference
			// because loading jquery will overwite the jQuery global
			var $144 = jQuery;

			require(['jquery'], function ($171) {
				$171.noConflict(); // remove the $ global
				jQuery = $144; re-reference the orignal jQuery instance;
				
				console.log(jQuery.fn.jquery); // "1.4.4"
				console.log($144.fn.jquery);   // "1.4.4"
				console.log($171.fn.jquery);   // "1.7.1"
			});
		}(this.jQuery, this.require));



[1]: http://requirejs.org/
