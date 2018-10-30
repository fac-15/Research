# CSS Team Research

## Responsive vs. Mobile-First Design
Responsive Design:
- when content is designed to shrink or expand based on the viewport width
- can also be described as 'Desktop-first' design
- uses only HTML & CSS

Mobile-first Design:

- When content is designed for a mobile and then scaled up to fit a computer-sized viewport

### Max-width vs Min-width

#### _Responsive approach_
``` max-width ```

A Desktop-first approach to styling means that styles are applied first to desktop devices.
Advanced styles and overrides for smaller screens are then added into the stylesheet via media queries.

#### _Mobile-First approach_

``` min-width ```

A mobile-first approach to styling means that styles are applied first to mobile devices.
Advanced styles and other overrides for larger screens are then added into the stylesheet via media queries.

### Mobile Optimization Top Tips
#### 1. Setting the Viewport Width
HTML5 introduced a method to let web designers take control over the viewport, through the <meta> tag.

You should include the following <meta> viewport element in all your web pages:
```<meta name="viewport" content="width=device-width, initial-scale=1.0">```

A <meta> viewport element gives the browser instructions on how to control the page's dimensions and scaling.

The width=device-width part sets the width of the page to follow the screen-width of the device (which will vary depending on the device).

The initial-scale=1.0 part sets the initial zoom level when the page is first loaded by the browser.

#### 2. Don’t Always Focus on the Mobile Consumer
As mobile and desktop merge, so too are the goals and desires of the users of these platforms.

#### 3. Make Sure All Content Is the Same on Desktop & Mobile

The idea behind this best practice is to avoid duplicate content and accusations of cloaking.

To be safe, always make sure that all content is the same on the desktop version of your site as it is on mobile.

#### 4. Use a ‘From the Top Down’ Development Approach

A “from the top down” development approach means that you consider all potential consequences of each decision made in a design from start to finish.

You develop for mobile-first, rather than desktop-first, and then tacking on a mobile design after. This development approach is ideal because you don’t introduce issues into the final design.

### Examples of Media Queries in action
[Media Queries in Action](https://mediaqueri.es/)







# How to write CSS with BEM

## BEM - Naming conventions

BEM attempts to divide the overall user interface into small reusable components.

##### BEM component classes in three groups:
><span style="color:green">Block: The sole root of the component.</span>
><span style="color:blue">Element: A component part of the Block.</span>
><span style="color:red">Modifier: A variant or extension of the Block or Element.</span>

![](https://i.imgur.com/C17RBOc.jpg)

#### Block:
* A standalone, reusable group of items . You could think of it as of component in frontend frameworks.
* For example, a ‘card’ would make a good block.
><span style="color:green">Block:</span> `class="card"`
#### Element:
* A part of a block that has no standalone meaning and is semantically tied to its block. Within a given block, all elements are semantically equal.
* Element names **must** be written and seperated from the component name by **two underscores**
><span style="color:green">Block:</span> `class="card"`
><span style="color:blue">Elements:</span> `class="card__title"`, `class="card__text"`, `class="card__image"`
#### Modifier:
 * A component modifier is a class that modifies the presentation of the base component in some form.
 * Modifier names **must** be written and be separated from the component name by **two hyphens**.
     * "block__element--modifier-value"
><span style="color:green">Block:</span> `class="card"`
><span style="color:blue">Elements:</span> `class="card__title"`, `class="card__text"`, `class="card__image"`
><span style="color:red">Modifiers:</span> `class="card__text--of-image"`
###### card
![](https://i.imgur.com/RjtvFFH.png =200x)

### General CSS styling rules:

- Use class name selectors **only**
- **No** tag names or ids
- **No** dependency on other blocks/elements on page
- Write selectors for **reusability**
- **Reduce** repeated code
- **Do not** nest selectors unnecessarily
- Keep selectors as short as possible
- Keep specificity down

### Maintainability
Specificity, portability, and reusability all have a direct impact on the mileage we will get out of our CSS.
- Most important when:
    * working with teams
    * working on long-term projects with legacy code
#### Reusability
* The idea of **reusability** is paramount. Composing independent blocks _(components)_ and reusing them intelligently, reduces the amount of CSS code that you will have to maintain.
* With a set of _style guidelines_ in place, you and your team can build a library of blocks, making your CSS super effective.
#### Structure
* BEM gives your CSS code a solid structure that remains simple and easy to understand.
#### Modularity
* Block styles are _never_ dependent on other elements on a page, so you will never experience problems from cascading style.
* You also gain the ability to **transfer** blocks _(components)_ from your finished projects to new ones.
#### Javascript
* As a rule, it is unwise to bind your CSS and your JS onto the same class in your HTML.
* This is because doing so means you can’t have (or remove) one without (removing) the other.
* It is much cleaner, much more transparent, and much more maintainable to bind your JS onto its own specific classes.
`<div class="card js-card">`


## Overall...
The implementation is largely personal preference, but the concept still remains: Add any **useful** or **specific meaning** via a mechanism that will allow you and your team to create **reusable** and **maintainable** code.

![](https://i.imgur.com/7DBi8bD.gif)
# ...DOESN'T HAVE TO FEEL LIKE THIS!
