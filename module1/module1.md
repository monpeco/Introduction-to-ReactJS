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

### Using JSX with Empty Tags

If a HTML tag is empty, you can close it with a '/>' instead of using a closing tag.

```javascript
var element = <input className ="nameInput"/>
```

### Using JSX with a Style Object

The style attribute can be populated with a style object instead of a string literal

```javascript
    var styleObject = {
        backgroundColor: 'red',
        color:'blue',
        fontSize: 25,
        width: 100
    }

    var element = <input style = {styleObject}/>
```

In this next example, the first set of curly braces is for the JSX expression while the second set of curly braces is for the style object:

```javascript
var element = <input style = {{width:200,height:100}}/>
```

### Using JSX with Nested Elements

React Elements can be nested within other React Elements as long as the whole thing is wrapped by 
in a single element.

```javascript
var element = (
    <div>
        <div>Hello World</div>
        <div>Hello Another World</div>
    </div>

)
```

This example is not surrounded with a single wrapping element and will throw an error:

```javascript
    var element = (
        <div>Hello World</div>
        <div>Hello World</div>
    )
```

It is recommended to surround nested elements with paranthesis to avoid the problems that occur with automatic semicolon insertion.

### Using JSX Objects

Objects created with JSX can be manipulated just like normal JavaScript objects. They can be passed in arrays, used as arguments or return statements to functions and used inside if statements or for loops.

An example using JSX objects within an If Else statement:

```javascript
   var product = {name:"apple",stock:0}

    if(product.stock > 0){
        var element = <h1>The product named {product.name} is not in stock</h1>
    }
    else{
        var element = <h1>The product named {product.name} and has {product.stock} units in stock</h1>
    }

    ReactDOM.render(
        element,
        document.getElementById("root")
    )
```

---

#### Module 1 | JSX and React Components   JSX   JSX Video

# JSX Video

https://youtu.be/9MJSbG-BpPM

> JSX is a syntax extension that allows us to write HTML tags in our
> JavaScript code. Without JSX, it is much, much more verbose to write
> React elements. So let's take a look at these examples. The first line
> uses JSX. Well, the second one doesn't. And as you can see it's a lot
> more effort. So, that's why JSX is preferred when we want some correct
> React elements. Curly braces allows us to embed JavaScript expressions
> into our JSX code. Let's take a look at example. So, over here we have
> the string variable and we have an item object. We can embed these
> into our HTML tag using curly braces. So, let's start with the string.
> So, by putting the string variable name inside the curly braces, we
> can now see that string has been embedded into our page. So, if we
> want to reference the item.name and item.price you can do so in a
> similar fashion. And as you can see here the item.name and price have
> also been rendered by us using JSX expressions with curly braces. Now
> lastly, we can also use functions in our curly braces. So, for
> example, if we use this calculateArea function that I wrote below, and
> put in some numbers. We can see that functions can also be used in our
> curly braces. You can supply attribute values using a string literal
> surrounded by quotes. You can also supply attribute values by
> embedding a JavaScript expression using curly braces. However, do not
> surround the curly braces with quotes. This will cause the expression
> to be treated as a string literal. And one last thing is that certain
> attributes are named differently in JSX. For example, class in HTML
> becomes className. Multiple React elements can be rendered at the same
> time as long as there is one enclosing element that surrounds all of
> the React elements. So, in this case, we have a div element that
> encloses both the Hello world divs. However, if we got rid of that div
> then it wouldn't work.

Tags: `JSX`, `JavaScript expression`, `className`

---

#### Module 1 | JSX and React Components   Functional Components   Functional Components

# Functional Components

### React Components

A React Component is an independent reusable component that outputs a React Element based on its properties and state.

There are two types of React Components:

* **Functional Components**
* **Class Components**

**Class Components** have state, lifecycle methods, and properties while **Functional Components** only 
have properties. In this module, we will cover Functional Components while Class Components will be 
covered in Module 2.

### Functional Components

Functional Components are just functions that output React Elements. By convention, the first letter 
of the function name should be capitalized.

Here is an example:

```javascript
function HelloWorld(){
    return <h1>Hello World!</h1>
}
```

You can use the React Component in JSX by creating an HTML tag with the same name as the React Component:

```javascript
var element = <HelloWorld/>
```
Another Example:

```javascript
ReactDOM.render(
    <HelloWorld/>,
    document.getElementById("root")
)
```

These examples will all evaluate to the React Element that is returned by the HelloWorld Component.

### Adding Properties to Functional Components

The first argument to a Functional Component is an object that contains the component's properties.

```javascript
function HelloWorld(props){
    return <h1>Message: {props.message}</h1>
}
```
You can supply property values the same way as you supply attribute values:

```javascript
ReactDOM.render(
    <HelloWorld message="Hello World!"/>,
    document.getElementById("root")
)
```
Properties can be string literals, arrays or any other type of JavaScript object including other 
React Elements:

```javascript
function HelloWorld(props){
    return <h1>Value: {props.numberArray[props.index]} </h1>
}

ReactDOM.render(
    <HelloWorld index = "3" numberArray={[1,2,3,4,5]}/>,
    document.getElementById("root")
)
```

You can supply as many property values as you want and they will all be accessible through 
the props argument.

---

#### Module 1 | JSX and React Components   Functional Components   Functional Components Video

# Functional Components Video

https://youtu.be/fB3fTFGR2JA

> A React component is an independent reusable component that returns a
> react element based on its properties and its state. There are two
> types of React components, class components and functional components.
> However, for now we're gonna cover functional components, as its name
> suggests, functional components are written similarly to JavaScript
> functions. Let's write one right now, Over here I am declaring a
> functional components named HelloWorld in this components will return
> a header with Hello World inside it. Now how do we use this functional
> component? Well in our ReactDOM.render function, we can put a tag with
> the functional component's name as the tag name. So in this case, it
> would be a tag with HelloWorld in it. And as we can see, our React
> component is now rendered to the page. Now we can add properties to
> this React component by adding props as an argument. The individual
> properties have to be supplied in a way similar to how attributes are
> declared. So if we have a property called message, you can assign that
> to something like My Message. And then, in our functional component we
> can use the curly brace notation to refer to that property. And as you
> can see here, the message property was supplied and it was, It was
> referenced by the props.message attribute.

Tags: `React component`, `React element`, `class components`, `functional components`

---

#### Module 1 | JSX and React Components   Composition   Composition

### Composing Components

Functional Components can include other Functional Components in their output. This lets us 
keep our components organized and readible.

For example, look at this Shopping Application that makes use of Composition:

```javascript
    function ShoppingTitle(props){
        return (
            <div>
                <h1>{props.title}</h1>
                <h2>Total Number of Items: {props.numItems}</h2>
            </div>

        ) 
    }
    function ListItem(props){
        return <li>{props.item}</li>
    }

    function ShoppingList(props){
        return (
            <div>
                <h3>{props.header}</h3>
                <ol>
                    <ListItem item = {props.items[0]}/>
                    <ListItem item = {props.items[1]}/>
                    <ListItem item = {props.items[2]}/>
                </ol>
            </div>
        )
    }


    function ShoppingApp(props){

        return (
            <div>
                <ShoppingTitle title = "My Shopping List" numItems = "9"/>
                <ShoppingList header = "Food" items = {[ "Apple","Bread","Cheese"]}/>
                <ShoppingList header = "Clothes" items = {[ "Shirt","Pants","Hat"]}/>
                <ShoppingList header = "Supplies" items = {[ "Pen","Paper","Glue"]}/>
            </div>
        )
    }

    ReactDOM.render(
        <ShoppingApp/>,
        document.getElementById("root")
    )
```

Compare that to just defining all the UI in one Functional Component.

```javascript
    function ShoppingApp(props){
        return (
            <div>
                <div>
                    <h1>My Shopping List</h1>
                    <h2>Total Number of Items: 9</h2>
                </div>
                <div>
                    <h3>Food</h3>
                    <ol>
                        <li>Apple</li>
                        <li>Bread</li>
                        <li>Cheese</li>
                    </ol>
                </div>

                <div>
                    <h3>Clothes</h3>
                    <ol>
                        <li>Shirt</li>
                        <li>Pants</li>
                        <li>Hat</li>
                    </ol>
                </div>

                <div>
                    <h3>Supplies</h3>
                    <ol>
                        <li>Pen</li>
                        <li>Paper</li>
                        <li>Glue</li>
                    </ol>
                </div>


            </div>
        )
    }

    ReactDOM.render(
        <ShoppingApp/>,
        document.getElementById("root")
    )
```

---

#### Module 1 | JSX and React Components   Composition   Composition Video

# missing video

---

#### Module 1 | JSX and React Components   Conditional Rendering   Conditional Rendering

# Conditional Rendering

Conditional Rendering

The output of a Functional Component can be determined based on its properties.

For example:

```javascript
function Feature(props){
    if (props.active == true){
        return <h1>This feature is active</h1>
    }
    else{
        return <h1>This feature is not active</h1>
    }

}
```
This can also be accomplished using an inline conditional operator:

```javascript
function Feature(props){
    return <h1>This feature is {props.active? "active" : "not active"}</h1>
}
```

Preventing Rendering

The output of a Functional Component can be prevented from rendering.

```javascript
function Feature(props){
    if(props.active!){
        return null
    }
    else{
        return <h1>{props.message}</h1>
    }
}
```

You can also conditionally prevent a feature from rendering using the && operator:

```javascript
function Feature(props){
    return (
        props.active && <h1>{props.message}</h1>
    )
}
```
With the && operator, true and expression will always evaluate to expression. On the other hand, false and expression will always evaluate to false which won't render.

---

#### Module 1 | JSX and React Components   Conditional Rendering   Conditional Rendering Video

# missing video

---

#### Module 1 | JSX and React Components   Module 1 Tutorial   Module 1 Tutorial

# Module 1 Tutorial

This tutorial is attended to teach you how to model an HTML DOM using React Components.

Link to Codepen Solution:
https://codepen.io/benjlin/pen/MorPNK

We will be converting the following page into a ReactJS application:

![solution](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/72ada07c8af824ce45450868bb69379d/asset-v1:Microsoft+DEV281x+4T2017+type@asset+block/m1tutorial2.PNG)

### Step 1: Break up the UI into components

The first step is to identify parts of the UI that can be broken into their own components.

![step1](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/cc6b28fdc52e17428d37a4ff048b79ec/asset-v1:Microsoft+DEV281x+4T2017+type@asset+block/m1tutorial2divided.png)

As the above image shows, we have broken up the application into several sections:

* A component that contains a title and description of the shopping application (blue)
* A component that contains a header a list of three items (red)
* A component that represents a list items (dark red)

### Step 2: Creating the individual React Components

To start off, we will create a React Component that represents an individual list item. For now, we will 
return a <li> tag with a test string, but later on we will replace it with an attribute passed from the 
component's properties.

```javascript
function ListItem(props){
    return <li>Test String</li>
}
```
We can test the component by rendering it to the page, be sure to add a root div in the HTML page:

```html
<div id="root"> </div>
```

```javascript
ReactDOM.render(
    <ListItem/>,
    document.getElementById("root")
)
```

Next will create a React Component that contains the application's title and description. For now, 
we will return <h1> and <h2> tags that contain test strings, but later on we will replace them with 
attributes passed from the component's properties. We must wrap the headers with <div> tag to ensure 
that there is one element that encompasses all of the returned React Elements. In addition, we must 
surround the returned value with parenthesis since the return value spans several lines.

```javascript
function ShoppingTitle(props){
    return (
        <div>
            <h1>Test Title</h1>
            <h2>Test Description</h2>
        </div>

    ) 
}
```

We can test the component by rendering it to the page:

```javascript
ReactDOM.render(
    <ShoppingTitle/>,
    document.getElementById("root")
)
```

Lastly, we will create the component that contains a header and three ListItem components. For now, 
we will return a <h3> tag with a test string, but later on we will replace it with an attribute passed 
from the component's properties. We must wrap the headers with <div> tag to ensure that there is one 
element that encompasses all of the returned React Elements. In addition, we must surround the 
returned value with parenthesis since the return value spans several lines.

```javascript
function ShoppingList(props){
    return (
        <div>
            <h3>Test Header</h3>
            <ol>
                <ListItem/>
                <ListItem/>
                <ListItem/>
            </ol>
        </div>
    )
}
```

We can test the component by rendering it to the page:

```javascript
ReactDOM.render(
    <ShoppingList/>,
    document.getElementById("root")
)
```

### Step 3: Putting the components together

Now that we have created and tested the individual React Components, we will now encompass them 
under one React Component. The `ShoppingApp` component will contain the `ShoppingTitle` component and 
three `ShoppingList` components.

```javascript
function ShoppingApp(props){

    return (
        <div>
            <ShoppingTitle/>
            <ShoppingList/>
            <ShoppingList/>
            <ShoppingList/>
        </div>
    )
}
```

We can test the application by rendering it to the page:

```javascript
ReactDOM.render(
    <ShoppingApp/>,
    document.getElementById("root")
)
```

### Step 4: Adding in the application data

Now that we have our entire application modeled using React Components, we can now replace our 
test strings with the actual application data.

```javascript
function ShoppingApp(props){

    return (
        <div>
            <ShoppingTitle title = "My Shopping List" numItems = "9"/>
            <ShoppingList header = "Food" items = {[ "Apple","Bread","Cheese"]}/>
            <ShoppingList header = "Clothes" items = {[ "Shirt","Pants","Hat"]}/>
            <ShoppingList header = "Supplies" items = {[ "Pen","Paper","Glue"]}/>
        </div>
    )
}
``` 

In the `ShoppingApp` component, I have added several attributes that contain the application data. I have 
supplied an array of strings to the items attribute of the `ShoppingList` component. The items in the array 
will be passed down to the individual `ListItem` components within the ShoppingList component. The numItems 
attribute on the ShoppingTitle component represents the number of total items in all of the shopping lists. 
This value will be included in the second header of the `ShoppingApp` component.

Now we must edit the `ShoppingList` component to make use of the supplied data. The shopping list headers 
can be accessed through `props.header` and the shopping items can be accessed from their indices from the 
`props.items` array.


```javascript
function ShoppingList(props){
    return (
        <div>
            <h3>{props.header}</h3>
            <ol>
                <ListItem item = {props.items[0]}/>
                <ListItem item = {props.items[1]}/>
                <ListItem item = {props.items[2]}/>
            </ol>
        </div>
    )
}
```

Next, we must edit the ShoppingTitle component to make use of the supplied data. The 
title and number of items can be accessed through props.title and props.numItems 
respectively.

```javascript
function ShoppingTitle(props){
    return (
        <div>
            <h1>{props.title}</h1>
            <h2>Total Number of Items: {props.numItems}</h2>
        </div>

    ) 
}
```

Lastly, we must edit the ListItem component to make use of the supplied data. The 
item name can be accessed through the props.item.

```javascript
function ListItem(props){
    return <li>{props.item}</li>
}
```
Now that we have completed all of the steps, we can test our entire application 
by rendering it to the page:

```javascript
ReactDOM.render(
    <ShoppingApp/>,
    document.getElementById("root")
)
```

---

#### Module 1 | JSX and React Components   Module 1 Lab   Module 1 Lab