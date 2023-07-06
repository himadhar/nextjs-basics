title: 'Improve JavaScript: Creating a Plugin using jQuery'
'
date: '2015-12-10'
------------------

# Improve JavaScript: Creating a Plugin using jQuery

## Introduction

![](/images/blogs/jquery.jpeg)

Creating JavaScript plugins can enhance code reusability and improve the functionality of your web applications. This article explains how to create a plugin using jQuery, a popular JavaScript library.

This blog aims to demonstrate step by step approach in building a jQuery plugin for your consumption in web projects. A plugin basically helps you to write a code, which you might need multiple times in your application and consuming them whenever necessary.

From jQuery home: “A jQuery plugin is simply a new method that we use to extend jQuery’s prototype object. By extending the prototype object you enable all jQuery objects to inherit any methods that you add. As established, whenever you call `jQuery()` you’re creating a new jQuery object, with all of jQuery’s methods inherited.”

The aim of this blog is to finally provide you with a logical structure in building a plugin and, to begin with, lets see, how a basic structure of a plugin looks like:

```
(function ( $ ) {
  var valuesYouNeed  = 0;
  $.fn.yourPlugin = function() {
    return this;
  };
}( jQuery ));
```

---

#### Below is the explanation for the code line by line:

1. Encapsulation of the code begins
2. Declare variables you would need common for the plugin and applications built on it
3. Add a param to jQuery by tagging “yourPlugin” to `$.fn`. This way, “yourPlugin” will be available to you just like any other jQuery methods (css, height and so on)
4. Return the logical conclusion for the plugin, say for example, you wish to change the color of the “this” element, you return the same. i.e., `return this.css(‘color’, ‘black’)`
5. Wrap your plugin’s code
6. End of encapsulation and tagging the function to the jQuery included in your project. You could simply ignore line 1 and 6. But to ensure that the function is chained and other plugins using the “$” as alias will have no issues, we encapsulate within the jQuery fold.

---

Now, calling this function is as simple as writing the code – `$(“#selector”).yourPlugin()`  – All you wished to happen in your code takes place and the output gets implemented.

Let's spice it up by making it even more generic. i.e., jQuery offers multiple selectors to be included while implementing any code of its. So, `$(‘#selector1, #selector2’).css(‘color’, ‘black’)`, will make both the elements’ colors referred to here into black. To achieve this, we simply add one more param in the above code:

```
(function ( $ ) {
    var valuesYouNeed  = 0;
    $.fn.yourPlugin = function() {
       return this.each(function() {
         // Your logic for each element goes here.
      });
   };
}( jQuery ));
```

---

## Steps to Create a jQuery Plugin

1. **Set up the Plugin Structure**: Start by creating a basic structure for your plugin. Create a new JavaScript file and define your plugin as a jQuery function.

```javascript
   (function ($) {
     $.fn.yourPluginName = function (options) {
       // Plugin code goes here
     };
   })(jQuery);
```

---

You can add your logic within the return block and things will get applied to all the selectors you included. basically, we are just iterating through each of the selectors passed in the request, applying the changes and catching the next one to repeat the actions.

We now know how to write a basic structure for a generic plugin. I will now proceed by writing a plugin that builds a DOM and appends to the selector passed in the request. Below is a sample plugin that adds the word “hello” as the content of the selector its requested into.

```
(function ( $ ) {
    $.fn.updateSelector= function() {
       return this.each(function() {
          $(this).append('hello');
      });
   };
}( jQuery ));
```

To implement this plugin, we simply call the “updateSelector” into the document ready function from jQuery tagged to an element:

```
$(document).ready(function () {
   $('.selector').updateSelector();
 });
```

And Voila, the rendering is done!

---

Basic update of elements aren’t the basic purposes for which a tool as powerful as a plugin can come in handy. You can go ahead and add parameters for manipulations, to make it as generic as possible.

Following is a sample of logic, where it takes an array as params and builds a string and renders it back to the selector.

```
(function ($) {
  $.fn.dataPlugin = function (options) {
        var options = $.extend({
            data: [1,2,3]
        }, options);
        var make = function () {
            var str = "";
            for(i=0; i<options.data.length; i++){
                str += options.data[i];
                if(i+1 < options.data.length) {
                    str += ', ';
                }
            }
            $(this).append(str);
        };
        return this.each(make);
    }
}(jQuery));
```

---

Implementing this would simply require us to pass the params while we call the plugin:

```
$(document).ready(function () {
    $('.selector').updateSelector({
         data: [1,2,3,4,5,6,7,8,9,10]
    });
 });
```

---

## Conclusion
This approach is basically to understand the structure of a plugin and its benefits. An [ResponsiveSlides.js](https://cdn.jsdelivr.net/jquery.responsiveslides/1.54/responsiveslides.jshttps:/) excellent example for a plugin with neat assorted functions to handle different purviews involved while handling multiple scenarios.

As a learning exercise, try to assimilate the approach and implementation of [ResponsiveSlides.js](https://cdn.jsdelivr.net/jquery.responsiveslides/1.54/responsiveslides.jshttps:/) and add a functionality to control the pause/play of the slide externally, once the slider is rendered (probably a dynamically created button on the carousel that allows one to pause or play the carousel).

I believe this is a good start to understand the structure of a plugin. Feel free to connect with me if interested in knowing more about different approaches in building a plugin. You can use the [H-Slider plugin](https://github.com/himadhar/h-sliderhttps:/).

---

<h6 style="text-align: right">
- Himadhar
</h6>