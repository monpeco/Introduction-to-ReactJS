#### Module 1 | JSX and React Components   Module 1 Intro   Module 1 Intro Video

# Module 1 Intro Video

https://youtu.be/bhXTULItbZY

> Welcome to Module 1. In this module, we're gonna start off by talking
> about what is ReactJS and why you should use it. Moving forward, we're
> gonna talk about React Elements and how they are the building blocks
> that represent DOM nodes. After that, we're gonna talk about JSX,
> which is a syntax extension that allows you to write HTML code in your
> JavaScript. After that, we're gonna talk about functional components
> which are independent reasonable components that describe how the UI
> should look like based on its state and properties. And lastly, we're
> gonna learn how to arrange functional components to model an
> application in an efficient and clean manner.

Tags: `React Elements`, `JSX`, `functional components`, `composition`

---

#### Module 1 | JSX and React Components   Setting up ReactJS   Setting Up ReactJS

# Setting Up ReactJS

The following steps are used to add ReactJS to an HTML file:

1. Create an HTML file
 
```html
<!DOCTYPE html>
<html>
  <head>
       <meta charset="UTF-8">

 
  </head>
  <body>
  </body>
</html>
```

2. Add scripts to include react.js, react-dom.js and babel.js inside the head of the HTML file

```html

```

3. Add a babel script within the body of the HTML file

```html

```

4. Add <div id="root></div> to the body of the HTML file

```html

```

5. Start rendering elements using ReactJS

```html

```

---

#### Module 1 | JSX and React Components   Setting up ReactJS   Setting up ReactJS in Codepen

# Setting up ReactJS in Codepen

We will be using CodePen to submit our lab assignments in this edX course. Codepen is used so other students can have an easier time viewing and testing your lab submissions. 

![codepen](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/bf09dbc9c52b92e126da5cf4760da08e/asset-v1:Microsoft+DEV281x+4T2017+type@asset+block/codepen.PNG)

[Link to CodePen with ReactJS set up](https://codepen.io/benjlin/pen/EXoMQQ?editors=1010)

The following steps are used to set up ReactJS to work in CodePen:

1. Go to https://codepen.io/pen to open a new project

2. Click Settings

3. Click JavaScript and under JavaScript Preprocessor select Babel

4. Click Quick-add and select React

5. Click Quick-add and select React-DOM (this must be selected after React or your app won't work)

 Once you have completed the above steps, add the following to get started:


```html

<div id="root"></div>

```

```javascript
    ReactDOM.render(

    <div>Hello World</div>,

    document.getElementById("root")

)

```

### My link: 
https://codepen.io/Monpeco/pen/VMzWMN
 
--- 

#### Module 1 | JSX and React Components   What is ReactJS   What is ReactJS?

# What is ReactJS?

ReactJS is a library that generates the view layer of an application based on its state. ReactJS applications are built from React 
Components - independent resusable components that describe how the UI should look based on their own state and properties.

### Why should I use ReactJS?

* ReactJS applications are incredibly performant at UI rerendering
* React Components make writing UI components easier
* What makes ReactJS so efficient at rerendering?

React Components are used to generate a Virtual DOM - a light-weight abstraction of the actual HTML DOM. 
The Virtual DOM is able to be generated much more quickly than the HTML DOM because it does not have to 
calculate CSS styles and layouts. When a React Component changes state, the Virtual DOM is recreated and 
the difference between the new Virtual DOM and the previous Virtual DOM is calculated. The ReactJS library 
then calculates the most efficient way to update the HTML DOM to reflect these changes. This ends up being 
much faster than regenerating the entire HTML DOM from the top.

![virtual DOM](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/78967a0e9538885041c75b2dfe5dd2ca/asset-v1:Microsoft+DEV281x+4T2017+type@asset+block/virtualDOM.gif)

### How hard is it to use ReactJS?

ReactJS is a relatively lightweight library and it does not take a whole lot of code to get started with it.

Here is an example of the code needed for a Hello World application:

```html
   <div id="root"></div>
```

```javascript
ReactDOM.render(
    <h1>Hello World!</h1>,
    document.getElementById("root")
)
```

---

#### Module 1 | JSX and React Components   What is ReactJS   What is ReactJS Video

# What is ReactJS Video

https://youtu.be/mJMsHKoLzFY

> ReactJS is a library that generates the view layer of an application
> based on its state. ReactJS applications are built from React
> Components, independent reusable components that describe how the UI
> should look based on their State and their Properties. So, why should
> you use ReactJS? Well, ReactJS applications are incredibly performant
> at UI rendering, and also, React components make writing UI components
> easy. So, what makes ReactJS so efficient at rerendering? Well, React
> components are used to generate a virtual DOM, a lightweight
> abstraction of the actual HTML DOM. The virtual DOM is able to be
> generated much more quickly than the HTML DOM because it does not have
> to do a bunch of calculations with the CSS styles and the layout. When
> a React component changes state, the virtual DOM is recreated, and the
> difference between the old virtual DOM and the new virtual DOM is
> calculated. The ReactJS library then calculates the most efficient way
> to update the HTML DOM and changes only what is necessary for the view
> to be updated. This ends up being much faster than just rewriting the
> HTML DOM from the top. So, how hard is it to use ReactJS? ReactJS is
> actually a relatively lightweight library and does not take a whole
> lot of code to get started. So, if you're ready to begin, let's
> continue on and learn how to write a ReactJS application.

---

#### Module 1 | JSX and React Components   Rendering Elements   Rendering Elements

# React Elements

**React Elements** are objects that represent a DOM node. They are written using a syntax extension named JSX which we will cover 
later in this module. **React Elements are different than React Components**, which we will also cover later in this module.

```javascript
var element = <h1>Hello World!</h1>
```
React Elements need to be rendered by the `ReactDOM.render()` method to appear in the DOM.

# ReactDOM.render()

The **ReactDOM.render()** method is used to render a React Element into a specified part of the HTML DOM. In most React applications, 
there is usually a single root node where everything gets rendered into, but you may use as many root nodes as you desire.

In this case, the `<h1>Hello World!</h1>` React Element is rendered into the DOM element with the id of "root".

```html
<div id="root"></div>
```

```javascript
ReactDOM.render(
    <h1>Hello World!</h1>,
    document.getElementById("root")
)
```

### Rerendering the DOM using additional render() calls

Once a DOM is rendered, it will remain the same until another `render()` method is called.

The following example uses additional `render()` calls to update the displayed number:

```javascript
var num = 0;

function updateNum(){

    ReactDOM.render(
        <div>{num++}</div>,
        document.getElementById("root")
    )
}

setInterval(updateNum,100)
```

---

#### Module 1 | JSX and React Components   Rendering Elements   Rendering Elements Video

Rendering Elements Video

https://youtu.be/xz2euIClwgo

> React elements are the building blocks of react JS applications. A
> react element is an object that represents a DomNode. React elements
> are written using JSX which is a JavaScript extension, that allows us
> to write HTML tags in our JavaScript code. So let's take a look at
> what that looks like. As you can see here in the code, I've written an
> HTML tag with, Hello World, inside it. And I define that to the
> element variable. This is something that JSX allows us to do. Now that
> we've created our react element, how do we render it to the page?
> Well, if we first look at HTML we'll see that we have a single div
> element within id of roots. We can target this div and embed our react
> element inside of it. And we can do that with the ReactDom.render
> method. Let me show you how that works. The ReactDom.render method
> takes in two arguments. The first being the element that we're trying
> to render, and the second being the target. So, if we target that root
> element we saw earlier and we embed our react element, we can see that
> Hello World is now rendered to the page. So once a DOM is rendered it
> will remain the same until another ReactDOM.render method is called.
> So, if we happen to change this element variable, the page would not
> re-render. We will have to recall another render method.

Tags: `Re act Element`, `JSX`, `ReactDOM.render()`

---

#### Module 1 | JSX and React Components   JSX   JSX

# JSX

### What is JSX?

JSX is a syntax extension to JavaScript that allows React Elements to be written inside JavaScript using HTML tags.

Using JSX, we can create React Elements easily with HTML Tags:

```javascript
var element = <h1>Hello World!</h1>
```

Without JSX, the process is much slower and more verbose:

```javascript
var element = React.createElement(
    'h1',
    null,
    'Hello World!'
)
```

### Using JSX with JavaScript Expressions

Curly braces can be used to embed JavaScript expressions into JSX.

The following are all examples of valid JavaScript expressions in JSX:

```javascript
var str = "World!" 

var element =  <h1> Hello {str}</h1>
```

```javascript
var item = {
    name: "Cheese",
    price: 5
}
var element
t = <p>{item.name} : ${item.price} </p>
```

```javascript
var length = 20
var width = 10

function calculateArea(x,y){
    return x * y
}

var element = <div>The Area is: {calculateArea(length,width)}</div>
```

### Using JSX with Attributes

You can supply attribute values using a string literal surrounded by quotes:

```javascript
var element = <button className ="deleteButton"> Delete </button>
```
You can also supply attributes values by embedding a JavaScript expression using curly braces:

```javascript
var element = <img src ={product.imageURL}></img>
```
Do not surround curly braces with quotes. This will cause your expression to be treated as a string literal:
```javascript
//Do not do this
var element = <img src ="{product.imageURL}"></img>
```
Some common HTML attributes are named differently in JSX. For example `class` becomes `className` 
because `class` is a reserved keyword in JavaScript. Furthermore, attribute names in JSX follow the 
camelCase naming convention so an HTML attribute such as `fontsize` would become `fontSize` in JSX.
