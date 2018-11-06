# Types of Testing 

## What is a unit test?

![](https://giphy.com/embed/STLj8QUhg25pe)

Unit testing is a software development process in which the smallest testable parts of an application, called *units*, are individually and independently scrutinized for proper operation. 

Unit testing involves breaking your program into pieces, and subjecting each piece to a series of tests. 

![](https://i.imgur.com/App8NeX.png)

### Unit testing principles: 
- Each part is tested individually 
- All components are tested at least once 
- Errors are picked up earlier 
- Scope is smaller -> easier to fix errors 

### Unit testing ideals: 
- **Isolatable**: Usually tests are run as separate programs, but the method of testing varies, depending on the language, and type of software (GUI, command-line, library).
- **Repeatable**
- **Easy to write**
- **Automatable**: Unit testing can be done manually but is often automated.
- **Periodically**: Tests are usually run periodically, often **after every change to the source code**. The more often the better, because the sooner you will catch problems.
- **Simple output**: The output from a test can be as simple as a console output, to a "green light" in a GUI such as NUnit, or a different language-specific framework.
- **Performing unit tests is designed to be simple**: The tests are written in the form of functions that will determine whether a returned value equals the value you were expecting.


## What is an integration test?

- **Individual units are combined and tested as a group**
- **Goal: Expose problems** in the interaction between integrated units
- **When**: This is the **second level** of testing performed after Unit Testing.
- **Who**: Developers themselves or independent testers perform Integration Testing.

<iframe src="https://giphy.com/embed/LWI0MveNXZeJW" width="397" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/kid-genius-LWI0MveNXZeJW"></a></p>


**Analogy:** During the process of manufacturing a ballpoint pen, the cap, the body, the tail and clip, the ink cartridge and the ballpoint are produced separately and unit tested separately. When two or more units are ready, they are assembled and Integration Testing is performed. For example, whether the cap fits into the body or not.

![](https://i.imgur.com/D78f8PO.jpg)

### Types of integration testing: 

- Big-bang
- Top-down
- Bottom-up
- Sandwich

### Big-bang approach
- **Big Bang** Integration Testing is an integration testing strategy wherein all units are linked at once, resulting in a complete system.
- This method can be **very effective for saving time** in the integration testing process. 
- However, when this type of testing strategy is adopted, it is **difficult to isolate any errors found**, because attention is not paid to verifying the interfaces across individual units.

### Bottom-up approach
![](https://i.imgur.com/2KXQI21.png)

- **Bottom-up** testing is an approach to integrated testing where the lowest level components are tested first, then used to facilitate the testing of higher level components. 
- The process is repeated until the component at the top of the hierarchy is tested. 
- All the bottom or low-level modules, procedures or functions are integrated and then tested.
- This approach is helpful only when all or most of the modules of the same development level are ready.

<iframe src="https://giphy.com/embed/d2Z99CRTQNnEYzmw" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/bbcearth-earth-bbc-thehunt-d2Z99CRTQNnEYzmw"></a></p>
<br>
<br>
<br>
<br>

### Top-down approach
![](https://i.imgur.com/gvwDfB2.png)

- **Top-down** testing is an approach to integrated testing where the top integrated modules are tested and the branch of the module is tested step by step until the end of the related module.
- It's a technique used in order to simulate the behaviour of the lower-level modules that are not yet integrated. Stubs are the modules that act as temporary replacement for a called module and give the same output as that of the actual product.
<iframe src="https://giphy.com/embed/alUHKvX7BJXwc" width="480" height="443" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/falling-funny-alUHKvX7BJXwc"></a></p>
<br>
<br>
<br>
<br>

### Sandwich approach

- **Sandwich testing** is an approach to combine **top down** testing with **bottom up** testing.
- One limitation to this sort of testing is that any conditions not stated in specified integration tests, outside of the confirmation of the execution of design items, will generally not be tested.

![](https://i.imgur.com/HnW61nm.png)

### Modified sandwich testing
A better version of sandwich testing, modified sandwich testing model fights the drawbacks of sandwich testing and helps testers perform accurate and precise integration testing. During the process of this testing, individual layers of the software components are tested first, which are later combined together with each other in increments and tested simultaneously.

Testing Strategy:

Individual Layer Testing: To ensure proper integration, subsystems and their interfaces are tested separately with the assistance of stubs and drivers. Moreover, as the testing progresses, these stub and drivers are replaced by top and bottom layer.

<iframe src="https://giphy.com/embed/l3nWaqfPyxbtGWihG" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/fear-sandwich-cold-cuts-l3nWaqfPyxbtGWihG"></a></p>

Testing in Parallel: Once the process of individual testing is over, the team starts testing various components of the software together. Here, the the focus shifts from individual testing top parallel testing. Carried out in two stages, parallel testing also require stubs and driver to complete the testing process.

Here, the the middle layer of the system is tested with stubs and drivers, top layer with stubs, and bottom layer with drivers. All of these are tested simultaneously at the same time.

In this stage, the stubs and drivers present in the first stage are replaced by top and bottom layer. In short, in this stage, the top layer accesses the middle layer, but the drivers are replaced by the top layer and bottom layer is accessed by the middle layer, where bottom layer replaces stubs.

![](https://i.imgur.com/ESKIdu9.png)

Advantages:
Allows parallel testing of various elements of the software system.

Enables early testing of user interface components.

Performs more coverage with the same stubs.

It is a time saving process as several components are tested simultaneously.

Disadvantages:
Requires development of many stubs and drivers.

As the need for stubs and drivers is high, this model of testing becomes quite expensive.

## What is end-to-end testing?

![](https://i.imgur.com/no5zBXX.png)

### What
End-to-end testing is a methodology used to test whether the flow of an application is performing as designed from start to finish. 

It is performed from start to finish under real-world scenarios like communication of the application with hardware, network, database and other applications.


### Why

“End to End testing” is defined as a testing method which determines whether the performance of an application is as per the requirement or not. 
The main reason for carrying out this testing is to determine various dependencies of an application as well as ensuring that accurate information is communicated between various system components. It is usually performed after completion of functional and system testing of any application.


## When would you use each kind of test?


### Unit testing: the first pitfall

<iframe src="https://giphy.com/embed/GhbcQjXkh6QDu" width="480" height="271" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/kim-kardashian-kanye-west-kimye-GhbcQjXkh6QDu"></a></p>

A unit can be anything from a full feature to a button, and it’s important you make sure you at least have all the units working individually before you can definitively say the software works as a whole.

Unit testing is essential, and done by the development team, every time when reviewing new parts of the code base.

### Integration testing: check if the units work well together
Integration testing moves one level higher than unit testing, and looks at how the units integrate with each other.

For example, after building a unit for archiving checklists, we might find that it breaks the search function. While integration testing, we’d find out which parts of the code clash and fix that during the debugging phase.


### System testing: does the entire piece of software work as intended?
By the time you get to system testing, you need to have completed both unit and integration tests and have the software fully loaded up in a test environment.

### Usability testing: are the user interfaces easy to operate and understand?

- Documentation testing: does the system guide explain the features as they work in real life?
- Functionality testing: does everything behave as expected and described in documentation?
- Inter-operability testing: does the system work with third party systems (different OS, browser, plug-ins, etc.)?
- Performance testing: does the system break itself by trying to use too many resources?
- Scalability testing: is the system affected by user count, user location, or server load?
- Stress testing: what’s the maximum strain the system can take before it breaks?
- Load testing: can the system handle the expected strain?
- Regression testing: do new features break old ones?
- Compliance testing: does the system comply with regulators (e.g. HIPAA)?
- Security testing: are there any security vulnerabilities?
- Recoverability testing: how fast/effectively does the system recover after breakdown?

### User acceptance testing: alpha and beta (black box) testing

The process is simple:

- Select a varied sample of power users (different locations, platforms, etc.)
- Invite them to the beta with a key
- Require they submit their feedback
- Iterate on the software based on feedback
