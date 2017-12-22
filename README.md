taggers
================


A library that enables tag shortcuts for the Composi `h` function. Less than 50 lines of code, taking your hyperscripting to the next level.

What It Does
------------

```javascript
// Instead of writing,
h('div')

// write:
div()

// Instead of writing,
h('section' {id: 'main'}, mainContents)

// write:
section({id: 'main'}, mainContents)
```

Taggers vs JSX
--------------

With `taggers`:

* You get errors if you misspell a tag name, because they are function names.
* You have a consistent syntax at all times, because it's just functions.

Supported Tags
--------------

```javascript
'a', 'abbr', 'acronym', 'address', 'applet', 'area', 'article', 'aside',
  'audio', 'b', 'base', 'basefont', 'bdi', 'bdo', 'bgsound', 'big', 'blink',
  'blockquote', 'body', 'br', 'button', 'canvas', 'caption', 'center', 'cite',
  'code', 'col', 'colgroup', 'command', 'content', 'data', 'datalist', 'dd',
  'del', 'details', 'dfn', 'dialog', 'dir', 'div', 'dl', 'dt', 'element', 'em',
  'embed', 'fieldset', 'figcaption', 'figure', 'font', 'footer', 'form',
  'frame', 'frameset', 'h1', 'h2', 'h3', 'h4', 'h5', 'h6', 'head', 'header',
  'hgroup', 'hr', 'html', 'i', 'iframe', 'image', 'img', 'input', 'ins',
  'isindex', 'kbd', 'keygen', 'label', 'legend', 'li', 'link', 'listing',
  'main', 'map', 'mark', 'marquee', 'math', 'menu', 'menuitem', 'meta',
  'meter', 'multicol', 'nav', 'nextid', 'nobr', 'noembed', 'noframes',
  'noscript', 'object', 'ol', 'optgroup', 'option', 'output', 'p', 'param',
  'picture', 'plaintext', 'pre', 'progress', 'q', 'rb', 'rbc', 'rp', 'rt',
  'rtc', 'ruby', 's', 'samp', 'script', 'section', 'select', 'shadow', 'slot',
  'small', 'source', 'spacer', 'span', 'strike', 'strong', 'style', 'sub',
  'summary', 'sup', 'svg', 'table', 'tbody', 'td', 'template', 'textarea',
  'tfoot', 'th', 'thead', 'time', 'title', 'tr', 'track', 'tt', 'u', 'ul',
  'var', 'video', 'wbr', 'xmp'
```

Installation
------------

```
npm install taggers
```

First import `taggers`. It's a default export so you can name the import whatever works for you. Here we'll call it `hyperscript`.
You need to pass the Composi `h` function to the imported `taggers` function. That's so that `taggers` will use `h` when it creates the virtual nodes:

Using ES6:
```javascript
import {h} from 'composi'
import {taggers} from 'taggers'
// Pass 'h' to taggers:
const {h1, nav, header} = taggers(h)

// Use the tags you've imported:
const Header = header({},
  nav({},
    h1({title: 'The Great Title'},'The Title')
  )
)
// <header><nav><h1 title='The Great Title'>The Title</h1></nav></header>
```

Parameters
----------

From the above example, it should be noted that tags expect two arguments: props and children. If the tag will have no props, you can pass an empty object or `null`:

```javascript
import {h} from 'composi'
import {taggers} from 'taggers'
const {div} = taggers(h)

// Use the 'div' function:
const element = div({}, 'Some content')
// <div>Some content</div>

// or:
const element = div(null, 'Some content')
// <div>Some content</div>
```

You can create a tag with properties but no children by providing only the first argument:

```javascript
import {h} from 'composi'
import {taggers} from 'taggers'
const {div} = taggers(h)

const element = div({id: 'whatever'})
// <div id='whatever'></div>
```

If you want to create an empty tag, just call the tag function without paramters:

```javascript
import {h} from 'composi'
import {taggers} from 'taggers'
const {div} = taggers(h)

const element = div()
// <div></div>
```