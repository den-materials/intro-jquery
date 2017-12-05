<!---
title: Intro To jQuery
type: lesson
duration: "1:25"
creator:
    name: Gerry Mathe, Elie Schoppik
    city: London, San Francisco
competencies: Front-end intro
--->

<!--9:55 WDI6 -->
<!--10:00 WDI4 -->
<!--Actually 10:00 -->
<!--WDI5 9:48 -->
<!--9:45 5 minutes -->

<!-- Hook: Raise your hand if you thought the LOTR DOM manipulation lab was easy.  A lot of other people think the same way as you.  That is why people started creating tools to make this job easier.  And that is exactly what jQuery does. -->

# Intro To jQuery

### Objectives
*After this lesson, students will be able to:*

- **Describe** jQuery and the context to use it in
- **Include** jQuery in your projects
- **Practice** using jQuery selectors


### Preparation
*Before this lesson, students should already be able to:*

- **Use** vanilla JavaScript to manipulate the DOM
- **Use** a text editor
- **Explain** CSS selectors

## jQuery - Intro

#### What is jQuery?
jQuery is a 3rd-party library that is intended to make front-end development tasks — particularly those involving DOM selection and manipulation — easier, faster, and more fun.

##### But wait, what do we mean by 'library'?

**A `library`** is just a collection of reusable methods that serve a particular purpose.


#### So, as a library, what does jQuery offer us?

jQuery helps us manipulate the DOM, allowing us to perform complex manipulations using less code with less hassle.  jQuery's syntax was developed to mimic CSS selector syntax, making code easier to develop, read, and manage; also, the syntax is more concise, and jQuery solves many cross-browser compatibility issues for us.

<!--WDI5 9:53 -->
<!--9:50 5 minutes -->
<!--10:07 WDI4 -->

## Using jQuery - Demo

#### Installation
jQuery is a client side library, which means we need to include it in our HTML. To do this, we have two options:

1. Reference jQuery from a server on the internet:

 - Directly from jQuery's website (http://code.jquery.com/)
	`<script
  src="https://code.jquery.com/jquery-3.2.1.min.js"
  integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4="
  crossorigin="anonymous"></script>`

 - From a CDN (content delivery network) like [CDNJS](https://cdnjs.com/) or [Google Hosted Libraries](https://developers.google.com/speed/libraries/)
	`<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>`

2. Download a copy of jQuery to host on your own server:

- [CDNJS](http://www.cdnjs.com), [Google Hosted Libraries](https://developers.google.com/speed/libraries/), and the [jQuery site](http://www.jquery.com) will all allow you to download a copy of jQuery to include in your projects.

#### What's with the 'min.js' in the name of the jQuery file?

If you look carefully at the filenames of the jQuery versions you download, or just look at the URL in the "src" attribute for each script tag above, you'll notice something at the end of each file name — namely, that they end in 'min.js'. This means the JavaScript code has been minified.

#### What's with the `integrity` and `crossorigin` attributes?

The `integrity` and `crossorigin` attributes are used for Subresource Integrity (SRI) checking. This allows browsers to ensure that resources hosted on third-party servers have not been tampered with. Use of SRI is recommended as a best-practice, whenever libraries are loaded from a third-party source. Read more at [srihash.org](srihash.org).

<!-- Catch-up add jQuery to an index.html file in a folder called `first_jquery` -->

<!--9:55 10 minutes -->

## Minified? Did I read that right? Discussion

Yep. You did. Minification is the process of making a JavaScript file smaller by, among other things, removing all line breaks and whitespace, reducing the length of variable and function names, and stripping out all comments. Minification can significantly reduce the size of a JavaScript file, and in turn, significantly decrease the time it takes our browsers to load the file into memory.

In jQuery's 3.2.1's case, the original unminified code is about 268 kilobytes, whereas the minified code is only 87 kilobytes. That makes the minified version **one-third** the size of the original - not bad!

Minified scripts can be difficult to read, so most servers that host jQuery and other libraries will also offer the original (non-minified) version of the code so developers can understand the code.

Minification is performed on JavaScript when it's ready for release and there are many options for doing this. If you'd like to minify your own scripts, try a Google search to check out the various options. Or, you can try the [Closure Compiler from Google](https://developers.google.com/closure/compiler/) which runs locally on your computer like any other piece of software you might use as a developer.

Also, if you do happen to come across a library where you can't find a non-minified version to look at, software also exists to decompress a minified script. These are usually called unminifiers, pretty-printers, or beautifiers). They take a minified JavaScript and attempt to decompress it, making it easier to read and understand.

<!-- Make sure you show both minified and non-minified versions here -->

**Even if you don't fully understand the code, it's a good exercise to visit code.jquery.com and take a look at minified and non-minified jQuery.**

#### And one more thing: 2.x vs. 3.x jQuery

If you've visited code.jquery.com, you'll see that there are two major versions in development:
  - The 2.x branch is the most cross-browser-compatible version of the jQuery core
  - The 3.x branch offers some new features. Some of these are continuing the additions that came with ES6, and others make coding with jQuery even easier. For a full list of new features, you can check out [this link](http://developer.telerik.com/featured/whats-new-in-jquery-3/).

<!--WDI5 10:09 -->
<!--10:19 WDI4 -->
<!--WDI6 10:12 -->
<!--10:05 >10 minutes -->

<!--Do all code out in Sublime with input from devs.  Devs at half-mast the whole time -->

## DOM manipulation with jQuery - Intro

Before we get into jQuery, let's just think about how we would perform the following tasks:
  - `select` a DIV and change its content
  - `append` a new DIV with some content to a web page
  - `listen` for events on a collection of DIVs or other HTML elements
    + For example, a blog site might have a "like" button for each comment on a post.

<!-- Have devs think about how they would do this for plain Javascript for a minute -->

#### First, let's just talk about selecting an element with jQuery

To select an element in the DOM, we use the global jQuery function:

```JavaScript
// This is the basic syntax for jQuery selections
$(' ')

// To select a particular element by tag, you do
$('h2') // selects all h2 elements

// To select by ID, you use the same syntax as CSS selectors
$('#someID') // Would select the element with ID="someID"

// To select all elements of a particular class, use CSS syntax again
$('.someClass') // Selects all elements of the class "someClass"

// And you can use more complicated CSS selectors as well
$('p.anotherClass') // Selects all <p> tags that also have the class "anotherClass" (<p class="anotherClass")
```

If you use variable assignment when doing a selection, a "jQuery" object is returned

```JavaScript

// We prepend '$' to variable names when a variable is going to be a jQuery object to help us remember what that variable is for.
var $jqObject = $('p'); // Returns a jQuery object containing all <p> tags on your web page.
```

<!--Catch up on this one (no vanilla JS, just jQuery) -->
#### Selecting a DOM element and changing its content

In this HTML:


```html
<div id="myDiv">Hello world!</div>
```

```JavaScript
var divToManipulate = document.getElementById('myDiv');
divToManipulate.innerHTML = "Goodbye world!";
```

Now the code above isn't too hard to deal with, but even so, in jQuery, this is a one-liner.

```javascript
$('#myDiv').html("Goodbye world!");
```

See it in action [here](http://jsbin.com/rirumatozu/4/edit?html,js,output)

If we wanted to **save our selection as a jQuery object**, the code would look like this instead:

- First we select the element we want and save it as a jQuery object

```javascript
var $myDiv = $('#myDiv');
```

- Then we use our jQuery object to perform our task

```javascript
$myDiv.html("Goodbye world!");
```

There are three things about the example above that make jQuery easier to use:
  1. jQuery is using the same syntax as CSS to select elements
  2. jQuery allows us to chain methods together to accomplish our goals (i.e., $().html(...) ), making code shorter and easier to understand
  3. jQuery deals with any cross-browser compatibility issues, which may not seem like a big deal in this example, but which quickly become difficult to deal with as things get more complex

<!--WDI5 10:25 -->
<!--Actually 10:22 -->
<!--10:28 WDI4 -->
<!--10:15 >10 minutes -->

<!--Just show this one, no catch-up -->
#### Appending a DOM element to a web page

If we had the following HTML page...

```html
<html>
<body>

  <div id="container"></div>

</body>
</html>
```

If we want to add a new DIV that provides a nice greeting, our vanilla JavaScript would have to be:

```javascript
  var myDiv = document.getElementById('container');
  var newP = document.createElement('p');
  newP.innerHTML = "Hello complicated, multi-step world of adding an element to the DOM!";
  myDiv.appendChild(newP);
```

And in jQuery, it looks like this:

```javascript
  $('#container').append("<p>").append("Hello simple insertion using jQuery chaining");
```

In the jQuery code example above, we first select the DIV with `id="container"`, then we append a new paragraph element (automatically created using core jQuery selector function), and then we append the text we want to insert to the new paragraph element we just created. In effect, the new HTML looks like this after the jQuery is run:

```html
  <div id="container">
    <p>
      Hello simple insertion using jQuery chaining
    </p>
  </div>
```

You can [see this in action on JSBin](http://jsbin.com/rocabu/1/edit?html,js,output)


#### Modifying Styles (CSS) Using jQuery

You can do more than select elements and modify content. You can also create or update CSS style attributes in jQuery using the .css() method

```js
$("#myDiv").css("color", "red");
```

The code above will change the color of all text inside the DIV with id="myDiv" to red.

[Check this out here](http://jsbin.com/cupumu/1/edit?html,js,output)

Or, if we have a bunch of elements that all have the same class (in this example, it's class="myClass"), we can use the class selector to modify the color of all of them at once:

```js
$(".myClass").css("color", "blue");
```

[You'll find this example here](http://jsbin.com/yutoyi/1/edit?html,js,output)

<!--WDI5 10:33 -->
<!--WDI6 10:41 -->

But that seems kind of boring. I mean, what if we want to do something with less hard-coding using jQuery.

[Here's a repeat of the last example](http://jsbin.com/wevoti/1/edit?html,js,output) that sets the text in all elements of class="myClass" to a random color. Try to understand how it works before moving on:

```javascript
var randColorValue = function() {
  return Math.floor( Math.random() * 255 );
}

var randColor = function() {
  var red = randColorValue();
  var green = randColorValue();
  var blue = randColorValue();

  return "rgb(" + red + "," + green + "," + blue + ")";

}

$(".myClass").css("color", randColor() );
```

<!--10:35 WDI5 -->
<!--10:31 -->
<!--10:30 <10 minutes -->

#### Adding and Removing Elements Using jQuery

Sometimes in a dynamic web application, user-input is meant to trigger the addition or removal of content or functionality. Using jQuery, we can easily create new DOM elements and insert them into the DOM, or remove existing elements (and any content they contain) from the DOM.

So, let's imagine we have a web page with the following content on it:

```html
<body>
  <div id="outerContainer">
    <div class="innerItem innerItemHeader">Enjoy some hipster ipsum:</div>
    <div class="innerItem">
      Aesthetic migas paleo McSweeney's, pork belly Kickstarter Echo Park sriracha keytar disrupt viral drinking vinegar fanny pack typewriter.
    </div>
  </div>
</body>
```

Let's say we want to add some more hipster ipsum to the page. Something like:

```html
<div class="innerItem">
	Farm-to-table Godard roof party bespoke, fashion axe mustache vinyl.
</div>
```

To add this DIV, and our hipster ipsum content using jQuery, we'd do the following:

Define a new DIV and assign jQuery object to $newDiv

```javascript
$newDiv = $('<div>');

// Add hipster ipsum content
$newDiv.html("Farm-to-table Godard roof party bespoke, fashion axe mustache vinyl.");

// Set its class to innerItem
$newDiv.addClass("innerItem");

// Append our new element  
$('#outerContainer').append($newDiv);
```

See this in action (and play around with it) [on JSBin](http://jsbin.com/gupade/3/edit?html,js,output)

Now, let's get rid of all the hipster ipsum we just made:

```javascript
$('#outerContainer').remove();
```

<!--WDI6 10:49 -->
<!--WDI5 10:42 -->
<!--Actually 10:38 -->
<!--10:39 WDI4 -->
<!--10:40 15 minutes -->

## Reddit - Independent Practice

Follow the directions below to practice using jQuery:

- Go to http://www.reddit.com

- Reddit uses jQuery, so we can use our Chrome developer console to manipulate the site in real time using jQuery.

- To do this, once Reddit.com has loaded, open the Console tab of Chrome Developer Tools

- Once that's loaded, try entering the following command into the Console:

```javascript
$('img').hide()
```

- Hit enter. All the images should have disappeared from the Reddit.com home page. Make sure you understand why before moving on.

- Now try this:
```js
$('img').show()
```

- That should have brought all the images back. Make sense so far?

- Now use the Chrome `Inspect`or, and try to match the title of the first Reddit post and replace the text using `.text()` or `.html()`.

- Try to replace the blue background in the header by another color using the function `.css()`.

- Now try some of the other examples we went over earlier in this lesson in the Chrome Console, and see what happens to the Reddit.com website. Remember, this is your laboratory — your chance to experiment and learn. Make use of it.

<!--WDI6 11:03, 11:06 done -->

## Conclusion

- jQuery makes JavaScript super friendly and easy to write. A lot of websites are using jQuery, soon you will too.  Remember that it's always good to know how to use what is called vanilla JavaScript, or JavaScript without a library.

- Please spend some time reviewing [the documentation](https://api.jquery.com/).

## Resources

- [What's New in jQuery 3](http://developer.telerik.com/featured/whats-new-in-jquery-3/)
