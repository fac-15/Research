DOM manipulation


## Description

### **Document Object Model**

The Document Object Model (DOM) is an application programming interface (API) for HTML and XML documents. It represents the page so programmers can build documents, navigate their structure, and add, modify, or delete elements and content.

Anything found in an HTML or XML document can be accessed, changed, deleted, or added using the Document Object Model


<span style="color:orange">DOM Tree

![](https://i.imgur.com/BW7Tf7V.png)



**The DOM is made up of Nodes and Objects:**

The name "Document Object Model" was chosen because it is an "object model" in the traditional object oriented design sense. In other words, the nodes do not represent a data structure, they represent objects, which have functions and identity.

Element object represents an HTML element, like P, DIV, A, TABLE, or any other HTML element.

A node can be any type that is an attribute node, a text node or any other node.






## How can you use JavaScript to create an HTML element and then add it to your webpage? How would you replace an existing element with it?

Creating a new html element:

    document.createElement("_element_tag_name_")

Adding it as a child to an element which already exists.

    document._parent_element_.appendChild("_name_of_child_")

In this case it will always appear as the last child to this node.


There is also a way to create a new element and replace an existing node all at once.

Following are the two methods to replace nodes.

>replaceChild( )
>replaceData( )

**replaceData( )**
This method replaces data in a text node.

**replaceChild( )**
The method replaceChild() replaces the specified node with the new node.



Code:

<span style="color:orange">This is required to make sure the elements we are creating and removing are seen each time we refresh the page.  It is here you would consider when you want the events to happen. (e.g. "onclick").</span>

    document.body.onload = addElement;
<span style="color:blue">- To add to the DOM tree, at the end</span>
<span style="color:purple">- Create the element and add to the target element (in this case the body)</span>

     function addElement () {

     var el = document.createElement("div");
     document.body.appendChild(el); 
     


<span style="color:blue">- This will place the element in a specific node on the DOM tree</span>
<span style="color:purple">- Reference the element you are using to place the new element</span>
<span style="color:purple">- Point to the new element you want to up in and in this case insertBefore that element</span>
      
      var currentP = document.querySelector(".introduction");
      document.body.insertBefore(el, currentP);

<span style="color:blue">- Remove and create to **replace** </span>
<span style="color:purple">- Choose the element you wish to replace</span>
<span style="color:purple">- Create the new element</span>


      var currentDiv = document.querySelector("div");
      var newElem = document.createElement('span')
      
<span style="color:blue">-  Get the parent node of the old element which will be replaced</span>
<span style="color:purple">- Specify the new element you wish to insert and the element it will replace.</span>

      currentDiv.parentNode.replaceChild(newElem, currentDiv)

    }



## How would you add a \<li> element to the start of a \<ul>?

To add a new list item to a `<ul>` is as simple as shown above, adding a new list item to the beginning requires touching the firstChild. see code...

<span style="color:orange">- Append `<li>` item to `<ul>`</span>
  
<span style="color:blue">- Create new list item</span>

      var listItem = document.createElement("li"); 
      
<span style="color:blue">- Dummy text & append to list item</span>
   
      
      var newContent = document.createTextNode("first new item"); 
      listItem.appendChild(newContent); 
      
<span style="color:blue">- Query UL tag</span>

      var listLabel = document.querySelector("ul");          
  
  <span style="color:blue">- Insert new list item first within listLabel (ul tag)</span>
    
      listLabel.insertBefore(listItem, listLabel.firstChild);

<span style="color:blue">- Add a second list element above **new** firstChild of element</span>

      var listItem2 = document.createElement("li");
      var newContent2 = document.createTextNode("addtional new item")
      listItem2.appendChild(newContent2);

      listLabel.insertBefore(listItem2, listLabel.firstChild);

![](https://i.imgur.com/o5nMw6J.png)



## What is a JavaScript Event? What does event.preventDefault() do and why might you use it?
A Javascript event are the **"things"** that can happen to HTML elements.


<br>

#### Common JS events
* ```onclick```	
    * Execute a JavaScript when a button is clicked
* ```onchange```	
    * An HTML element has been changed
onclick	The user clicks an HTML element
* ```onmouseover```	
    * The user moves the mouse over an HTML element
* ```onkeydown```	
    * The user pushes a keyboard key
* ```onload```	
    * The browser has finished loading the page

#### What is ```event.preventDefault()```?
It method tells the user that if the event does not get explicitly handled, its default action should not be taken as it normally would be.



## What is a NodeList? How is it different from an Array?

A NodeList object is a list (collection) of nodes extracted from a document. It is almost the same as an HTMLCollection object and is returned when you access a document's childnodes property. You do this by using ```var c = document.body.childNodes;```


Nodelists have numeric indices and lengths like an array but have their own set of methods. They cannot be manipulated with array methods such as ```.push() & .slice()```. Nodelists have their own methods including ```.keys() and .forEach()```. 

#### Nodelist Vs Array
1. Nodelist is a collection - a special array-like, iterable object

    There are two main consequences:
* We can use ```for..of``` to iterate over it:
```for (let node of document.body.childNodes) { alert(node); // shows all nodes from the collection } ```   
That’s because it’s iterable (provides the ```Symbol.iterator``` property, as required).
* Array methods **WILL NOT WORK** because it's not an array!  
```alert(document.body.childNodes.filter); // undefined (there's no filter method!)```

* However if we can use ``Array.from`` to create a “_real_” array from the collection, if we want array methods:   
```alert( Array.from(document.body.childNodes).filter ); // now it's there``` 

#### Nodelists only have one property:
```NodeList.length```


#### Nodelist Methods
* ```NodeList.item()```


* ```NodeList.entries()```


* ```NodeList.forEach()```


* ```NodeList.keys()```

* ```NodeList.values()```


## What are the security concerns around Element.innerHTML and what could you use instead?

```Element.innerHTML``` gets or sets the HTML markup contained in the element.


To insert the HTML into the document rather than replace the contents of an element, use the method ```insertAdjacentHTML()```.

Replace all text within the body
```document.body.innerHTML = "";```

#### Security considerations




Risks to take into consideration:
* Setting innerHTML will destroy existing HTML elements that have event handlers attached to them, potentially creating a memory leak on some browsers.
* You don't get back a reference to the element(s) you just created, forcing you to add code to retrieve those references manually (using the DOM API)
* You can't set the innerHTML property on all HTML elements on all browsers (for instance, Internet Explorer won't let you set the innerHTML property of a table row element)



I recommended not to use innerHTML when inserting plain text; instead, use ```Node.textContent```. This doesn't parse the passed content as HTML, but instead inserts it as raw text.



## Challenge! Create a web page with an empty \<body> and add some content using JavaScript
