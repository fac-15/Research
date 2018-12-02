# NODE SHELL PROJECT

Our research group were meant to create our own test output formatter.

Footage of what our afternoon looked like:

![the struggle is real](https://media.giphy.com/media/3otPoo4b2gdv8BBvFK/giphy.gif)



### PIPING 

"The pipe() function reads data from a readable stream as it becomes available and writes it to a destination writable stream." - StackOverflow user **hexacyanide** 

![smoking pipe](https://media.giphy.com/media/tGQFAuLzsabkI/giphy.gif)

Aim is to pipe the results of test.js into the output-formatter.js file,  this will now read the results of those tests and provide us with useful information.

1. Used files from Node Shell project folders, cloned test and logic functionality
2. Setup output.js file and the package.JSON to pipe from test.js to output-formatter
3. used process.stdin to pipe the file in utf8 format
4. Chuck that data that comes from test.js and add to a empty string
5. Write error handler
6. Ouput end event, by splitting each line from the test output by each new line, loop over the test and look for "not ok" & if true add to the counter.

```
CODEEEEE DEMO
```




### Problems we had

Finding out how to pipe test.js into the output-formatting.js file
& how to make the output useable
Outputing images using ASCII code into the terminal




### The Cow

We dedicated few minutes trying to find an image that would be rendered nicely in the terminal, and the cow did fulfill our needs.
We were not able to isolate the syntax that would allow all images to be rendered.

```
  `________________________________________
< mooooooooooooooooooooooooooooooooooooo >
 ----------------------------------------
        \\   ^__^
         \\  (oo)\\_______
            (__)\\       )\\/\\
              ||----w |
                ||     ||`,
;

```

### Stretch Goals

Make output colorful
Upload to NPM as a package, so people can download it
Take error message and display to user
Using full pictures as output

