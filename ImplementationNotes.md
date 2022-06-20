## Implementation Notes 

This project is meant to be an introduction to Next.JS for building a modern website - the end goal
is to design a professional looking blog/cv site which can be hosted using github pages. 


### Introduction

We start by looking at the Next.js Foundations course to guide through the prerequisite knowledge 
for Next.js. We run through a simple project - starting a Javascript application and then migrating 
it to React and Next.js. 


Next.js is a flexible React framework that provides building blocks to create fast web applications. 

### Building Blocks of Web Application 

There are several things to consider when building modern applications including: 

* User Interface - how users will consume and interact with the application 
* Routing - how users navigate between different parts of the application 
* Data Fetching - where the data lives and how to get it 
* Rendering - when and where you render static or dynamic content 
* Integrations - what third-party services will be used (CMS, auth, payments) and how you connect 
  to them 
* Infrastructure - where you deploy, store and run the application code (serverless, cdn, edge) 
* Performance - how to optimize your application for end-users
* Scalability - how your application adapts as your team, data and traffic grow 
* Developer Experience - your team's experience building and maintaining your application 

For each part of the application, we need to decide whether to build a solution ourselves or use 
other tools such as libraries and frameworks 

### What is React? 

React is a JavaScript library for building interactive user interfaces. By user interfaces we 
mean the elements that users see and interact with on-screen. 

Library means that React provides helpful functions to build UI but leaves it up to the developer 
where to use those functions in their application. 

Part of the success of react is that it is relatively unopinionated about the other aspects of 
building applications. This has resulted in a flourishing ecosystem of third-party tools and 
solutions. 

It also means that building a complete React application from the ground up requires so effort - 
developers need to spend time configuring tools and reinventing solutions for common application 
requirements. 

### What is Next.js? 

Next.js is a react framework that gives you building blocks to create we applications - by framework
we mean that Next.js handles the tooling and configuration needed for React, and provides additional 
structure, features and optimizations for your application. 

You can use React to build the UI then incrementally adopt Next.js features to solve common
application requires such as routing, data fetching, integrations - all while improving the 
developer and end-user experience. 

Whether you are a individual developer or part of a larger team, you can leverage React and Next.js
to build fully interactive, highly dynamic and performant web applications. 

Next we discuss how to get started with React and Next.js. 


### From JS to React 

### Rendering User Interfaces 

To see how React works we first will go over how browsers interpret your code to create interactive
user interfaces (UI). 

When a user visits a web page, the server returns an HTML file to the browser - the browser then
reads the HTML and constructs the Document object Model (DOM). 


### What is the DOM? 

The DOM is an object representation of the HTML elements. It acts as a bridge between your 
code and the user interface and has a tree-like structure with parent and child relationships. 

You can use DOM methods and a programming language like JavaScript to listen to user events and 
manipulate the DOM by selecting, adding, updating and deleting specific elements in the user 
interface. DOM manipulation allows you to not only target specific elements but also change their 
style and content. 

We can see how Javascript and DOM methods can be used below: 

```html
<!-- index.html --> 
<html> 
	<body> 
		<div id="app"></div>
	</body>
</html> 
```

The div is given a unique id so that we can target it later. 


```html 
<script type="text/javascript">
	const app = document.getElementById('app');
	const header = document.createElement('h1');
	const headerContent = document.createTextNode(
		'Develop. Preview. Ship.'
	);

	head.appendChild(headerContent);
	app.appendChild(header); 
</script>
```

Javascript can be written inside a HTML file by adding a script tag - inside it we can use a DOM 
method `getElementById()` to select the `<div>` element by its `id`. We can continue to use DOM 
methods to create a new `<h1>` element.


### HTML vs the DOM 

If we look at the DOM elements using the browser developer tools, we will notice the DOM includes 
the `<h1>` element. The DOM of the page is different from the source code - or in other words, the
original HTML file you created 

This is since the HTML represents the initial page content, whereas the DOM represents the updated
page content which was changed by the Javascript code we wrote. 

Updating the Dom  with plain Javascript is very powerful but verbose. A lot of code was written 
just to write an `<h1>` element with some text. As the team or the size of the application grows 
it can become increasinly challenging to build applications this way. 

This way, developers spend a lot of time writing instructions to tell the computer how it should 
do things. But wouldn't it be nice to describe what you want to show and let the computer 
figure out how to update the DOM! 


### Imperative vs Declarative Programming 

The code above is a good example of imperative programming. You are writing the steps for how the 
user interface should be updated. But when it comes to building user interfaces, a declarative 
approach is often preferred because it can speed up the development process. Instead of having to 
write DOM methods, it would be helpful if developers were able to declare what they want to show
(in this case, an 'h1' tag with some text). 

In other words imperative programming is like giving a chef step-by-step instructions on how to 
make a pizza. Declarative programming is like ordering a pizza without being concerned about the 
steps it takes to make the pizza. 

A popular declarative library that helps developers build user interfaces is React. 


### React: A declarative UI library 

As a developer you can tell React what you want to happen to the user interface, and React will 
figure out the steps of how to update the DOM on your behalf. Next, we will explore how we can get
started with React. 



### Getting Started with React 

To use react in a project we can load two React scripts from an external website called unpkg.com: 

* react is the core react library
* react-dom provides DOM-specific methods that enable you to use React with the DOM 

```html 
<!-- index.html --> 

<script src="https://unpkg.com/react@17/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
```

Instead of directly manipulating the DOM with plain Javascript you can use `ReactDOM.render()` from
`react-dom` to tell React to render our `<h1>` title inside our app element. 

```javascript
<script type="text/javascript">
	const app = document.getElementById('app');
	ReactDOM.render(<h1>Develop. Preview. Ship. </h1>, app);
</script>
```

 
