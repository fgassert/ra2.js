Responsive App v2
---
A lightweight responsive framework for fullscreen web applications.
Built in HTML, CSS3, and javascript.

Supports all modern browsers, IE 9+, iOS. Functions in IE8.

### TODO
 - [ ] Verify IE and Mobile Support
 - [ ] Add build scripts
 - [ ] Add examples

### How it works
The responsive app framework divides the screen realestate into four sections: two responsive panels, headmatter, and main content. See a [demo](http://fgassert.github.io/ra2.js/).

![layout](http://raw.github.com/fgassert/ra2.js/master/fullscreen-app-layout.png)

The framework is designed to be easily modified by inserting HTML into these sections. Rather than creating a layout on the fly, the framework relies on static HTML and CSS for better performance.

ra.js monitors window size and moves the respective panels. The main element is a div called `#ra-container`, which slides to the left and right to reveal the side panels when on small screens.

The `#ra-container` element is assigned a class depending on the screen mode:
```
.ra-large /* for normal window sizes */
.ra-small /* for small window sizes */
.ra-fullscreen /* when in full screen mode */
```

In addition ra.css defines two classes: `.ra-hidewhenlarge` and `.ra-hidewhensmall` for elements that you only want to appear when screen mode is large or small.

Use
===
### Option 1: Edit the html

Clone the master branch. All dependencies are held in the `_site` folder.

**Edit these files:**

`_site/index.html`: Base html. Rather than creating a layout on the fly, the framework relies on static HTML and CSS for better performance [read the source](https://github.com/fgassert/ra2.js/blob/master/_site/index.html) to see where to insert content.

`_site/css/style.css`: Additional styling information, edit this document to change framework appearance

**Core files:**

`_site/css/ra.css`: Core css.

`_site/js/ra.js`: Core javascript

`_site/js/classList.min.js`: [classList shim](https://github.com/eligrey/classList.js/blob/master/classList.js) for older browser support

### Option 2: Jekyll + GitHub Pages

The Responsive App framework is built using [Jekyll](http://jekyllrb.com) which uses the [Liquid](http://liquidmarkup.org) templating engine. 

Fork this repository, switch to the `gh-pages` branch and replace `_includes/main-content.html` with your own content.
Go to http://{username}/github.io/responsive-app/ to see the changes!

`index.html` is the main template for the Responsive app framework.

`_includes/*` holds the html content for the app. Edit these files and `css/style.css`.

GitHub Pages and Jekyll will automatically compile the `gh-pages` repository into a static site located in the `_site` folder. The `index.html` loads up the content in the `_includes` folder. Any non-Jekyll files in the base directory including the `css` and `js` folders will be copied into the `_site` directory. 

ra.js Options, methods, and events
===

Initialize the Responsive App framework using `ra = new ra({options})`.

**Default options:**
```
{
  minWidth:640,        // minimum window width (px) for screen size to count as large, 
                       //  when window width is smaller than minWidth the layout will be condensed
  panelWidthSm:284,    // panel width (px) in small screen layout.
  panelWidthLg:284,    // panel width (px) in large screen layout.
  panel1:true,         // toggle panel on/off
}
```

**Methods:**

The `ra` object supports the following methods
```
ra.resize()              // Forces ra to recalculate panel sizes
ra.screenSize()          // Returns the current mode (#ra-container.className)
                         //  Small: 'ra-small', Large: 'ra-large', Fullscreen, 'ra-fullscreen'
ra.toggleFullScreen()    // Toggles fullscreen mode. 
                         //  In fullscreen mode the main content fills the entire window
ra.togglePane		 // Toggles the panel on or off
ra.toggleNav		 // Toggles the nav dropdown on or off on in small screen mode
ra.setOptions({options}) // Edits the ra options and recalculates panel appearance
ra.getOptions()          // Returns the current configuration
ra.getCurrentPanel()	 // Returns id of curren panel
```

**Events:**

ra.js will dispatch custom events on the `#ra-container` element
```
'ra-screenchange'	// occurs when screen mode changes
'ra-panelchange'	// occurs when panel changes
```


