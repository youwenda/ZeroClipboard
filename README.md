ZeroClipboard
==============

The ZeroClipboard library provides an easy way to copy text to the clipboard using an invisible [Adobe Flash](http://en.wikipedia.org/wiki/Adobe_Flash) movie, and a [JavaScript](http://en.wikipedia.org/wiki/JavaScript) interface. The "Zero" signifies that the library is invisible and the user interface is left entirely up to you.

## Simple Example

``` html
<html>
  <body>
    <button id="copy-button" data-clipboard-text="Copy Me!" title="Click to copy me.">Copy to Clipboard</button>
    <script src="ZeroClipboard.js"></script>
    <script src="main.js"></script>
  </body>
</html>
```

``` js
// main.js
ZeroClipboard.setMoviePath("/path/to/ZeroClipboard.swf");
var clip = new ZeroClipboard.Client("#copy-button");

clip.on( 'load', function(client) {
  // alert( "movie is loaded" );
} );

clip.on( 'complete', function(client, args) {
  this.style.display = 'none'; // "this" is the element that was clicked
  alert("Copied text to clipboard: " + args.text );
} );

clip.on( 'mouseover', function(client) {
  // alert("mouse over");
} );

clip.on( 'mouseout', function(client) {
  // alert("mouse out");
} );

clip.on( 'mousedown', function(client) {

  // alert("mouse down");
} );

clip.on( 'mouseup', function(client) {
  // alert("mouse up");
} );
```

See the [instructions](ZeroClipboard/blob/master/docs/instructions.md) for advanced instructions on how to use the library on your site.

Here is a working [test page](http://jonrohan.github.com/ZeroClipboard/#demo) where you can try out ZeroClipboard in your browser.

## Testing ZeroClipboard.swf Locally

To test the page [demo page](http://jonrohan.github.com/ZeroClipboard/#demo) locally. checkout the `gh-pages` branch and run `make`. This should open [localhost:3000](http://localhost:3000/)

```
git co gh-pages
make
```
add `BRANCH=my-dev-branch` to get the assets from a certain branch

```
git co gh-pages
make BRANCH=my-dev-branch
```

## Support

This library is fully compatible with Flash Player 10, which requires that the clipboard copy operation be initiated by a user click event inside the Flash movie. This is achieved by automatically floating the invisible movie on top of a [DOM](http://en.wikipedia.org/wiki/Document_Object_Model) element of your choice. Standard mouse events are even propagated out to your DOM element, so you can still have rollover and mouse down effects.

Works in IE8+. Works in IE7 but requires Sizzle/jQuery. (And of course works in all of the other browsers.)

## Contributing

see [CONTRIBUTING.md](ZeroClipboard/blob/master/CONTRIBUTING.md)

## Releases

see [releases.md](ZeroClipboard/blob/master/docs/releases.md)

## Last Build

[![Build Status](https://secure.travis-ci.org/jonrohan/ZeroClipboard.png?branch=master)](https://travis-ci.org/jonrohan/ZeroClipboard)
