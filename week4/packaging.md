# Packaging

![gif](https://media.giphy.com/media/407R27DUChMPJnRIO8/giphy.gif)

### Dependencies: 
- **What is a dependency?**

     Dependency is a broad software engineering term used to refer when **a piece of software relies on another one**.
     

- **Why might you want to use a dependency in your project, rather than writing the code from scratch?**

    - Save a lot of time and space
    - Reliable

- **What have traditionally been some of the issues with managing dependencies?**

    #### Dependency duplication and the dependency tree

- Unlike other package managers, npm installs a tree of dependencies. That is, every package installed gets its own set of dependencies rather than forcing every package to share the same canonical set of packages. 

- For example, consider two packages, foo and bar. Each of them have their own set of dependencies, which can be represented as a tree:

    foo
    ├── hello ^0.1.2
    └── world ^1.0.7

    bar
    ├── hello ^0.2.8
    └── goodbye ^3.4.0

Imagine an application that depends on both foo and bar. Obviously, the world and goodbye dependencies are totally unrelated, so how npm handles them is relatively uninteresting. However, consider the case of hello: both packages require conflicting versions.

Most package managers (including RubyGems/Bundler, pip, and Cabal) would simply barf here, reporting a version conflict. This is because, in most package management models, only one version of any particular package can be installed at a time. In that sense, one of the package manager’s primary responsibilities is to figure out a set of package versions that will satisfy every version constraint simultaneously.

In contrast, npm has a somewhat easier job: it’s totally okay with installing different versions of the same package because each package gets its own set of dependencies. In the aforementioned example, the resulting directory structure would look something like this:

node_modules/
├── foo/
│   └── node_modules/
│   _ ├── hello/
│   _ └── world/
└── bar/ 
   _ └── node_modules/
      __  ├── hello/
       __ └── goodbye/
        
Notably, the directory structure very closely mirrors the actual dependency tree. The above diagram is something of a simplification: in practice, each transitive dependency would have its own node_modules directory and so on, but the directory structure can get pretty messy pretty quickly. 

This model is, of course, extremely simple. The obvious effect is that every package gets its own little sandbox. If foo depends on ramda@^0.19.0 but bar depends on ramda@^0.22.0, they can both coexist completely peacefully without any problems.

This system is better than the alternative, flat model, so long as the underlying runtime supports the required module loading scheme. However, it is not without drawbacks.

The most apparent downside is a significant increase in code size, given the potential for many, many copies of the same package, all with different versions. A larger program—it can have a significant impact on performance. Larger programs just don’t fit into CPU caches as easily, and merely having to page a program in and out can significantly slow things down. That’s mostly just a tradeoff, though, since you’re sacrificing performance, not program correctness.

The more difficult problem is how dependency isolation can affect cross-package communication.

### Dev dependencies vs. Dependencies: 

devDependencies are used for the build process, tools that help you manage how the end code will end up, third party test modules, (ex. webpack stuff)

devDependencies are modules which are only required during development whereas **dependencies are required at runtime.** 

If you are deploying your application, **dependencies has to be installed**, or else your app simply will not work. 

The difference between these two, is that devDependencies are modules which are only required during development, while dependencies are modules which are also required at runtime.

To save a dependency as a **devDependency** on installation we need to do an npm install `--save-dev`, instead of just an `npm install --save`. A nice shorthand for installing a devDependency that I like to use is `npm i -D`. The shorthand for saving a regular dependency is -S instead of `-D`.

Some good examples of dependencies which would be required at runtime include React, Redux, Express, and Axios.

Some good examples of when to install devDependencies would be Nodemon, Babel, ESLint, and testing frameworks like Chai, Mocha, Enzyme, etc…

#### Examples: 

- When you install an npm package using `npm install <package-name>`, you are installing it as a dependency.

- The package is automatically listed in the `package.json` file, under the dependencies list.

- When you add the `-D` flag, or `--save-dev`, you are installing it as a development dependency, which adds it to the devDependencies list. 

- When you go into production, if you type `npm install` and the folder contains a `package.json` file, they are installed, as npm assumes this is a development deploy.

- You need to set the `--production` flag (`npm install --production`) to avoid installing those development dependencies.



## Node dependencies
There are several dependencies that Node.js relies on to work the way it does.
### Node dependencies: Libraries

- V8  
V8 is Google’s open source high-performance JavaScript and WebAssembly engine, written in C++. It is used in Google Chrome, the open source browser from Google.

- libuv 
libuv is a multi-platform support library with a focus on asynchronous I/O.

- http-parser 
This library parses HTTP protocol for requests and responses.
Monkey patch before you require http for the first time.

```
process.binding('http_parser').HTTPParser = require('http-parser-js').HTTPParser;
var http = require('http');
```
- c-ares
c-ares is a C library for asynchronous DNS requests (including name resolves)

- OpenSSL 
OpenSSL is a toolkit for the Transport Layer Security (TLS) and Secure Sockets Layer (SSL) protocols. It is also a general-purpose cryptography library.

- zlib 
A software library used for data compression.zlib

### Node dependencies: Tools

- npm 
npm is a package manager for JavaScript. It is the default package manager for JavaScript runtime environment Node.js. It consists of a command line client, also called npm, and an online database of public and paid-for private packages, called the npm registry.

- gyp 
GYP is a build automation tool. GYP was created by Google to generate native IDE project files for building the Chromium web browser and is licensed as open source software using the BSD software license. 


### NPM: 
- **What is a package manager?**

    - A package manager is a collection of software tools that automates the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system in a consistent manner.

    - npm is the package manager for JavaScript 
- **How does it help with dependencies?**

    - Easy to install
    - Manages the installations of new packages/ dependencies
    - Alerts devs about vulnerabilities and conflicts
- **What is package.json?**
    - All npm packages contain a file, usually in the project root, called `package.json`. 
    - This file holds various metadata relevant to the project. 
    - This file is used to give information to npm that allows it to identify the project as well as handle the project's dependencies.

- **What does npm init do?**
    - `npm init` can be used to set up a new or existing npm package.
    - Any additional options will be passed directly to the command, so `npm init -y` will create a new project and initialize the description to default values. For example:
    
    ```
  {
  "name": "<Folder name>",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
    }
    ```

- **How do you use an installed package in your code?**

- To use an npm package from a file in your application you import the name of the package:
    ```
    import moment from 'moment';

    // this is equivalent to the standard node require:
    const moment = require('moment');
    ```
    
For example, **nodemon** wraps your application, so you can pass all the arguments you would normally pass to your app

1. `npm i nodemon`

2. put the package name in 'scripts' in package.json(dependencies)
3. ![](https://i.imgur.com/uBsQXdR.png)

4. In terminal, npm run dev


### npm install: 

- there are two ways to install things:

**globally** —- This drops modules in {prefix}/lib/node_modules, and puts executable files in {prefix}/bin, where {prefix} is usually something like /usr/local. It also installs man pages in {prefix}/share/man, if they’re supplied.

**locally** —- This installs your package in the current working directory. Node modules go in ./node_modules, executables go in ./node_modules/.bin/, and man pages aren’t installed at all.

**Which to choose**
Whether to install a package globally or locally depends on the global config, which is aliased to the -g command line switch.

Just like how global variables are kind of gross, but also necessary in some cases, global packages are important, but best avoided if not needed.

In general, the rule of thumb is:

If you’re installing something that you want to use in your program, using require('whatever'), then install it locally, at the root of your project.
If you’re installing something that you want to use in your shell, on the command line or something, install it globally.


## Package files quick quiz 

- **Where does NPM install packages?**

![](https://i.imgur.com/g2HMs2l.png)


- **Why is it important to make sure that installed packages aren't included in your repositories?**

![](https://i.imgur.com/iRccnSg.png)

    
- **How do you prevent Git from including these files in your repository?**

![](https://i.imgur.com/R98DxXO.png)




![gif](https://media.giphy.com/media/k83akFa8k9tvi/giphy.gif)
