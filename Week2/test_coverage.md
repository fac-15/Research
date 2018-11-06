# TEST COVERAGE 


[Code coverage exercise from yesterday](https://github.com/dwyl/learn-tape#bonus-level)
## Test Frameworks
[Istanbul](https://www.npmjs.com/package/istanbul)
[nyc](https://www.npmjs.com/package/nyc)
[node v.10 +](https://medium.com/the-node-js-collection/rethinking-javascript-test-coverage-5726fb272949). Test coverage tools now covered in Node (perhaps!)
<img src="https://media.giphy.com/media/xUPGcpfvIsVNeOAZgI/giphy.gif" alt="bug" width="500"/>

## What is test coverage?

- Put simply, test coverage is a useful way to get an **idea** of **how well** an application has been **tested**.


- You may have written good tests that pass, but if they only test **a limited percentage** of your source code then it's hard to be confident about the entire end product. If part of your code is **untested**, how would you know if there's any **bugs** lurking there?

<img src="https://media.giphy.com/media/1xOQlQxrIX4Jw6lBZI/giphy.gif" alt="bug" width="250" style="margin-left:10em;"/>


- This is where **test coverage** comes in - it will give you the **percentage** of your source code that is exercised by your test suite (for example, Tape). These are some of the most important **criteria** that coverage takes into account:
  - **Statement coverage**:
    - Has each statement in the code been executed?
  - **Function coverage**
    - Has each function in the code been called?
  - **Branch coverage**
    - Has each branch of each control structure (eg. The _true_ and _false_ brances within an _if_ statement) been executed?
  - **Condition coverage** 
    - Has each Boolean sub-expression evaluated both to true and false?
  - (Oliver will show this in practice later)

- **However**, it's **important** to remember that even if you achieve 100% code coverage, **this doesn't necessarily mean** that all your tests are perfect.
<img src="https://media.giphy.com/media/MPuTZQqOmYKPK/giphy.gif" alt="your opinion"/> 

- This is simply because test coverage relies upon the tests that **you** have written, and if you haven't accounted for things like edge cases and unpredictable user input, it may not flag that up.

- **So** - test coverage lets you know **how much** of your code is untested, but **won't necessarily** give you an indication of **how well** written those tests actually are. **For example**:

<img src="https://media.giphy.com/media/10eJOwQ9BKrF72/giphy.gif" alt="bear test" width="450" style="margin-left:5em; margin-bottom:2em"/>

   
- It's also known as **code coverage**, or even just **coverage**, and in a large company would be the kind of stuff that the Quality Assurance team would be working on.

## Why is test coverage useful?

- As explained above, test coverage tools help you to find out how much of your code base your tests cover. This can ultimately help you to:

    - **Write more tests**, in an attempt to cover your full code base
    - **Organise** your tests better
    - **Refactor** your code
    - And work more **efficiently!**

- Like testing itself, coverage helps you to write your code with more **confidence**, without fear of breaking something - you've got **a better overview** of which parts of your code do and don't work, and which parts are **unaddressed**. 

- It's useful in ensuring that all your components play together nicely (**integration testing**), and of course that they’re even individually functioning at all (**unit testing**).

- Test coverage helps to streamline the **TDD** (Test Driven Development) process. If you're going to be spending loads of time writing tests, it's going to be easier if you know which tests you need and where to use them!



## What are Istanbul and nyc?
### [Istanbul](https://istanbul.js.org/)
 - A code coverage tool that works with node
 - Tracks how well _unit tests_ exercise your codebase.
 - Computes statement, line, function and branch coverage
 - When run with `istanbul cover <test.js>`, will output results to the console, and in json and html files in the `/coverage` folder in the root of your project.
 - Supports ES2015+ testing with [babel-plugin-istanbul](https://github.com/istanbuljs/babel-plugin-istanbul)

### [NYC](https://github.com/istanbuljs/nyc)
 - An extension of Istanbul (Istanbul is a dependency of nyc), that _provides support for_ 'applications that spawn processes', and 'ES2015 transformations', via source maps and babel.
 - Works well with most JavaScript testing frameworks (those that are more popular than Tape!) - e.g. [Mocha](https://mochajs.org/), Jest, etc.
 - Also works with TypeScript (used in Angular).
 - Extra functionality also includes _stack traces_, which show the order of functions run to achieve the current state of the webpage or application. `console.trace()` provides an implementation of this in the console. [More on Stack Trace](https://code-maven.com/stack-trace-in-javascript).


## How would you use them to improve your testing?

### Using different coverage criteria to evaluate whether you have written appropriate tests

![](https://image.ibb.co/hytNoV/Screen-Shot-2018-11-06-at-2-44-59-PM.png)
- *Function coverage* - ```foo()``` was called at least once
- *Statement coverage* - called as ```foo(1,1)``` 
  - Every line in the function is executed including ```z = x```;.
- *Branch Coverage* - Tests calling ```foo(1,1)``` and ```foo(0,1)``` 
  - in the first case, both if conditions are met and ```z = x;``` is executed, while in the second case, the first condition ```(x>0)``` is not satisfied, which prevents executing ```z = x;```.
  - Full branch coverage = 100 percent statement coverage.
- *Condition coverage* - tests that call ```foo(1,0)``` and ```foo(0,1)```. 
  - These are necessary because in the first cases, ```(x>0)``` evaluates to true, while in the second, it evaluates false. At the same time, the first case makes ```(y>0)``` false, while the second makes it true.
  - 100 percent condition coverage is hard! Therefore there are a number of options for reporting that focus on the most important combinations
- There are other forms of coverage criteria, however the above listed types are the most important 
- Need to look at all crteria together! - 96.3% line coverage, but only 50% branch coverage 
  - ![](https://cloud.githubusercontent.com/assets/194400/14235496/d5ae4f4e-f9f7-11e5-9388-c50dcca10cbf.png)

<img src="https://media.giphy.com/media/7MZ0v9KynmiSA/giphy.gif" alt="bug" width="500"/>

### Code Coverage in your workflow
- No hard rules about when and how to use 
- Does not guarantee good tests, just a tool

- Begin to focusing on testing, not on coverage
- Use it to identify holes in your test suite
- When your project is big enough, coverage reports can be useful 
  - Most tools  allow you to dig into the coverage reports to see the actual items that weren't covered by tests and then use that to identify critical parts of your application that still need to be tested. 
- When using Continuous Integration (CI), you can make Code Coverage part of your flow
  - "CI is the process of automating the build and testing of code every time a team member commits changes to version control."
  - Can start failing the tests if you don't reach a high enough percentage of coverage 
- Also possible to sign up to external services to track code coverage 
  - Useful for larger organizations and projects who would like to track coverage across different test suites/projects, to integreate it with CI, to see detailed reports and visualizations, etc.
  - E.g. [Dwyl's tutorial on Istanbul](https://github.com/dwyl/learn-istanbul) recommends [CodeCov](https://codecov.io/#features). Some of the features that they talk about include:
    - When you create a pull request your CI will send a coverage report to Codecov and Codecov will leave a comment on the PR
    - you can see at a glance if new code is being added without corresponding tests
    - When the coverage is lower the Pull Request "fails"  

## Challenge! Use Istanbul/nyc to calculate your code coverage for the TDD workshop.

### Install istanbul from NPM:

    npm install istanbul --save-dev

### Run the following command (in your terminal) to get a coverage report:

    node_modules/.bin/istanbul cover node_modules/.bin/tape ./test/*.test.js
    
**or**
    
    node_modules/.bin/istanbul cover <file-where-your-tests-are.js>
    
**make sure you run this on the file that contains your tests, not your codebase file(s)!!!**    

### You should expect to see something like this:

![](https://preview.ibb.co/m4WdvA/Screen-Shot-2018-11-06-at-15-04-39.png)

### Also you are able to see the report in browser:

#### Go to your project root directory, open the **coverage** folder,then **Icov-report** and open **index.html** in browser.

![](https://image.ibb.co/cZuvQA/Screen-Shot-2018-11-06-at-15-42-34.png)

## Do not rely only on your test coverage ##
<img src = "https://tenor.com/view/fail-bathroom-twerk-gif-3545393.gif" alt="fail" width="470" style="margin-left:5em;"/>



