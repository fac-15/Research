# Continuous Integration

An example project we created for research: [example-CI-research-travis](https://github.com/fac-15/example-CI-research-travis)

### BEFORE CI
![git merge gif](https://media.giphy.com/media/cFkiFMDg3iFoI/giphy.gif)

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

### AFTER CI
![git merge gif](https://media.giphy.com/media/D0WOL0ogZIoG4/giphy.gif)


Continuous Integration (CI) is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early. By integrating regularly, you can **detect errors quickly**, and **locate them more easily**.

#### Summary 
The aim of continuous integration is to make a simple, repeatable process that is a part of the everyday process; it should reduce integration costs and make responding to problems early easier.  

- Basic CI Lifecycle:
![](https://code-maze.com/wp-content/uploads/2016/02/ci-cycle-2.png)

#### Benefits of CI
- Reduced integration risk 
  - integrating frequently reduces the chances of build breaking bugs
-  Higher code quality
    -  dealing with less errors means that there is more time to focus on writing quality code
-  Reduced friction between team members
    -  due to presence of impartial system
-  Quality of life improvement for testers
    -  different versions and builds of the code makes it easier to isolate and deal with bugs
-  Less time deploying
-  Increased confidence and moral
    -  less fear of breaking something
-  Easier onboarding of new team members
    -  due to a clear and defined build process
-  Save and encrypt environment variables through a web interface
    -  encrypt with [travis ruby gem](https://docs.travis-ci.com/user/encryption-keys/), and a command in your terminal



![travis](http://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Travis_Logo.png/440px-Travis_Logo.png)




### What is TravisCI
- one of the major CI development platforms
- it works well with git.
- used to build and test projects on github
- it automatically detects when a new commit has been made (to any branch) and every time that happens it will try and build the project and run tests.



![travis photo](https://i.imgur.com/ZkCbJPy.png)



### How to use TravisCI

1. Log in to TravisCI and sync the account. 
2. Select the project from the list of projects. 
3. Click on the settings icon near the project name to do some changes in settings.
4. Creating a `.travis.yml` file with: 

```
language: node_js
node_js:
 - "node"
```

Make sure there is a whitespace _before_ ```- "node"```

### What happens in Github?
The most obvious difference is when you go to merge a pull request.
![](https://i.imgur.com/QWtkHu6.png)

![](https://i.imgur.com/vVh2d6I.png)

![](https://media.giphy.com/media/xT77XWum9yH7zNkFW0/giphy.gif)

### Adding a TravisCI badge

```
[![Build Status](https://travis-ci.org/fac-15/example-CI-research-travis.svg?branch=master)](https://travis-ci.org/fac-15/example-CI-research-travis)
```



