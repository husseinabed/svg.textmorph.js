# svg.pathmorphing.js

A plugin for the [svgjs](https://github.com/wout/svg.js) library to enable text morphing / animation

In order to morph text, we have to convert the text to paths.

So at first we need an svg-font.

You can load this font like so:

```javascript

new SVG.SVGFont(font, callback, lazyloading)

```

 - `font` can be an xml string containing a font element, an id pointing to an element containing a font element or can be a path to a file.

 - The `callback` is called when the font is loaded (which is neccessary when the file asynchronously loaded).

 - `lazyloading` specifies if the glyphs should only be pulled from the font if needed or cached all together when loading the font.
   This parameter is true per default which means lazyloading is active.

Example:

```javascript

new SVG.SVGFont('myFont.svg', function(){
  // callback is called in context of the font

  // lets use the font
  var text = draw.morphText('ABCDEFG').font({
    family:this, // or this.family or just the font-family which is specified in the font
    size:50
  })
  
  // animate the text
  text.animate().text('GFEDCBA')

})

```

## Dependencies
This module requires svg.js >= v2.1.1