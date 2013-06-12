# Intro
backbone.switcher role is to switch views when a certain attribute of the model has change.
Views are isntansiated each time and are given the "parent" model as a reference. Hence, the Parent view that holds them functions as a somewhat "proxy" for the views.

# Usage
simple usage of switcher:
``` javascript
	var layout = Backbone.View.extend({
		switcher: {
			key: 'resource',
			// 'key' may be a reference to multiple attributes values
			// and may be defined as such:
			// key: 'resource filter'

			views: {
				viewA: SomeViewA,
				viewB: SomeViewB
			}
		},
		
		initialize: function() {
			console.log('init...', this.options);
		}
	});
```