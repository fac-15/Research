---
slideOptions:
  transition: slide
---
:computer:
# Templating and Serverside rendering
:computer: 

---

<i> What is server-side rendering? </i>
![](https://media.giphy.com/media/3o6Zti8Yz88sqW1nq0/giphy.gif)

---

<i>Server-side rendering (SSR) </i>is the conventional method of serving your files to a browser. 

![](https://media.giphy.com/media/l0HlU54bbdSbJuI3m/giphy.gif)

Note: Now that we want our webpages to act more like applications where you can send messages, update information, shop, etc, <i>client side rendering</i> is becoming more popular.

---

![](https://i.imgur.com/TZajVVD.png)

With SSR, you load your files on to your server and then your server serves those files to the browser when you visit a webpage. Any interactivity happens in a separate request.

---

Request speed depends on:
![](https://media.giphy.com/media/QTvYcj77RjkQ/giphy.gif)

1. internet speed
2. the location of the server
3. how many users are trying to access the site
4. how optimized the webpage is

---

Once the request is finished being processed, the browser gets back the rendered HTML and displays it.

Every time you visit a different page on the website, your browser makes another request for information.

Note: This is not a problem for a simple webpage, but for websites with many pages, it will be very slow to load.

---

## <i> What are the pros and cons of serverside rendering vs clientside </i> 
![](https://i.imgur.com/ciM1rAY.png)

---

## <i> What are Templating Languages such as handlebar?</i> 

![](https://media.giphy.com/media/Js5iT9z6CKnC0/giphy.gif)<!-- .element: class="fragment" data-fragment-index="1" -->

---

>... they allow the programmer to create a replicatable **'template'**.That can be used in **multiple instances** with **different fields** to fill in

![](https://media.giphy.com/media/E7BTTLP53k772/giphy.gif)<!-- .element: class="fragment" data-fragment-index="1" -->

---

## <i> What problems do templating languages solve?</i>

<span>:art: Increases brainspace => creativity</span><!-- .element: class="fragment" data-fragment-index="1" -->
<span>:sweat_drops: Encourages 'dry'(er) codeing</span><!-- .element: class="fragment" data-fragment-index="2" -->
<span>:revolving_hearts: Enables easy-to-make re-usable code</span><!-- .element: class="fragment" data-fragment-index="3" -->
<span>:lock: Handlebars {{}} notation is more secure</span><!-- .element: class="fragment" data-fragment-index="4" -->

Note:
Increases **creativity** because it makes everything easier thus reducing strain and making more space for creativity .
Encourages **dry code** because things like 'partials' in handlebars mean that code is easily reusable.
This code is **easily-to-make** because it does not need to be re-factored or formatted in anyway to be modularised other than. 
Handlbars double bracket notation has an automatic escape inbuilt for special case characters (such as &,#,$). This can help protect against cross-site-scrypting. It is more appropriate to filter it here because 


---

### Pros and Cons
![](https://i.imgur.com/dmug6Hn.png)

---



## <i> What are some examples of functionality that templating languages provide e.g. conditional logic etc. </i>

---

A template engine enables you to use static template files in your application. At runtime, the template engine replaces variables in a template file with actual values, and transforms the template into an HTML file sent to the client. This approach makes it easier to design an HTML page.

---

- ```Looping``` - script language power to do loops (for/for each, while) or recursion
**Mustache Templating**
```javascript=
You can Mustache use loops in your templates. Taking this template:

{{#people}}
    {{name}}
{{/people}}

With this data passed in:

{ people: [ { name: "Jack" }, { name: "Fred" } ] }

You'll get the string "JackFred" returned.

```

---


Alternative templating language example:

**JADE Templating**
```javascript=
We can also do loops in Jade too:

each person in people
li=person

Called with an array of names: '{ people: [ "Jack", "Fred" ]}', 

This will output:

<li>Jack</li><li>Fred</li>
```

---


- ```Assignment``` - set names and references to sub-templates
- ```Includes``` - include external files
- ```Condition Inclusions``` - script language power to conditional includes
- ```Variables``` - script language power to use variables
- ```Natural templates``` - the template can be a document as valid as the final result, the engine syntax doesn't break the document's structure

---

- ```Inheritance``` - Supports the ability to inherit a layout from a parent template, separately overriding arbitrary sections of the parent template's content.
- ```Function``` - script language power to use functions
- ```Languages``` - implementation language of the engine (not the template script language)


---

# Le End

![](https://media.giphy.com/media/xT5LMEYx5AZwu4oiac/giphy.gif)


