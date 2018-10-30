# A11Y (Accessibility)


https://github.com/fac-15/a11y-research-site


# Accessibility 



## Semantic HTML 
Instead of using ```<div>```s to structure your content, writing an accessible website layout is about wrapping your ```<nav>```, ```<footer>```, ```<article>``` etc., in appropriate sectioning elements. These give users extra clues about what content they contain. 

Other than making your project more accessible, it also has the bonus  of making your life as a devoloper easier, as many of these tags comes with built in functionality, as well as being easier to understand for both readers, developers and search engines (because search engines prioritises keywords inside headings, links, etc., over keywords inside non-semantic ```<div>```s etc.).


## HTML5 Elements and Divs
[link in precourse materials](https://codepen.io/mi-lee/post/an-overview-of-html5-semantics)

## Adding ARIA attributes:

**ARIA roles:**

These can be used to label elements which have no semantic meaning, for example, ```<section>```, ```<article>```, or ```<header>``` elements. Elements such as ```<form>``` or ```<input>``` have semantic meaning, and do not require an ARIA role.

ARIA roles can be applied to an element like so:
```<section role="main content">```

[More info here](https://a11yproject.com/posts/getting-started-aria/)

## Key handlers 
UI controls, such as links, buttons, forms, the <select> tag etc., has the added bonus of by default allowing the user to navigate between them with the keyboard.  

## Using tabindex  

By default, only interactive elements (e.g. form inputs, address bar, links to external webpages) are focusable on a webpage when using the `tab` key. Tabindex can be used to make more elements focusable with the tab key. This may be appropriate for menus, and is likely to require script to work properly. [More on tabindex](https://developer.mozilla.org/en-US/docs/Web/Accessibility/Keyboard-navigable_JavaScript_widgets#Using_tabindex).
[Google Devs page on tabindex](https://developers.google.com/web/fundamentals/accessibility/focus/using-tabindex).


Tools to test for accessibility
------------------------------
Chrome extension: Accessibility Developer Tools
Chrome extension: High Contrast, Increase the contrast or invert the contrast
Markup Validation Service -

Contrast checker - http://juicystudio.com
This gives an AAA highest score for combinations of text at different sizes on coloured backgrounds.

I have a friend with sight accessibility issues. When she turns on high contrast on the screen she finds the program buttons become invisible, when useing library indexing program.


## Accessible Navigation:
- [including options to skip navigation at top of page](https://a11yproject.com/posts/skip-nav-links/)

"where dropdown systems hide structure away, tables of content lay it bare."

Table of content menus is prefereble when a site has a lot of content, and it's also easy to make responsive without having to write much code.

Navigation submenus (or "dropdowns" to some) work well with a mouse or by keyboard, but does not work as well with touch.


## [Web Accessibility Checklist](https://a11yproject.com/checklist)


## [MDN - Common Accessibility Problems](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility)

## Accessible Modals
[Example](https://www.w3.org/TR/wai-aria-practices/examples/dialog-modal/dialog.html)
[Codepen Example](https://codepen.io/matuzo/pen/GrNdvK)
[To do list for accessible modals](https://bitsofco.de/accessible-modal-dialog/)
- Markup the Dialog and Dialog Overlay Appropriately
-- ```role='dialog'```
- On Dialog Open, Set Focus
-- First need to create an array of focusable elements in the modal, before assigning one focus using the ```focus()``` method
- On Dialog Close, Return Focus to the Last Focused Element
-- Just before opening the modal we can save the previously focused element in order to return focus once it is close. Uses```document.activeElement``` and ```focus()```
- While Open, Prevent Mouse Clicks Outside the Dialog
-- Achieved through simple styling - increasing z-index of the overlay (providing it covers the whole page behind the modal)
- While Open, Prevent Tabbing to Outside the Dialog
-- Creating "keyboard trap". 
- Allow the ESC Key to Close the Dialog


## What not to do:

Don't use dashes if you can avoid it. Instead of writing 5–7, write 5 to 7.
      
Expand abbreviations — instead of writing Jan, write January.
      
Expand acronyms, at least once or twice. Instead of writing HTML in the first instance, write Hypertext Markup Language.

Navigation submenus (or "dropdowns" to some) work well with a mouse or by keyboard, but they’re not so hot when it comes to touch.

You certainly shouldn’t equate "small screen" with "touch activated". 


