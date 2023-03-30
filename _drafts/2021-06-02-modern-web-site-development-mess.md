---
layout: post
title:  "Modern Web Site Development Mess"
date:   2021-06-02 10:57:00 -0000
categories: web development
---

### TL;DR

I have been out of web site development for a while, and now, when I need to build a simple website for my side project, i discovered a lot of new frameworks and completely lost.

I understand that develops constantly stive to create new tools to make front and back end more scalable and easy to develop. Ultimatly, the less time we need to spend to build and maintain the code the better. However, it feels that the learning curve is unnessesary too steep.

And it is not that packages do not make sense. Surely, all of them bring some value. but it looks like a 'Whild West'. There are so many different packages that seemingly doing the same thing. There are so many different ways of doing the same thing and it becomes not so obvious why someone should choos one set of packages over another. 

Here I am describing my path through the maze of web packages.

### Project Overview

To set the stage, my project is not that complicated though requires use of multiple different technologies.

Here are the requirements:
1. User Authentication and authorization.
2. Obviousely that would require Registration and Profile pages.
3. I needed to allow users to upload thier data to the site in predefined CSV format.
4. Once file is uploaded that should trigger file processing job that saves data in the format consumable by the web pages.
5. Data will be displayied in tables.
6. User can sort, filter, search, add tags and save the preferences.
7. Some of the data will need to be precalculated to be diplayed in charts.

From the get go I decided to not spend time reavieing Python of Ruby frameworks. In addition, I feel that Java and .Net are a bit obsolete and discarted them too.

There seems to be a lot of gravitational force to use Node.js or related Java Script packages. I was curious about React for a while and thought that it would be a good opportunity to learn the frameowrk.

To store data on the backend I had several options:
1. AWS - seems to be the leader in cloud technologies. A lot of companies are choosing them by default, but it would take me a bit more time to set everything up there.
2. Firebase - is very similar to AWS in capabilities and it seems a bit more intuitive to setup.
3. Asure - is trying to compete with AWS, but Microsoft left a bitter taste in my mouse. So I decided not to spend much time with them for now.
3. Other cloud providers like Heroku, and Cloudflare could be a good alternatives. I kept them on the back burner of my research.

Thus, I decided to start with Firebase. I figured I can switch to AWS if things not going to work out or when I will have more clear picture of what my architecture going to look like.

My breif look at Firebase showed that it has most of the components I need off the shelf:
1. Firebase Auth - allows to setup user Authentication and Autharization. I hae built a small prototype proving that it works as expected and relativly easy to setup.
2. Firebase Store - this is equivalent of the AWS S3 buckets for various file types. I decided to use it to store user uploaded files. 
3. Firebase Storage (or Cloud, they seem to change the name) - is Document based database that I can use to store data for the web site.
4. Firebase Function - this is similar to AWS Lambda and should allow me to put backend code there. This is the only component that Google requires an upgrade to a paid account.

I was able to built simple prototype for all the components with a free account, but the Function. I figured the amount of traffic my site is going to generate initially should not trigger any payments. I assumed that Firebase Function should allow me to build RESTfull APIs, but it is the only peice I haven't prototypes.


After building all the small pieces in isolation. I was ready to build site and put all this things together.

### React vs. Node vs. HTML vs. Express vs. Antything Else?

I have build my prototypes in simple HTML with Firebase SDK. Now I need to do the same in React.

First, I started with the [React](https://reactjs.org/) web site. It has [Tic-Tac-Toe](https://reactjs.org/tutorial/tutorial.html) example and pretty good [documentation](https://reactjs.org/docs/hello-world.html) explaining various React consempts. 

#### Where Do I start?

I decided to start with simple HTML and add React as I go. However. I still need to setup project structure, development environemnt and potencially CI/CD pipleines.

What do I need first?
1. Account with Firebase. As I learned, it would have to be paid account, though I expect the balance to be $0.00 for a while. You wold need `gmail.com` email and valid credit card.
2. Account at [Github]() (or other source control systems. [GitLab]() and [Bitbucket]() are solid alternatives). It is free. You can have your organization and projects there.

Environment dependencies: https://www.freecodecamp.org/news/quick-guide-to-understanding-and-creating-reactjs-apps-8457ee8f7123/
1. Since React is based on Node.js, we need to install node.
	a) Thebest way to install it throug `nvm` since you might need to run divverent versions of the node.
		TODO: Installation steps: nvm, npm, node. gems
	b) Npm vs Yarn - dependency management
	c) TODO: Docer for consistency and team sharing
	d) Install `create-react-app` node package (globally)
	```bash
	npm install -g create-react-app
	```
	e) TODO: React project structure and components:
		- Create react app with name `first-react-app`

	```bash
	npx create-react-app first-react-app
	```
	f)





React UI frameworks:
1. react-bootstrap
2. material-ui
3. reactstrap
4. tailwindCSS
5. baseui
6. chakra-ui


There are quite a lot of UI frameworks for React. 


#### Base Web

Base UI: https://baseweb.design/getting-started/setup#eslint-plugin-baseui

It works, but it requires set of tools that are not that mainstream: Flow, [Styleron](https://www.styletron.org/getting-started) . I also found out that there `npm` has har time reslobing the dependencies between `react` and the `baseui` libraries. I had to use `yarn`, but it seems to be a bit troublesome.

There is more info [here](https://baseweb.design/getting-started/learn), but I decided to put off `baseui` for now.


#### Material UI

Material Design exapmple: https://afteracademy.com/blog/create-react-isomorphic-app-like-a-pro
It also shows React architecture and pretty good full production expample

Example has dependency on [TypeScript](). Even though it is not very complicated, but still it is another framework to learn and worry about. In addition it required [Babel]() to build it into JS.





[Storybook](https://storybook.js.org/) is a freamework to separate UI development from the business logic, data access layer and whatever else you have in your application.

To install storybook, run the following command from the root of your project

```bash
npx sb init
```

Note that storybook needs to be installed into the project that is already setup with framework. Storybook will look into your dependencies and provide you with the best cofiguration available.

Command above will make the following changes:
- Install the required dependencies.
- Setup the necessary scripts to run and build Storybook.
- Add the default Storybook configuration.
- Add some boilerplate stories to get you started.

To check the installation run
```bash
# Starts Storybook in development mode
npm run storybook
```

Story captures the rendered state of a UI component. Single component may have several stories.



### Firebase

Motivation to use Firebase is basaed on the simplest and the most importantly the cheapest solution to start with. I also keep in mind the way I can migrate out in case my assumptions are wrong.

What services do I need?

1. Firebase Authentication

	Since Authentication is required for pretty much all the services regardless if I use Firebase or some other providers, that is the first piece I need to have setup fast.

	Firebase Authentication is very similar to AWS Cognito (and probably other Auth services. I have heard that Auth0 is pretty popular). Since Firebase Authentication is free, it is the easiest way to start.

2. Firbase Storage
3. Firestore Database
4. Realtime Database
4. Firebase Functions


You need Google email (with gmail extension) to setup an account with Firebase. Once that is setup, go to https://console.firebase.google.com/ console and create project. Project encapsulates all the services and metrics for a given site. Google will ask you permission to use your data. I just gave them the most minimal: alloed access for tech supposrt and help with marketing.

Once you have you project set, let's start with Authentication. Go to https://console.firebase.google.com/project/optionada-95736/authentication and click on `Get Started`.

You will be presented with the list of authentication options.

To use FirebaseUI to authenticate users you first need to configure each provider you want to use in their own developer app settings.

Click on email and enable email authentication only. Keep the `Email link` disabled. Click `Save`.

Select Google and enable it. By default Google will use your email you opened Firebase account with.

That is it.


#### Firebase CLI

[Install Firebase CLI](https://firebase.google.com/docs/cli#install_the_firebase_cli)

[Update Firebase CLI](https://firebase.google.com/docs/cli#update-cli)


Please check [Firebase CLI docs](https://firebase.google.com/docs/cli) for more info.
[Is this the same info?](https://firebase.google.com/docs/cli#mac-linux-npm)

First you need to set it up on your machine. (Mac OS: Using `npm`)

```bash
npm install -g firebase-tools
```

Login and test Firebase CLI

```bash
firebase login
```

This command connects your local machine to Firebase and grants you access to your Firebase projects.

Note: The firebase login command opens a web page that connects to localhost on your machine. If you're using a remote machine and don't have access to localhost, run the command with the flag `--no-localhost`.


Note: You can also [use the Firebase CLI with CI systems](https://firebase.google.com/docs/cli#cli-ci-systems).

Test CLI installation

```bash
firebase projects:list
firebase login:list
firebase help
```

Logout

```bash
firebase logout
```

To use another account for a specific project

```bash
firebase login:use ishvager@gmail.com
```

##### Initialize Firebase project

Since Firebase requrires common directiory to perform many common tasks, we need to link local folder to a Firebase project by using

```bash
firebase init
```

Note: The firebase init command does not create a new directory. If you're starting a new app, you must first make a directory, then run firebase init from within that directory.

To use more then one Firebase account, add another account

```bash
login:add -P optionada-95736 ishvager@gmail.com 
```

Switch from between accounts

```bash
firebase use [options] [alias_of_the_project_id]
```

Note: once we login and added account, firebase init fails with `.firebaserc already has a default project, using optionada-443f1.` error.


##### Create Web App

Go to projec's overview and click on web app. It will ask you to provide webapp name and whethere you want to host it. Say yes.

To deploy your web

```bash
firebase deploy
``` 









Random thoughts bla
--------------------


Firebase Local Emulator

Helps develop locally. All Firebase services will be run locally.

Unit Testing: using Firebase Test SDK, we can run unit test in Node.js using mocha test runner.
	- loading Security Rules
	- flushing the local database between tests
	- managing syncronous interation with the emulators

Integration Tests: each product emulator responts to SDK and REST API calls, so we can build scripts to write self contained integration tests.

Manual Tests: by connectiong to individual Emulation Services, we can test Firebase app manually.


In addition we can use 
	- Cloud Function shell for inteactive and iterative function prototyping and development.
	- Rules Playgroud, a part of Firebase console, interactive experience with Security Rules desing. [Quickly validate Firebase Security Rules.](https://firebase.google.com/docs/rules/simulator)


[Install and configure Local Emulator Suite.](https://firebase.google.com/docs/emulator-suite/install_and_configure)
































### Tailwind CSS

[Tailwind Tutorial](https://dev.to/hagnerd/setting-up-tailwind-with-create-react-app-4jd)

