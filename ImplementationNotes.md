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

When this code is run in the browser we end up with a syntax error because `<h1>...</h1>` is not 
valid Javascript - it is JSX 


### What is JSX? 

JSX is a syntax extension for Javascript that allows you to describe your UI in a familiar HTML-like
syntax. The nice thing about JSX is that a part from the three JSX rules there is no need to learn 
any new symbols or syntax outside of HTML and JavaScript: 

* Return a single root element: to return multiple elements from a component, wrap them with a single
  parent tag - for example you can use a <div>

* Close all the tags: JSX requires tags to be explicitly closed: self-closing tags like <img> must 
  become <img/> 

* camelCase most of the things: JSX turns into JavaScript and attributes written in JSX become keys
  of JavaScript objects. In components you will often want to read these attributes into variables. 
  JavaScript has limitations on variable names - their names cannot contain dashes or be reserved 
  words like class. This is why many HTML and SVG attributes are written in camelCase, so instead 
  of stroke-width we use strikeWidth 


Note that browsers do not understand JSX out of the box, so we need a JavaScript compiler such as 
Babel, to transform JSX code into regular JavaScript


### Adding Babel to the project 

To add Babel to the project, copy the following script in `index.html` file: 

```javascript
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
``` 

In addition we need to inform Babel what code to transform by changing the script type to 
`type=text/jsx`. 


We can see that comparing the declarative React code with the imperative Javascript code, React 
allows us to cut down on a lot of repetitive code. 


### Essential JavaScript for React 

Would be helpful to brush up on core JavaScript principles before diving into React 


### React Core Concepts 

There are three core concepts of React that you need to be familiar with to start building React 
applications. These are: 

* Components 
* Props 
* State 



### Building UI with Components 

User interfaces can be broken down into smaller building blocks called components. Components allow
you to build self-contained, reusable snippets of code. If you think of components as LEGO bricks, 
you can take individual bricks and combine them together to form larger structures. If you 
need to update a piece of the UI you can update the specific component or brick. 


This modularity allows the code to be more maintanable as it grows since you can easily add, update
and delete components without touching the rest of the application. 

The nice thing about React components if that they are just JavaScript. THe following is an example 
of a React component: 


### Creating components 

In React, components are functions - a component is a function that returns UI elements. Inside the
return statement of the function you can write JSX: 

```
function Header() {
	return (<h1>Develop. Preview. Ship. </h1>)
}
``` 

To render this component to the DOM, you can pass it as an argument in the `ReactDOM.render()` 
method: 

```
const app = document.getElementById("app")

function Header() {
...
} 

ReactDOM.render(<Header/>, app)
```


Note that React components should be capitalized to distinguish them from plain HTML and JavaScript.
React components should also be used the same way we would use regular HTML tags with angle brackets
`<>`. 


### Nesting Components 

Applications usually include more content than a single component - you can nest React components 
inside each other like you would with regular HTML elements. 

This could look something like: 

```
function Header() {
	return <h1>Develop. Preview. Ship.</h1>
} 

function HomePage() {
	return (
		<div> 
			{/* Nesting the Header component */}
			<Header />
		</div>
	);
}

ReactDOM.render(<Header />, app);
```

 
### Component Trees 

You can keep nesting React components this way to form component trees. For example a HomePage 
component could hold a `Header`, an `Article` and a `Footer` component. These components can in 
turn have their own child components and so on. The `Header` could contain a `Logo`, `Title` and 
`Navigation` component. 

This modular format allows you to reuse components in different places inside your app. In the 
previous example, since Homepage is the top-level component, you can pass it to the 
ReactDOM.render() method. Next we discuss props and how to use them to pass data between components.


### Displaying Data with Props 

If we were to reuse the `<Header />` component, it would display the same content both times: 

```
function Header() {
	return <h1>Develop. Preview. Ship.</h1>
}

function HomePage() {
	return (
		<div> 
			<Header /> 
			<Header />
		</div>
	);
}
```

What if we want to pass different text or you do not know the information ahead of time because we
are fetching data from an external source? 

Regular HTML elements have attributes that we can use to pass pieces of information that change the 
behavior of those elements. For example, changing the `src` attribute of an `<img>` element changes 
the image that is shown. Changing the `href` attribute of an `<a>` tag changes the destination of 
the link.


In the same way, we can pass pieces of information as properties to React components. These are 
referred to as `props`.


Similar to a JavaScript function, you can design components that accept custom arguments (or props)
that change the component's behavior or what is visibly shown when it is rendered to the screen. 
These props can then be passed from parent components to child components. 

> In React, data flows down the component tree. This is referred to as one-way data flow. State, 
which will be discussed below, can be passed from parent to child components as props. 


### Using props 

In the `Homepage` component, we can pass a custom `title` prop to the `Header` component just 
like you would pass HTML attributes. 

```javascript 
function HomePage() {
	return (
		<div>
			<Header title="React" />
		</div>
	);
}

function Header(props) {

}  
```

If we use `console.log()` on props, we can see that it is an object with a title property. Since 
props is an object, we can use object destructuring to explicitly name the values of props inside 
your function parameters. We can replace the content of the `<h1>` tag with your title variable. 

```javascript 
function Header({ title }) {
	console.log(title);
	return <h1>title</h1>;
}
```


If this is opened in the browser we see that it displays the actual word title - react thinks that 
we are intending to render a plain text string to the DOM. We need a way to denote to React that 
this a JavaScript variable. 


### Using Variables in JSX

To use the variable defined, we can use curly braces `{}`, a special JSX syntax that allows us to 
write regular JavaScript directly inside of the JSX markup. 

```javascript 
return <h1>{title}</h1>;
```

we can think of curly braces as a way to enter Javascript land when using JSX. Any JavaScript 
expression (that evalues to a single value) can be used inside curly braces. This includes: 

1. An object property with dot notation

```javascript 
function Header(props) {
	return <h1>{props.title}</h1>;
}
```

2. A template literal: 

```javascript 
function Header({ title }) {
	return <h1>{`Cool ${title}`}</h1>;
}
```

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

3. The returned value of a function 

```javascript 
function createTitle(title){
	if (title){
		return titiel; 
	} else {
		return `Default title`;
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}

4. Ternary operators 

```javascript 
function Header({ title }) {
	return <h1>{title ? title : `Default Title`}</h1>;
}
```

You can pass any string to the title prop since we have accounted for the default case in the 
component with the ternary operator. The component now accepts a generic title prop which we can 
reuse in different parts of the application - all we need to do is change the title. 

### Iterating through lists 

It is common to have data that you need to show as a list. You can use array methods to manipulate
your data and generate UI elements that are identical in style but hold different pieces of 
information. 

We can add an array of names to the `HomePage` component and use the `array.map()` method to iterate
over the array and use an arrow function to map a name to a list item: 

```javascript
function HomePage() {
	const names = ['Kung Fu Panda', 'Finding Nemo', 'Lion King'];
	
	return (
		<div> 
			<ul> 
				{names.map((name) => (
					<li key={name}>{name}</li>
				))}
			</ul>
		</div>
	);
}
```


Notice how we use the curly braces to weave in between JavaScript and JSX. Also note that if we do
not pass the key prop - React will give a warning about the missing `key` prop. This is because 
React needs something to uniquely identify items in an array so that it knows which elements to 
update in the DOM. 

We are using names for now since they are currently unique but it is recommended to use something 
guaranteed to be unique such as item ID. Next we look into state and how to listen to user events 
in React.


### Adding Interactivity with State 

Let us explore how React helps us add interactivity with state and event handlers. As an example, 
let's create a like button in the project - start with adding a button element to the code: 


```javascript 
<button>Like</button> 
```

### Listening to Events

To make the button do something when clicked you can make use of the onclick event. In React, event
names are camelCased. The onClick event is one of many possible events you can use to respond to 
user interaction. 


### Handling Events 

We can define a function handle events when they are triggered - for example the following code 
use the handleLick() function to deal with the click event. 

```javascript
function handleClick() {
	console.log('increment like count')
}

return (
	<div> 
		<button onClick={handleClick}>Like</button>
	<div>
);
```

### State and Hooks 

React has a set of functions called hooks - hooks allow you to add additional logic such as state 
to the components. You can think of state as information in the UI that changes over time, usually 
triggered by user interaction. 

We can use state to store and increment the number of times a user has clicked the like button. 
The React hook to manage state is called `useState()`

```javascript 
function HomePage() {
	React.useState();
}
```

`useState()` returns an array and we can access and use those array values inside the component 
using array destructuring: 

```javascript
const [value, update] = React.useState();
```

The first item in the array is the state `value` which we can name anything - it is recommended that
the name be descriptive. 

The second item in the array is a function to update the value. The name can be set to anything but 
it is common to prefix it with `set` followed by the name of the state variable that we are updating. 
For the previous likes example, the complete code could look something like this: 

```javascript
function HomePage() {
	const [likes, setLikes] = useState()
	
	function handleClick() {
		setLikes(likes+1)
	}

	return (
		<div>
			{/* ... */}
			<button onClick={handleClick}>Likes ({likes})</button>
		</div>
	)
} 
```

Clicking the button calls the handleClick function which calls the setLikes state updater function 
with a single argument of the current number of likes+1

> unlike props which are passed to components as the first function parameter, the state is initiated
> and stored within a component. You can pass the state information to children components as props
> but the logic for updating the state should be kept within the component where state was intially 
> created 

### From React to Next.js

While React excels at building UI it does take some work to independently build that UI into a fully
functioning scalable application. Next.js handles muhc of the setup and configuration and has 
additional features to help build React applications. 

So far we have been introduced to three essential React concepts: components, props and state
Having a strong foundation will help to get started building React applications and things to look 
at later would be: 

	* How react handles renders and how to use refs
	* How to manage state 
	* How to use context for deeply nested data
	* How to use React API hooks such as useEffect()


### Getting Started with Next.js

To add Next.js to the project - you will not need to load the react and react-dom scripts from 
unpkg.com anymore. Instead, we install these packages locally using the node package manager.

Jumping back to the index.html file, the next js code does not require the following aspects of 
react code. 

1. The react and react-dom scripts since they have been installed with npm 
2. The html and body tags because Next,js will create them 
3. Code that interacts with the app element and ReactDom.render() method
4. Babel script because Next.js has a compiler that transforms JSX into valid javascript browsers 
   can understand 
5. The script type="text/jsx" tag
6. The React. part of the React.useState(0) function 

 
 ### NextJS 

 To build a complete web application with React from scratch there are many details which need to be considered: 

 * Code needs to be bundled using bundler like webpack and transformed using a compiler like Babel
 * Need to do production optimizations such as code splitting 
 * Might want to statically pre-render some pages for performance and SEO - might also want server-side rendering or client-side rendering 
 * Might need to server-side code to connect the React app to the datastore

 A framework can be used to solve these problems given that they provide the right level of abstraction - this is where next.js comes in. 

Let's get into things and start with learning the basics by creating a simple blog app. 

### Link

The Link component enables client-side navigation between two pages in the same Next.js app. This means that the page transition happens using JavaScript which is faster than the default navigation done by the browser. 

We can see that if we change the color of a page using devtools and navigate between the page transitions - the color change persists. This demonstrates that the browser does not load the full page and client-side navigation is working.


### Code splitting and prefetching 

Next.js does code splitting automatically so each page only loads what is necessary for that page - meaning when homepage is rendered, the code for other pages is not served initially. 

This ensures that the homepage loads quickly even if we have hundreds of pages.

Only loading code for the page requrested also means that pages becomes isolated - if a certain page throws an error, the rest of the application would still work. 

In production build for Next.js - whenever link components appear in the browser's viewport Next.js will automatically prefetch the code for the linked page in the background. This makes page transitions near-instant. 

> If you need to link to an external page - just use an <a> tag without link 

> If we need to add attributes like className - add it to the a tag, not to the Link tag

### Styling

Next.js has built-in support for CSS and Sass - we will be covering the CSS portion for this project.

In addition we will also go over how Next.js handles static assets like images and page metadata like the `<title>` tag. 

NextJS can serve static assets like images under the top-level `public` directory. Files inside `public` can be referenced from the root of the application similar to `pages`. 

The public directory is also useful for robots.text, google site verification and any other static assets. 


If we are using regular HTML, we can add the profile picture as follows: 

```
<img src="/images/profile.jpg" alt="Name">
``` 

Doing so however means that you need to manually handle: 

	* Ensuring the image is responsive on different screen sizes 
	* Optimizing images with a third-party tool or library 
	* Only loading images when they enter the viewport

NextJS provides and `Image` component out of the box to handle this for you. Next.js has support for Image Optimization by default which allows for resizing, optimizing and serving images in modern formats like WebP when the browser supports it. This avoids shipping large images to devices with a smaller viewport. It also allows Next.js to automatically adopt future image formats and serve them to browsers that support those formats. 

Instead of optimizing images at build, Next.js optimizes images on-demand as users request them. Unlike static stie generators the build times are not increased whether shipping 10 images or 10 million images. 

Images are lazy loaded by default so the page speed isn't penalized for images outside the viewport. Images load as they are scrolled into viewport.

### Metadata 

If we wanted to modify the metadata of the page such as the `<title>` html tag, we make sure of the <Head> component. Unlike the lower case <head>, <Head> is a react component built into next js and allows us to modify the <head> of a page. 

### Scripts

In addition to metadata, scripts that need to load and execute as soon as possible are usually added to the <head> of a page. 

`next/script` is an extension of the HTML `<script>` element and optimizes when additional scripts are fetched and executed. 

This component has a few additional properties
	* `strategy` controls when the third-party script should load. A value of `lazyOnload` tells Next.js to load this particular script lazily during browser idle time
	* `onLoad` is used to run any JS code immediately after the script has finished loading. 


### CSS Styling

One of the built in support methods for CSS offered by Next.js is `styled-jsx`. This is a CSS in JS library that allows for writing CSS within a React component and these styles will be scoped (other components will not be affected). 

Another method which is used in this project is CSS Modules which allows us to import CSS files in a React component. In order to use CSS Modules the CSS file name must end with `.module.css`.

```javascript
import styles from './layout.module.css';

export default function Layout({ children }) {
  return <div className={styles.container}>{children}</div>;
}
```

If we take a look at the HTML in the browser's devtools, we will notice that the `div` rendered by the `Layout` component has a class name that looks like `layout_container_...`. 

This is what is being does by css modules - it automatically generates unique class names. As long as we use CSS Modules, we do not need to worry about class name collisions. 

Next.js's code splitting feature works on CSS Modules as well - it ensures the minimal amount of CSS is loaded for each page. This results in smaller bundle sizes.

CSS Modules are useful for component-level styles. If you want some CSS to be loaded by every page, Next.js has support for that as well. 

We make use of the `App` component (in `pages/_app.js`) which is the top level component which will be common across all different pages. We can use this app component to keep state when navigating between pages as well.

Global CSS files can be added by importing them from `pages/_app.js` - we cannot import global CSS anywhere else. 

### Additional Styling Tricks

Classnames is a simple library that allows for toggling classnames easily. For example if we want an alert to be colored differently if it was a success or an error - we can use classnames to toggle the class name while keeping the styling as just 

```css
.success {
	color: green;
}
.error {
	color: red;
}
```


### Data Fetching 

Next we will cover how to fetch external blog data for the app - the blog content will be stored in the file system but will also work if the content is stored elsewhere. 

This will cover: 
	* next.js' pre-rendering feature 
	* two forms of pre-rendering, static generation and server-side rendering
	* static generation with data and without data
	* getStaticProps and how to use it import external data into the index page 


### Pre-rendering 

By default Next.js pre-renders every page - meaning that next.js generates HTML for each page in advance instead of having it all done by client-side JavaScript. Pre-rendering can result in better performance and search engine optimization. 

Each generated HTML is associated with minimal JS code necessary for that page - when a page is loaded by the browser, its JS code runs and makes the page fully interactive (process known as hydration)

There are two forms of pre-rendering offered by Next.js: Static Generation and Server-side Rendering. 

* Static generation is the pre-rendering method that generates the HTML at build time - the pre-rendered html is then reused on each request

* Server-side rendering is the pre-rendering method that generates the HTML on each request


### Per-page Basis

Next.js allows for choosing which pre-rendering form we want to use for each page - we can create a hybrid Next.js app by choosing static generation for most pages and using server-side rendering for others.

Static generation is suggested whenever possible since the page can be built once and served by CDN which makes it faster than having a server render the page for each request

Examples of good pages to use this with include:
	* Marketing pages
	* blog posts
	* e-commerce product listings
	* help and documentation

Static generation is not a good idea if you cannot pre-render a page ahead of the user's request. This would be the case when the page contains frequently updated data and where the page content changes on every request. 

### Static Generation with Data

FOr some pages you might not be able to render the HTML without first fetching some external data - perhaps we need to access the file system, fetch external API, or query the database at build time. 

Next.js supports static generation with data out of the box. This works in Next.js thought the getStaticProps function. When we export a page component, we can also export an async function called getStaticProps. If we do this then:

	* `getStaticProps` runs at build time in production and
	* inside the function we can fetch external data and send it as props to the page 

getStaticProps tells Next.js that this page has some data dependencies so when we pre-render this page at build time - make sure to resolve them first! 

For data in our app we will be using markdown 

```
---
title: 'When to Use Static Generation v.s. Server-side Rendering'
date: '2020-01-02'
---

Example post
```

The metadata section at the top - which in this example contains `title` and `date` - is part of a format called YAML Front Matter which can be parsed using a library called gray-matter. 

### Fetch External API

In our current implementation we used getSortedPostsData to fetch data from the file system - we can also fetch data from other sources like an external API and it will work just fine: 

```javascript
export async function getSortedPostsData() {
	const res = await fetch('..');
	return res.json();
}
```

We can also query the database directly in a method such as below:

```javascript
import someDatabaseSDK from 'someDatabaseSDK'

const databaseClient = someDatabaseSDK.createClient(...)

export async function getSortedPostsData() {
  // Instead of the file system,
  // fetch post data from a database
  return databaseClient.query('SELECT posts...')
}
```

This works because `getStaticProps` only runs on the server-side and will never run on the client-side. This code will also not be included in the JS bundle for the browser. 

In production build the getStaticProps method runs at build time so we will not be able to sue data that is only available during request time such as query parameters or HTTP headers. 

If data needs to be fetched at request time static generation is not a good idea - we should try server-side rendering or skip pre-rendering.

To use server-side rendering, we need to export `getServerSideProps` instead of `getStaticProps` from the page.

Time to first byte will be slower than getStaticProps since the server must compute the result and it cannot be cached by a CDN without extra configuration.

### Dynamic Routes 

Here we will discuss the case where each page path depends on external data - next.js allows us to statically generate pages with paths that depend on external data. This enables dynamic URLs in Next.js and want them for our blog posts. 

To implement this we create a page called `[id].js` - pages that begin with `[` and end with `]` are dynamic routes in Next.js.

### API Routes

Next.js also has support API Routes which allow us to create an API endpoint as a Node.js serverless function (also known as Lambdas). 

A good use case for this would be handling form input. It is possible to create a form on the webpage and have it send a post request to an API route - we can then write code to directly save this data to a database. This API route code will not be part of the client bundle so we can safely write server-side code.