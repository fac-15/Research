<a name="introduction"></a>
# FAC-15 Tips & Tricks

<a name="goal"></a>
## Goal

Keep track of all the useful lessons, tips, and tricks we come across during `FAC-15`.

<a name="method"></a>
## Method
Each tip should indlude a short description and *How To*. We'll also do our best to include the live version and repo of the project, and a link for further reading.

<a name="contributing"></a>
## Contributing
This file is a work in progress, aimed to allow everyone to contribute. Please feel free to edit it to make things clearer.

# Table of Contents

- [Introduction](#introduction)
	- [Goal](#goal)
	- [Method](#method)
	- [Contributing](#contributing)

- [Week 1](#week-1)
	* [Team Awesome](#team-awesome)
        - [Smooth Scrolling](#smooth-scrolling)
        - [Icons](#icons)
        - [Vertical Navbar](#vertical-navbar)
        - [Grid in Mobile Display](#mobile-grid)
    * [Team KA\$H](#team-kash)
        - [Adding a favicon](#favicon)
        - [Using gimp for designing a logo](#gimp)
        - [Automatic form validation](#auto-form-validation)
        - [Including invisible text for screen readers](#invisible-text-screen-readers)
    * [Team CCSM](#team-ccsm)
        - [Hamburger menu](#hamburder-menu)
        - [Adding alert messages as form validation](#validation-alert-messages)
    * [Team CC](#team-cc)
        - [input field’s pattern attribute](#input-pattern-attribute)
        - [aria-labelledby](#aria-labelledby)
        - [Grid](#grid)
        - [Linking each team member image to it’s own team bio](#linking-team-member-to-bio)


<a name="team-awesome"></a>
## Team Awesome 

<a href="https://fac-15.github.io/team-1-portfolio"><img src="https://i.imgur.com/CE7ywYP.png" alt="Team Awesome's portfolio" width=40%></a>

[Project link](https://fac-15.github.io/team-1-portfolio/) | [Github repo](https://github.com/fac-15/team-1-portfolio)


<a name="smooth-scrolling"></a>
### Smooth Scrolling

- We found a quick and simple way to add smooth scrolling to the entire html page with no JS code. To apply it to your project, add this next block of code to your `css` file:

    ```
    html {
      scroll-behavior: smooth;
    }
    ```

- :warning: This does not support all browsers/ all browser versions: It currently doesn't work on *Safari* & *Explorer*. Also doesn't work on *Chrome* versions older than `61.0` nor on *Firefox* versions older than `36.0`.

- :book: Resource: [w3schools](https://www.w3schools.com/howto/howto_css_smooth_scroll.asp)

<a name="icons"></a>
### Icons 

- We used [Font Awesome](https://fontawesome.com) to add icons and logo to our portfolio. The way to do this is to first Include the font awesome library in your `index.html` > `head` tag: 
    ```
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.4.2/css/all.css" integrity="sha384-/rXc/GQVaYpyDdyxK+ecHPVYJSN9bmVFBvjA/9eOB+pb3F2w2N6fc5qB9Ew5yIns" crossorigin="anonymous">
    ```
    Then, use a `span` tag to add icons, like so: 
    ```
    <span class="fas fa-pencil-alt fa-3x colorcss" ></span>
    ```
    The code above adds a pencil shaped icon to the page. The `fa-3x` sets the icon size. We chose to make it three times bigger than its original size. We also added our own project class name `colorcss`, that adds a specific color to the icon.

- :book: Resource: [Font Awesome: Getting Started](https://fontawesome.com/how-to-use/on-the-web/setup/getting-started?using=web-fonts-with-css)

<a name="vertical-mobile-navbar"></a>
### Vertical mobile navbar

<a name="mobile-grid"></a>
### Media queries & grid-template-rows










<a name="team-kash"></a>
## KASH

<a href="https://fac-15.github.io/kash-portfolio/"><img src="https://i.imgur.com/PaeNgDw.png" alt="Team Ka$h's portfolio" width=40%></a>

[Portfolio URL](https://fac-15.github.io/kash-portfolio/) | [Github repo](https://github.com/fac-15/kash-portfolio)

<a name="favicon"></a>
### Adding a Favicon
    
<a name="gimp"></a>
### Using gimp for designing a logo

<a name="auto-form-validation"></a>
### Automatic form validation
In the html, write "<input type="email">" for the email box. Add "<input type=text">" for the names, and "<input type="submit">" for the submit button. More on this here: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/email

<a name="invisible-text-screen-readers"></a>
### Including invisible text for screen readers







<a name="ccsm"></a>
## CCSM 

<a href="https://fac-15.github.io/CCSM/"><img src="https://i.imgur.com/DDVIn9c.png" alt="Team CCSM's portfolio" width=40%></a>

[Portfolio link](https://fac-15.github.io/CCSM/) | [Github repo](https://github.com/fac-15/CCSM)

<a name="hamburger-menu"></a>
### Hamburger menu

We nicked code from an article for this, and altered it to fit our purpose. Will see if Mike can get the link...

<a name="validation-alert-messages"></a>
### Adding alert messages as form validation

We used regex rules, and added an eventListener on the submit button, resulting in a relevant alert message if certain criteria wasn't met (i.e no name inputted, or an invalid email address).

I (Charlie) personally think that other groups' use of the type attribute in the HTML input tag is an easier and nicer way to achieve this! Likewise for the pattern attribute instead of writing out regex rules in the JS file.

Useful resource for testing regex - https://regex101.com/ . Thanks Hannah





<a name="cc"></a>
## CC

<a href="https://fac-15.github.io/CC/"><img src="https://i.imgur.com/QWiFfyP.png" alt="Team CCSM's portfolio" width=40%></a>

[Portfolio link](https://fac-15.github.io/CC/) | [Github repo](https://github.com/fac-15/CC)

<a name="input-pattern-attribute"></a>
### `input` field's `pattern` attribute

<a name="aria-labelledby"></a>
### `aria-labelledby`

<a name="grid"></a>
### Grid

<a name="linking-team-member-to-bio"></a>
### Linking each team member image to it's own team bio


## Other useful tricks 

### Shortcuts 

To create a html skeleton on vs code, type ! and press the tab key.
