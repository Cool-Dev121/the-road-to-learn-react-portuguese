# Introduction to React

The chapter gives you an introduction to React. You may ask yourself: Why should I learn React in the first place? The chapter might give you the answer to that question. Afterward you will dive into the ecosystem by bootstrapping your first React application. Along the way you will get an introduction to JSX and ReactDOM. Be prepared for your first React component.

## Hi, my name is React.

**Why should you bother to learn React?** In recent years single page applications ([SPA](https://en.wikipedia.org/wiki/Single-page_application)) have become popular. Frameworks like Angular, Ember and Backbone helped JavaScript developers to build modern web applications beyond the usage of jQuery. The list is not exhaustive. There exists a wide range of SPA frameworks. When you consider the release dates, most of them are among the first generation of SPAs: Angular 2010, Backbone 2010, Ember 2011.

The initial React release was 2013 by Facebook. React is not an SPA framework but a view library. It is the V in the [MVC](https://de.wikipedia.org/wiki/Model_View_Controller) (model view controller). It only enables you to render components as viewable elements in a browser. Yet the whole ecosystem around React makes it possible to build single page applications.

But why should you consider using React over the first generation of SPA frameworks? While the first generation of frameworks tried to solve a lot of things at once, React only helps you to build your view layer. It's a library and not a framework. The idea behind it: Your view is a hierarchy of composable components.

In React you can focus on your view before you introduce more aspects to your application. Every other aspect is another building block for your SPA. These building blocks are essential to build a mature application. They come with two advantages.

First you can learn the building blocks step by step. You don't have to worry about understanding them altogether. It is different from a framework that gives you every building block from the start. This book focuses on React as the first building block. More building blocks follow eventually.

Second all building blocks are interchangeable. It makes the ecosystem around React such an innovative place. Multiple solutions are competing with each other. You can pick the most appealing solution for you and your use case.

The first generation of SPA frameworks arrived at an enterprise level. They are more rigid. React stays innovative and gets adopted by multiple tech thought leader companies like [Airbnb, Netflix and of course Facebook](https://github.com/facebook/react/wiki/Sites-Using-React). All of them invest in the future of React and are content with React and the ecosystem itself.

React is probably one of the best choices for building single page applications nowadays. It only delivers the view layer, but the React ecosystem is a whole flexible and interchangeable framework. React has a slim API, an amazing ecosystem and a great community. You can read about my experiences [why I moved from Angular to React](https://www.robinwieruch.de/reasons-why-i-moved-from-angular-to-react/). I highly recommend to have an understanding why you would choose React over another framework or library. After all everyone is keen to experience where React will lead us in 2017 and beyond.

### Exercises

* read about [why I moved from Angular to React](https://www.robinwieruch.de/reasons-why-i-moved-from-angular-to-react/)

## Requirements

Before you start to read the book, you should be familiar with HTML, CSS and JavaScript (ES5). The book will teach JavaScript ES6 and beyond. If you are coming from a different SPA framework or library, you should already be familiar with the basics. If you have just started in web development, you should feel comfortable with HTML, CSS and JavaScript ES5 to learn React.

Every developer needs tools to build applications. You will need an editor (IDE) and terminal (command line) tool. You can read my developer setup to organize your tools: [Developer Setup](https://www.robinwieruch.de/developer-setup/). It is adjusted for Mac users, but you can substitute most of the tools for other operating system.

The editor is used to organize and write your code. The terminal is used to execute commands. A command can be to start your application, to run tests or to install other libraries for your project.

Last but not least you will need an installation of [node and npm](https://nodejs.org/en/). Both are used to manage libraries you will need along the way to learn React. You will install external node packages via npm (node package manager). These node packages can be libraries or whole frameworks.

You can verify your versions of node and npm on the command line. If you don't get any output in the terminal, you need to install node and npm first. These are my versions:

{title="Command Line",lang="text"}
~~~~~~~~
node --version
*v7.4.0
npm --version
*v4.0.5
~~~~~~~~

## node and npm

This chapter gives you a little crash course in node and npm. It is not exhaustive, but you will get all the necessary tools. If you are familiar with both of them, you can skip the chapter.

The **node package manager** (npm) allows you to install external **node packages** from the command line. These packages can be a set of utility functions, libraries or whole frameworks. They are the dependencies of your application. You can either install these packages to your global node package folder or to your local project folder.

Global node packages are accessible from everywhere in the terminal and you have to install them only once. You can install a global package by typing in your terminal:

{title="Command Line",lang="text"}
~~~~~~~~
npm install -g <package>
~~~~~~~~

The `-g` flag tells npm to install the package globally. Local packages are used in your application. For instance, React as a library will be a local package which can be required in your application for usage. You can install it via the terminal by typing:

{title="Command Line",lang="text"}
~~~~~~~~
npm install <package>
~~~~~~~~

In the case of React it would be:

{title="Command Line",lang="text"}
~~~~~~~~
npm install react
~~~~~~~~

The installed package will automatically appear in a folder called *node_modules/*. But be careful. Whenever you install a local package you shouldn't forget the neat `--save` flag:

{title="Command Line",lang="text"}
~~~~~~~~
npm install --save <package>
~~~~~~~~

The `--save` flag tells npm to store the package requirement in a file called *package.json*. The file can be found in your project folder.

Not every project folder comes with a *package.json* file though. There is a npm command to initialize a npm project and thus a *package.json* file. Only when you have that file, you can install new local packages via npm.

{title="Command Line",lang="text"}
~~~~~~~~
npm init -y
~~~~~~~~

The `-y` flag is a shortcut to initialize all the defaults in your *package.json*. If you don't use it, you have to decide how to configure the file.

One more word about the *package.json*. The file enables you to share your project with other developers without sharing all the node packages. The file has all the references of node packages used in your project. These packages are called dependencies. Everyone can copy your project without the dependencies. The dependencies are references in the *package.json*. Someone who copies your project can install all packages by using `npm install` on the command line.

I want to cover one more npm command to prevent confusion:

{title="Command Line",lang="text"}
~~~~~~~~
npm install --save-dev <package>
~~~~~~~~

The `--save-dev` flag indicates that the node package is only used in the development environment. It will not be used in production when you deploy your application on a server. What kind of node package could that be? Imagine you want to test your application with the help of a node package. You need to install that package via npm, but want to exclude it from your production environment. There you don't want to test your application anymore. It should be tested already and work out of the box for users. That's only one use case where you would want to use the `--save-dev` flag.

You will encounter more npm commands on your way. But these will be sufficient for now.

### Exercises:

* setup a throw away npm project
  * create a new folder with `mkdir <folder_name>`
  * navigate into the folder with `cd <folder_name>`
  * execute `npm init -y`
  * install a local package like React with `npm install --save react`
  * have a look into the *package.json* file and the *node_modules/* folder
  * find out how to uninstall the *react* node package
* read more about [npm](https://docs.npmjs.com/)

## Installation

There are multiple approaches to get started with a React application.

The first one is to use a CDN. That may sound more complicated than it is. A CDN is a [content delivery network](https://en.wikipedia.org/wiki/Content_delivery_network). Several companies have CDNs that host files publicly for users. These files can be libraries like React. After all a library can be only one JavaScript file. It can be hosted somewhere and you can require it in your application.

How to use a CDN to get started in React? You can inline the `<script>` tag in your HTML that points to a CDN url. To get started in React you need two files (libraries): *react* and *react-dom*.

{title="Code Playground",lang="javascript"}
~~~~~~~~
<script src="https://unpkg.com/react@15/dist/react.js"></script>
<script src="https://unpkg.com/react-dom@15/dist/react-dom.js"></script>
~~~~~~~~

But why should you use a CDN when you have npm to install node packages (libraries)?

When your application has a *package.json* file, you can install *react* and *react-dom* from the command line. The requirement is that the folder is initialized as npm project with a *package.json* file. You can install multiple node packages in one line with npm.

{title="Command Line",lang="text"}
~~~~~~~~
npm install --save react react-dom
~~~~~~~~

That approach is often used to add React to an existing application.

Unfortunately that's not everything. You would have to deal with [Babel](http://babeljs.io/) to make your application aware of JSX - the React syntax - and JavaScript ES6. Babel transpiles your code that browsers can interpret ES6 and JSX. Not all browsers are capable of interpreting the syntax. The setup includes a lot of configuration and tooling. It can be overwhelming for React beginners to bother with all the configuration.

Because of this reason, Facebook introduced *create-react-app* as a zero-configuration React solution. The next chapter will show you how to setup your application.

### Exercises:

* read more about [React installations](https://facebook.github.io/react/docs/installation.html)

## Zero-Configuration Setup

In the Road to learn React you will use [create-react-app](https://github.com/facebookincubator/create-react-app) to bootstrap your application. It's an opinionated yet zero-configuration starter kit for React introduced by Facebook in 2016. People would [recommend it to beginners by 96%](https://twitter.com/dan_abramov/status/806985854099062785). In *create-react-app* the tooling and configuration evolve in the background while the focus is on the application implementation.

To get started, you will have to install the package to your global node packages. After that you always have it available on the command line to bootstrap new React applications.

{title="Command Line",lang="text"}
~~~~~~~~
npm install -g create-react-app
~~~~~~~~

You can check the version of *create-react-app* to verify a successful installation on your command line:

{title="Command Line",lang="text"}
~~~~~~~~
create-react-app --version
~~~~~~~~

It should give you an output about the version.

Now you can bootstrap your first React application. We call it *hackernews*, but you can choose a different name. Afterward simply navigate into the folder:

{title="Command Line",lang="text"}
~~~~~~~~
create-react-app hackernews
cd hackernews
~~~~~~~~

Now you can open the application in your editor. The following folder structure should be presented to you:

{title="Folder Structure",lang="text"}
~~~~~~~~
hackernews/
  README.md
  node_modules/
  package.json
  .gitignore
  public/
    favicon.ico
    index.html
  src/
    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
~~~~~~~~

In the beginning everything you need is located in the *src/* folder.

The main focus lies on the *src/App.js* file to implement React components. It will be used to implement your application, but later you might want to split up your components into multiple files.

Additionally you will find a *src/App.test.js* file for tests and a *src/index.js* as entry point to the React world. You will get to know both files in a later chapter. In addition, there is a *src/index.css* and a *src/App.css* file to style your application and components. They all come with default style when you open them.

Next to to the *src/* folder you will find the *package.json* file and *node_modules/* folder to manage your node packages. The *create-react-app* application is a npm project. You can use npm to install and uninstall node packages to your project.

The *create-react-app* project comes with the following npm scripts for your command line:

{title="Command Line",lang="text"}
~~~~~~~~
// Runs the application in http://localhost:3000
npm start

// Runs the tests
npm test

// Builds the application for production
npm run build
~~~~~~~~

The scripts are defined in your *package.json* too. Your boilerplate React application is bootstrapped now.

### Exercises:

* `npm start` your application and visit the page in your browser
* run the interactive `npm test` script
* make yourself familiar with the folder structure
* make yourself familiar with the content of the files
* read more about [the scripts and create-react-app](https://github.com/facebookincubator/create-react-app)

## Introduction to JSX

Now you will get to know JSX. It is the syntax in React. As I mentioned before, *create-react-app* has already bootstrapped a boilerplate application. All files come with default implementations. Let's dive into the source code.

The only file you will touch in the beginning will be the *src/App.js* file.

{title="src/App.js",lang=javascript}
~~~~~~~~
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

class App extends Component {
  render() {
    return (
      <div className="App">
        <div className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <h2>Welcome to React</h2>
        </div>
        <p className="App-intro">
          To get started, edit <code>src/App.js</code> and save to reload.
        </p>
      </div>
    );
  }
}

export default App;
~~~~~~~~

Don't let yourself get confused by the import/export statements and class declaration. These features are already JavaScript ES6. We will revisit those in a later chapter.

In the file you have an **ES6 class component** with the name App. It is a component declaration. Basically after you have declared a component, you can use it as element everywhere in your application. It will produce an **instance** of your **component** or in other words: the component gets instantiated.

The **element** it returns is specified in the `render()` method. Elements are what components are made of. It is useful to understand the differences between component, instance and element.

Pretty soon you will see where the App component is used. Otherwise you wouldn't see the rendered output in the browser, would you? The App component is only the declaration, but not the usage. You would instantiate the component somewhere in your JSX with `<App />`.

The content in the render block looks pretty similar to HTML, but it's JSX. JSX allows you to mix HTML and JavaScript. It's powerful yet confusing when you are used to plain HTML. That's why a good starting point is to use basic HTML in your JSX. Next you can start to embed JavaScript expressions in between by using curly braces.

First let's remove all the clutter in the file.

{title="src/App.js",lang=javascript}
~~~~~~~~
import React, { Component } from 'react';
import './App.css';

class App extends Component {
  render() {
    return (
      <div className="App">
        <h2>Welcome to React</h2>
      </div>
    );
  }
}

export default App;
~~~~~~~~

Now you only return HTML without JavaScript. Let's make the "Welcome to React" a variable. A variable can be used in your JSX.

{title="src/App.js",lang=javascript}
~~~~~~~~
import React, { Component } from 'react';
import './App.css';

class App extends Component {
  render() {
# leanpub-start-insert
    var helloWorld = 'Welcome to React';
# leanpub-end-insert
    return (
      <div className="App">
# leanpub-start-insert
        <h2>{helloWorld}</h2>
# leanpub-end-insert
      </div>
    );
  }
}

export default App;
~~~~~~~~

It should work when you start your application on the command line.

Additionally you might have noticed the `className` attribute. It reflects the standard `class` attribute in HTML. Because of technical reasons, JSX had to replace a handful of internal HTML attributes. You can find all of the [supported HTML attributes in the React documentation](https://facebook.github.io/react/docs/dom-elements.html). On your way to learn React you will come across some more JSX attributes.

### Exercises:

* define more variables and render them in your JSX
  * use a complex object to represent an user with a first name and last name
* read more about [JSX](https://facebook.github.io/react/docs/introducing-jsx.html)
* read more about [React components, elements and instances](https://facebook.github.io/react/blog/2015/12/18/react-components-elements-and-instances.html)

## ES6 const and let

I guess you noticed that we declared the variable `helloWorld` with `var`. JavaScript ES6 comes with two more options to declare your variables: `const` and `let`. In JavaScript ES6 you will rarely find `var` anymore. Let's get some explanation for `const` and `let`:

A variable declared with `const` cannot be re-assigned or re-declared. It cannot get mutated (changed, modified). You embrace immutable data structures by using it. Once the data structure is defined, you cannot change it.

{title="Code Playground",lang="javascript"}
~~~~~~~~
// not allowed
const helloWorld = 'Welcome to React';
helloWorld = 'Bye Bye React';
~~~~~~~~

A variable declared with `let` can get mutated.

{title="Code Playground",lang="javascript"}
~~~~~~~~
// allowed
let helloWorld = 'Welcome to React';
helloWorld = 'Bye Bye React';
~~~~~~~~

You would use it when you would need to re-assign a variable.

However, you have to be careful with `const`. A variable declared with `const` cannot get modified. But when the variable is an array or object, the value it holds can get altered. The value it holds is not immutable.

{title="Code Playground",lang="javascript"}
~~~~~~~~
// allowed
const helloWorld = {
  text: 'Welcome to React'
};
helloWorld.text = 'Bye Bye React';
~~~~~~~~

But when to use each declaration? There are different opinions about the usage. I suggest to use `const` whenever you can. It indicates that you want to keep your data structure immutable even though values in objects and arrays can get modified. If you want to modify your variable, you can use `let`.

Immutability is embraced in React and its ecosystem. That's why `const` should be your default choice when you define a variable. Still, in complex objects the values within can get modified. Be careful about this behavior.

In your application you should use `const` over `var`.

{title="src/App.js",lang=javascript}
~~~~~~~~
import React, { Component } from 'react';
import './App.css';

class App extends Component {
  render() {
# leanpub-start-insert
    const helloWorld = 'Welcome to React';
# leanpub-end-insert
    return (
      <div className="App">
        <h2>{helloWorld}</h2>
      </div>
    );
  }
}

export default App;
~~~~~~~~

### Exercises:

* read more about ES6 [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)
* read more about ES6 [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
* research more about immutable data structures
  * why do they make sense in programming in general
  * why are they used in React and its ecosystem

## ReactDOM

Before you continue with the App component, you might want to see where it is used. It is located in your entry point to the React world: the *src/index.js* file.

{title="src/index.js",lang=javascript}
~~~~~~~~
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import './index.css';

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
~~~~~~~~

Basically `ReactDOM.render()` uses a DOM node in your HTML to replace it with your JSX. That's how you can easily integrate React in every foreign application. It is not forbidden to use `ReactDOM.render()` multiple times across your application. You can use it at multiple places to bootstrap simple JSX syntax, a React component, multiple React components or a whole application.

`ReactDOM.render()` expects two arguments.

The first argument is JSX that gets rendered. The second argument specifies the place where the React application hooks into your HTML. It expects an element with an `id='root'`. You can open your *public/index.html* file to find the id attribute.

In the implementation `ReactDOM.render()` already takes your App component. However, it would be fine to pass simpler JSX as long as it is JSX. It doesn't have to be an instantiation of a component.

{title="Code Playground",lang=javascript}
~~~~~~~~
ReactDOM.render(
  <h1>Hello React World</h1>,
  document.getElementById('root')
);
~~~~~~~~

### Exercises:

* open the *public/index.html* to see where the React applications hooks into your HTML
* read more about [rendering elements in React](https://facebook.github.io/react/docs/rendering-elements.html)

## Hot Module Reloading

There is one thing that you can do in the *src/index.js* file to improve your experience as a developer.

In *create-react-app* it is already an advantage that the browser automatically refreshes the page when you change your source code. Try it by changing the `helloWorld` variable in your *src/App.js* file. The browser should refresh the page. But you can do better.

Hot Module Reloading (HMR) is a tool to reload your application in the browser. The browser doesn't perform a page refresh. You can easily activate it in *create-react-app*. In your *src/index.js* - your entry point to React - you have to add one little configuration.

{title="src/index.js",lang=javascript}
~~~~~~~~
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import './index.css';

ReactDOM.render(
  <App />,
  document.getElementById('root')
);

# leanpub-start-insert
if (module.hot) {
  module.hot.accept()
}
# leanpub-end-insert
~~~~~~~~

That's it. Try again to change the `hellowWorld` variable in your *src/App.js* file. The browser shouldn't perform a page refresh, but the application reloads and shows the correct output.

HMR comes with multiple advantages.

Imagine you are debugging your code with `console.log()` statements. These statements will stay in your developer console, even though you change your code, because the browser doesn't refresh the page anymore. That can be convenient for debugging purposes.

In a growing application a page refresh delays your productivity. You have to wait until the page loads. A page reload can take several seconds in a large application. HMR takes away this disadvantage.

The biggest benefit is that you can keep the application state with HMR. Imagine you have a dialog in your application with multiple steps and you are at step 3. Basically it is a wizard. Without HMR you would change the source code and your browser refreshes the page. You would have to open the dialog again and would have to navigate from step 1 to step 3. With HMR your dialog stays open at step 3. It keeps the application state even though the source code changes. The application itself reloads, but not the page.

### Exercises:

* change your *src/App.js* source code a few times to see HMR in action
* watch the first 10 minutes of [Live React: Hot Reloading with Time Travel](https://www.youtube.com/watch?v=xsSnOQynTHs) by Dan Abramov

## Complex JavaScript in JSX

Let's get back to your App component. So far you rendered some primitive variables in your JSX. Now you will start to render a list of items. The list will be artificial data in the beginning, but later you will fetch the data from an external API. That will be far more exciting.

First you have to define the list of items.

{title="src/App.js",lang=javascript}
~~~~~~~~
import React, { Component } from 'react';
import './App.css';

# leanpub-start-insert
const list = [
  {
    title: 'React',
    url: 'https://facebook.github.io/react/',
    author: 'Jordan Walke',
    num_comments: 3,
    points: 4,
    objectID: 0,
  },
  {
    title: 'Redux',
    url: 'https://github.com/reactjs/redux',
    author: 'Dan Abramov, Andrew Clark',
    num_comments: 2,
    points: 5,
    objectID: 1,
  },
];
# leanpub-end-insert

class App extends Component {
  ...
}
~~~~~~~~

The artifical data will reflect the data we will fetch later on from the API. An item in the list has a title, an url and a author. Additionally it comes with an identifier, points (which indicate how popular an article is) and a count of comments.

Now you can use the built-in JavaScript `map` functionality in your JSX. It enables you to iterate over your list of items to display them. As mentioned, you will use curly braces to encapsulate the JavaScript expression in your JSX.

{title="src/App.js",lang=javascript}
~~~~~~~~
class App extends Component {

  render() {
    return (
      <div className="App">
# leanpub-start-insert
        { list.map(function(item) {
          return <div>{item.title}</div>;
        })}
# leanpub-end-insert
      </div>
    );
  }
}

export default App;
~~~~~~~~

That's pretty powerful in JSX. Usually you might have used `map` to convert one list of items to another list of items. This time you use `map` to convert a list of items to HTML elements.

So far, only the `title` will be displayed for each item. But let's display some more of the item properties.

{title="src/App.js",lang=javascript}
~~~~~~~~
class App extends Component {

  render() {
    return (
      <div className="App">
# leanpub-start-insert
        { list.map(function(item) {
          return (
            <div>
              <span>
                <a href={item.url}>{item.title}</a>
              </span>
              <span>{item.author}</span>
              <span>{item.num_comments}</span>
              <span>{item.points}</span>
            </div>
          );
        })}
# leanpub-end-insert
      </div>
    );
  }
}

export default App;
~~~~~~~~

You can see how the map function is simply inlined in your JSX. Each item property is displayed in a `<span>` tag. Moreover the url property of the item is used in the `href` attribute of the anchor tag.

React will do all the work for you and display each item. But you should add one helper for React to embrace its full potential and improve its performance. You have to assign a key attribute to each list element. Only that way React is able to identify added, changed and removed items when the list changes. The artificial list items come with an identifier already.

{title="src/App.js",lang=javascript}
~~~~~~~~
{ list.map(function(item) {
  return (
# leanpub-start-insert
    <div key={item.objectID}>
# leanpub-end-insert
      <span>
        <a href={item.url}>{item.title}</a>
      </span>
      <span>{item.author}</span>
      <span>{item.num_comments}</span>
      <span>{item.points}</span>
    </div>
  );
})}
~~~~~~~~

You should make sure that the key attribute is a stable identifier. Don't make the mistake of using the item index in the array. The array index isn't stable at all. For instance, when the list changes its order, React will have a hard time identifying the items properly.

{title="src/App.js",lang=javascript}
~~~~~~~~
// don't do this
{ list.map(function(item, key) {
  return (
    <div key={key}>
      ...
    </div>
  );
})}
~~~~~~~~

You are displaying both list items now. You can start your app, open your browser and see both items of the list displayed.

### Exercises:

* read more about [React lists and keys](https://facebook.github.io/react/docs/lists-and-keys.html)
* recap the [standard built-in Array functionalities in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
* use more JavaScript expressions on your own in JSX

## ES6 Arrow Functions

JavaScript ES6 introduced arrow functions. An arrow function expression is shorter than a function expression.

{title="Code Playground",lang="javascript"}
~~~~~~~~
// function expression
function () { ... }

// arrow function expression
() => { ... }
~~~~~~~~

But you have to be aware of its functionalities. One of them is a different behavior with the `this` object. A function expression always defines its own `this` object. Arrow function expressions still have the `this` object of the enclosing context. Don't get confused when using `this` in an arrow function.

There is another valuable fact about arrow functions regarding the parenthesis. You can remove the parenthesis when the function gets only one argument, but have to keep them when it gets multiple arguments.

{title="Code Playground",lang="javascript"}
~~~~~~~~
// allowed
item => { ... }

// allowed
(item) => { ... }

// not allowed
item, key => { ... }

// allowed
(item, key) => { ... }
~~~~~~~~

However, let's have a look at the `map` function. You can write it more concisely with an ES6 arrow function.

{title="src/App.js",lang=javascript}
~~~~~~~~
# leanpub-start-insert
{ list.map(item => {
# leanpub-end-insert
  return (
    <div key={item.objectID}>
      <span>
        <a href={item.url}>{item.title}</a>
      </span>
      <span>{item.author}</span>
      <span>{item.num_comments}</span>
      <span>{item.points}</span>
    </div>
  );
})}
~~~~~~~~

Additionally you can remove the *block body* of the ES6 arrow function. In a *concise body* an implicit return is attached thus you can remove the return statement. That will happen more often in the book, so be sure to understand the difference between a block body and a concise body.

{title="src/App.js",lang=javascript}
~~~~~~~~
# leanpub-start-insert
{ list.map(item =>
# leanpub-end-insert
  <div key={item.objectID}>
    <span>
      <a href={item.url}>{item.title}</a>
    </span>
    <span>{item.author}</span>
    <span>{item.num_comments}</span>
    <span>{item.points}</span>
  </div>
# leanpub-start-insert
)}
# leanpub-end-insert
~~~~~~~~

Your JSX looks more concise and readable now. It omits the function statement, the curly braces and the return statement.

### Exercises:

* read more about [ES6 arrow functions](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

## ES6 Classes

JavaScript ES6 introduced classes. A class is commonly used in object-oriented programming languages. JavaScript was and is very flexible in its programming paradigms. You can do functional programming and object-oriented programming side by side for their particular use cases.

Even though React embraces functional programming, for instance with immutable data structures, classes are used to declare components. They are called ES6 class components. React mixes the good parts of both programming paradigms.

Let's consider the following Developer class to examine a JavaScript ES6 class without thinking about a component.

{title="Code Playground",lang="javascript"}
~~~~~~~~
class Developer {
  constructor(firstname, lastname) {
    this.firstname = firstname;
    this.lastname = lastname;
  }

  getName() {
    return this.firstname + ' ' + this.lastname;
  }
}
~~~~~~~~

A class has a constructor to make it instantiable. The constructor can take arguments to assign it to the class instance. Additionally a class can define functions. Because the function is associated with a class, it is called a method. Sometimes it is referenced as class method.

The Developer class is only the class declaration. You can create multiple instances of the class by invoking it. It is similar to the ES6 class component, that has a declaration, but you have to use it somewhere else to instantiate it.

Let's see how you can instantiate the class and how you can use its methods.

{title="Code Playground",lang="javascript"}
~~~~~~~~
const robin = new Developer('Robin', 'Wieruch');
console.log(robin.getName());
// output: Robin Wieruch
~~~~~~~~

React uses JavaScript ES6 classes for ES6 class components. You already used one ES6 class component.

{title="src/App.js",lang=javascript}
~~~~~~~~
import React, { Component } from 'react';

...

class App extends Component {
  render() {
    ...
  }
}
~~~~~~~~

The App class extends from `Component`. Basically you declare the App component, but it extends from another component. What does extend mean? In object-oriented programming you have the principle of inheritance. It is used to pass over functionalities from one class to another class.

The App class extends functionality from the Component class. To be more specific, it inherits functionalities from the Component class. The Component is used to extend a basic ES6 class to a ES6 component class. It has all the functionalities a component needs to have. One of these functionalities, a method, you have already used: the `render()` method. But you will learn about more functionalities.

The `Component` class encapsulates all the React functionalities that a developer doesn't need to see. It enables developers to use classes as components in React.

The methods a React `Component` exposes is the public interface. One of these methods has to be overwritten, the others don't need to be overwritten. You will learn about the latter ones when the book arrives at lifecycle methods in a later chapter. The `render()` method has to be overwritten, because it defines the output of a React `Component`.

Now you know the basics around JavaScript ES6 classes and how they are used in React to extend them to components. As I said, you will learn more about the Component methods when the book describes React lifecycle methods.

### Exercises:

* read more about [ES6 classes](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Classes)

{pagebreak}

You have learned to bootstrap your own React application! Let's recap the last chapters:

* React
  * create-react-app bootstraps a React application
  * JSX mixes up HTML and JavaScript to define React components
  * components, instances and elements are different things
  * ReactDOM.render() is an entry point for a React application
  * built-in JavaScript functionalities can be used in JSX
    * map can be used to render a list of items as HTML elements
* ES6
  * variable declarations with const and let for particular use cases
  * arrow functions can be used to shorten your function declarations
  * classes are used to define components in React

It makes sense to take a break at this point. Internalize the learnings and apply them on your own. You can experiment with the source code you have written so far.

You can find the source code in the [official repository](https://github.com/rwieruch/hackernews-client/tree/0c5a701170dcc72fe68bdd594df3a6522f58fbb3).
