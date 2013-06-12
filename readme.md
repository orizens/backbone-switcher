# Intro
backbone.switcher role is to switch views when a certain attribute of the model has change.
Views are isntansiated each time and are given the "parent" model as a reference. Hence, the Parent view that holds them functions as a somewhat "proxy" for the views.

## Requirements
switcher is an extension on top of [backbone.beamer](https://github.com/orizens/Backbone.Beamer)

## Usage
simple usage of switcher:
``` javascript
	var layout = Backbone.View.extend({
		switcher: {
			// 'key' is a reference to an attribute in "this.model"
			// it tells the view to listen to change event of the "resource" attribute
			key: 'resource',
			
			// the keys "viewA", "viewB" are possible values
			// of the "resource" attribute in "this.model"
			// "SettingsView" is a reference to some custom Backbone.View object (not an instance)
			views: {
				settings: SettingsView,
				help: HelpView
			}
		},
		
		initialize: function() {
			console.log('init...', this.options);
		}
	});
	
	// later in the instance of layout
	var layoutView = new layout({ model: contactModel });
	contactModel.set({ resource: "settings" });
	// now layoutView will remove the current active view and
	// will instansiate a new viewA instance, and render it to layoutView.el DOM element.
```
