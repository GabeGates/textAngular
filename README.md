GabeGates/textAngular v1.5.17
===========

## Requirements

1. `AngularJS` ~ `1.5.x`
2. `Rangy` ~ `1.3.x`, Both rangy-core and rangy-selectionsaverestore are required. (There is a minified combination of these two included in the dist folder)
3. `Bootstrap` ^ `3.x` for the default styles and glyphicons (Can use `bootstrap-css-only`, you must add this to your bower or include this manually)
4. NOTE: please check the requirements for earlier releases, if these are an issue.

### Where to get it

**NOTE:** Our `textAngular-sanitize.js` and angular.js's `angular-sanitize.js` are the SAME file, you must include one or the other but not both. We highly recommend using `textAngular-sanitize.js` as it loosens some parts of the sanitizer that are far too strict for our uses and adds some more features we need.

**Via Bower:**

Run `bower install https://github.com/GabeGates/textAngular` from the command line.
Include script tags similar to the following:
```html
<link rel='stylesheet' href='/bower_components/textAngular/dist/textAngular.css'>
<script src='/bower_components/textAngular/dist/textAngular-rangy.min.js'></script>
<script src='/bower_components/textAngular/dist/textAngular-sanitize.min.js'></script>
<script src='/bower_components/textAngular/dist/textAngular.min.js'></script>
```

**Via Github**

Download the code from [https://github.com/GabeGates/textAngular/releases/latest](https://github.com/GabeGates/textAngular/releases/latest), unzip the files then add script tags similar to the following:
```html
<link rel='stylesheet' href='/path/to/unzipped/files/dist/textAngular.min.css'>
<script src='/path/to/unzipped/files/dist/textAngular-rangy.min.js'></script>
<script src='/path/to/unzipped/files/dist/textAngular-sanitize.min.js'></script>
<script src='/path/to/unzipped/files/dist/textAngular.min.js'></script>
```

### Usage

1. Include (`rangy-core.js` and `rangy-selectionsaverestore.js`) or `textAngular-rangy.min.js` in your project using script tags
2. Include `textAngular-sanitize.js` or `textAngular-sanitize.min.js` in your project using script tags
3. Include (`textAngularSetup.js` and `textAngular.js`) or `textAngular.min.js` (textAngularSetup.js is included inside textAngular.min.js)
4. Add a dependency to `textAngular` in your app module, for example: ```angular.module('myModule', ['textAngular'])```.
5. Create an element to hold the editor and add an `ng-model="htmlVariable"` attribute where `htmlVariable` is the scope variable that will hold the HTML entered into the editor:
```html
<div text-angular ng-model="htmlVariable"></div>
```
OR
```html
<text-angular ng-model="htmlVariable"></text-angular>
```
This acts similar to a regular AngularJS / form input if you give it a name attribute, allowing for form submission and AngularJS form validation.

Have fun!

**Important Note:** Though textAngular supports the use of all attributes in it's input, please note that angulars ng-bind-html **WILL** strip out all of your style attributes if you are using `angular-sanitize.js`.

For Additional options see the [github Wiki](https://github.com/GabeGates/textAngular/wiki).

### Issues?

textAngular uses ```execCommand``` for the rich-text functionality.
That being said, its still a fairly experimental browser feature-set, and may not behave the same in all browsers - see http://tifftiff.de/contenteditable/compliance_test.html for a full compliance list.
It has been tested to work on Chrome, Safari, Opera, Firefox and Internet Explorer 8+.
If you find something, please let me know - throw me a message, or submit an issue request!

## Developer Notes

When checking out, you need a node.js installation, running `npm install` and then `bower install` will get you setup with everything to run the unit tests and minification.
All changes should be done in the src folder, running `grunt compile` to compile the app or use `grunt watch` to compile the files as you save them.
When you are ready to create A PR check that `grunt` passes without errors and you have created tests for your feature if necessary. `grunt setVersion` will update versions referenced in our files using the version in package.json

## Customization

It is possible to override the toolbar by using a decorator in the module's .config block. Simply set the taOptions.toolbar to an array of arrays comprised of button names. Each array of button names represents a button group. The default toolbar can be represented like so:
```html
  taOptions.toolbar = [
      ['h1', 'h2', 'h3', 'h4', 'h5', 'h6', 'p', 'pre', 'quote'],
      ['bold', 'italics', 'underline', 'strikeThrough', 'ul', 'ol', 'redo', 'undo', 'clear'],
      ['justifyLeft', 'justifyCenter', 'justifyRight', 'indent', 'outdent'],
      ['html', 'insertImage','insertLink', 'insertVideo', 'wordcount', 'charcount']
  ];
```
New buttons can be created using taRegisterTool. Examples can be found inside demo/static-demo.html

## License

This project is licensed under the [MIT license](http://opensource.org/licenses/MIT).


## Forked From

For any original information check out the original forked repository.

For original project: https://github.com/textAngular/textAngular

Also using colorpicker.js from https://github.com/DavidDurman/FlexiColorPicker
