#### Module 2 | State, Life Cycle, and Event Handlers   Module 2 Intro   Module 2 Intro Video

# Module 2 Intro Video

https://youtu.be/sbJTI9NEcF8

> Welcome to module 2. Module 2 is about class components, state, life
> cycle methods, and event handlers. In this module, we're gonna talk
> about how to create a class component, how to set its initial state
> and then update it. And then we're gonna talk about the life cycle
> methods that a class component will go through. Moving forward, we're
> gonna talk about how do add event handlers to class components. And
> then lastly we're gonna talk about how to make class components update
> the state of other class components.

Tags: `class components`, `state`, `life cycle methods`, `event handlers`

---

#### Module 2 | State, Life Cycle, and Event Handlers   Class Components   Class Components

# Class Components

In addition to being written as a function, React Components can also be written using **ES6 classes**. 
**Class Components** differ from **Functional Components** because they allow React Components to have 
**life cycle methods** and **state**. Class components have two instance properties, `this.state` 
and `this.props`, that represent the component's state and properties respectively.

**Class Components have 2 instance properties: this.state and this.props**

React Component written using ES6 classes:
```javascript
class Welcome extends React.Component{
    render(){
        return <h1>Hello World!</h1>
    }
}
```

This is the same as the following Functional Component:

```javascript
function Welcome(){
    return <h1>Hello World!</h1>
}
```

Both types of React Components can be used by writing their name within an HTML tag:
```javascript
var element = <Welcome/>
```

### The Render() method

The **render()** method of a class component is used to describe what kind of React Element is 
going to be returned from the Class Component. It the same as the return value of of a Functional Component.

For example, the following Class Component will render<h1>Hello World!</h1>:
```html
<div id="root"></div>
```

```javascript
class Welcome extends React.Component{
    render(){
        return <h1>Hello World!</h1>
    }
} 

//renders <h1>Hello World!</h1>
ReactDOM.render(
    <Welcome/>,
    document.getElementById("root")
)
```

### Adding properties to Class Components

The properties of a Class Component can be accessed through the `this.props` attribute. This differs 
slightly from Functional Components where the properties were passed in as a variable.

```javascript
class Welcome extends React.Component{
    render(){
        return <h1>Message: {this.props.message}</h1>
    }
}
```

You can supply property values the same way as you supply attribute values:

```javascript
<Welcome message="Hello World!"/>
```

---

#### Module 2 | State, Life Cycle, and Event Handlers   Class Components   Class Components Video

# Class Components Video

https://youtu.be/jXeaQaWwufo

> In addition to being written as a function, React component can also
> be written using ES6 classes. These are called class components, the
> difference between a class component and a React functional component
> is that class components can have state and life cycle methods. Let's
> take a look at these two React components, they output the same thing,
> but one is written as a class component, while the other one is a
> functional component. So if we take a look at the class component, we
> will notice this render method. The render of a class component is
> used to describe what kind of React element the class will output. Now
> what if we wanna add a property to this class components? Well, we can
> do it in a similar way to how we did with functional components. So
> first we describe the property by naming it, so if we have a property
> called message and we set that equal to class component, we can then
> address it by referencing this.props.message. And there we have it,
> class component is now rendered to the page. And one thing to remember
> is that you have to do this.props.message whereas before with
> functional components you only had to do props.message.

Tags: `ES6 classes`, `Class Component`, `render`, `properties`, `this.props.message`

**The difference between a class component and a functional component is that class components 
can have state and life cycle methods**

#### Module 2 | State, Life Cycle, and Event Handlers   State   State

# State

### Constructor(props)

The `constructor()` method is called before a React Component is mounted and is used to set up the initial state of the component. 
It is important to call `super(props)` at the beginning of the `constructor()` method or else the `this.props` attribute may not 
work correctly. The first argument to the `constructor()` method represents the properties that are passed into the component.

```javascript
class Counter extends React.Component{
    constructor(props){
        super(props)
    }
    render(){
        return <div>Hello World!</div>
    }
}
```

# Adding an initial state to Class Components

The initial state of a Class Component can be declared within the `constructor()` method. The state of the 
component must be declared as an object with attributes.

```javascript
class Counter extends React.Component{
    constructor(props){
        super(props)
        this.state = {foo:123,bar:456}
    }
    render(){
        return <div>foo:{this.state.foo} bar:{this.state.bar}</div>
    }
}
```

### Updating state

The `setState(updater,[callback])` method is used to update the state of the component. It takes in an updater 
object and updates the component state by shallowly merging the updater object's attributes with the previous 
component state. The method updates the state asynchronously, so a there is an option callback that will be 
called once the state has finished updating completely. In order to use the `setState() method`, it must be 
referenced by calling `this.setState()`.

The `setState` method will trigger the updating phase of the component lifecycle to start. This will cause the 
component to rerender unless the `shouldComponentUpdate()` function returns false.

```javascript
this.setState({message:"new message"})
```

### Updating state based on previous state

The `setState()` method does not immediately update the state of the component, it just puts the update in a 
queue to be processed later. React may batch multiple update requests together to make rendering more efficient. 
Due to this, special precautions must be made when you try to update the state based on the component's 
previous state. Due to this, precautions must be made when updating the state based on previous state values.

For example, the following code will only increment the state value attribute by 1 even though it was called 4 
times:

```javascript
class Counter extends React.Component{
    constructor(props){
        super(props)
        //initial state set up
        this.state = {value:0}
    }
    componentDidMount(){
        //updating state
        this.setState({value:this.state.value+1})
        this.setState({value:this.state.value+1})
        this.setState({value:this.state.value+1})
        this.setState({value:this.state.value+1})
    }
    render(){
        return <div>Message:{this.state.message}</div>
    }
}
```

The `setState(updater,[callback])` method can take in an updater function as its first argument to update the 
state based on the previous state and properties. The return value of the updater function will be shallowly 
merged with the previous component state. The method updates the state asynchronously, so a there is an option 
callback that will be called once the state has finished updating completely.

Example:
```javascript
this.setState((prevState, props) => {
    return {attribute: "value"}
})
```

Here is an example of how to update the state based on previous state:

```javascript
class Counter extends React.Component{
    constructor(props){
        super(props)
        //initial state set up
        this.state = {message:"initial message"}
    }
    componentDidMount()
        //updating state
        this.setState((prevState, props) => {
            return {message: prevState.message + '!'}
        })
    }
    render(){
        return <div>Message:{this.state.message}</div>
    }
```

### Using future state values

Since state updates asynchronously, you can not just expect the state values to update immediately after a 
`setState()` method call.

For example, the console log may not output the updated state:
```javascript
//this.state.count is originally 0
this.setState({count:42})
console.log(this.state.count)
//outputs 0 still
```
In order to use a state after it has been updated, do all logic in the callback argument:

```javascript
//this.state.count is originally 0
this.setState({count:42}, () = {
    console.log(this.state.count)
    //outputs 42
})
```
### State is not mutable

State is read only so you should not try to manually change the values of the state attributes. If the state needs to be updated, the setState() method is the only way to change the state.

For example, don't do this:

```javascript
//incorrect, state should not be mutated directly
this.state.message = "new message"
```

---

#### Module 2 | State, Life Cycle, and Event Handlers   State   State Video

State Video

https://youtu.be/BY_DhPf4_0E

> The constructor method is called right before a component is mounted
> and is used to setup the initial state of the components. If we look
> at our constructor method in our class components we can see it has a
> props argument and super props is called right at the beginning. It is
> important to always do this steps If you do not do these steps, and
> you try to reference a property of the class components, the
> properties will not render correctly. So if you're gonna use
> properties, you must provide props as an argument, and the do super
> props. So after calling super props we can now set our initial state.
> So the initial state is set by setting the, this.state value to equal
> an object and then you can provide this object with the values you
> want your state to have. So let's have a value attribute and set it to
> zero. Now we can reference the value attribute by typing
> this.state.value. And now we can see that this is rendered to the
> page. So what if we wanna update the state? Well, we have this other
> method called component in mount and this is called immediately after
> the constructor method is called. So we're just using this as an
> example of updating the state sometime in the future. So to update the
> state, we have this method called this dot set state. And this dot set
> state takes in an object and does a shallow merge of that object with
> the pre-existing state. So let's merge it with an object that says
> value and the value will be this.state.valueplus 1. So this will
> basically increment the previous states value attribute by one. And as
> you can see, it was rendered and is now 1. So one thing to note is
> that setState does not happen immediately. It is actually asynchronous
> and you can't really determine when it's gonna finish. So if you do
> something like console.log this.state.value immediately below, it
> might now work the way you expect. You would expect it log 1 because
> we just incremented the state. However, if we look at the console, we
> could see that it is 0. This is because after we called the
> this.setState and then we reached the console.log the value may not
> have been incremented yet since setState was asynchronous. Now if they
> want to do like this and do something with the future value of a state
> we can use the call back method that is the second argument of the
> setState function, so let's do something here. So let's make a
> callback that does the same thing. It logs the save value. As we can
> see here, it logged 1 to the console. Because the value was
> incremented and then the callback was called and then it logged new
> value of the states. So if you ever want to do something with a future
> value, you have to do it in the callback. Now another thing to note is
> that if you wanted to do something with a previous state value and
> then you have to do it in a special way. For example, if we want to
> increment the state four times, we would expect this to work, but it
> actually doesn't. And as you can see the page still displays one even
> though we incremented it at four times. If we want to If you want to
> update the state based on a previous state value we have to do it a
> bit differently. So we can do it like this, we can provide another
> call back as the first argument and it will have the previous state
> and the props as arguments to this call back. And then we can return
> an object that will be shallowly merged with the previous existing
> state. So if we do, and then we can provide it a new value. So over
> here we merged it with the prevState.value + 1. Now if we call this
> multiple times. It will actually work. And as you can see the page now
> renders four. Now, the last thing to know when updating state is to
> never mutate the state directly. That means do not try to set
> this.state.value to equal some new value, it just won't work.

---

#### Module 2 | State, Life Cycle, and Event Handlers   Life Cycle Methods   Life Cycle Methods

# Life Cycle Methods

Each Class Component goes through a component life cycle with multiple phases. There are several 
life cycle methods that can be overridden to run code at different parts of the life cycle.

### Mounting Phase Methods

The mounting phase begins when an instance of a component is created and rendered into the DOM. 
The following lifecycle methods occur in the order they are listed:

* **constructor(props)** - called when the component is first initialized. This method is only called once.
* **componentWillMount()** - called when a component is about to mount.
* **render()** - called when a component is rendered.
* **componentDidMount()** - called when a component has finished mounting. This is where network requests are usually made.


### Updating Phase Methods

The updating phase begins when a component's properties or state changes. The following lifecycle 
methods occur in the order they are listed:

* **componentWillReceiveProps(nextProps)** - called when a component has updated and is receiving new props.
* **shouldComponentUpdate(nextProps, nextState)** - called after receiving props and is about to update. If this method returns false, **componentWillUpdate()**, **render()**, and **componentDidUpdate()** will not execute.
* **componentWillUpdate(nextProps, nextState)** - called when a component is about to be updated.
* **render()** - called when a component is rerendered.
* **componentDidUpdate(prevProps, prevState)** - called when a component has finished updating.

### Unmounting Phase Methods

The unmounting phase begins when a component is being removed from the DOM. The following life cycle method occurs during the 
unmounting phase:

* **componentWillUnmount()** - called when a component has been unmounted. This is where any cleanups are 
made such as cancelling timers or network requests.

---

#### Module 2 | State, Life Cycle, and Event Handlers   Life Cycle Methods   Life Cycle Methods Video

# Life Cycle Methods Video

https://youtu.be/W7rAGd1XBH4

> Each class component goes through a component life cycle with multiple
> phases. There are several life cycle methods that can be overwritten
> to run code at different parts of the life cycle. The first phase is
> the mounting phase. The mounting phase begins when an instance of a
> component is created and rendered to the DOM. The following life cycle
> methods happen in the order I'm going to mention. The first is the
> constructor, and this is called when the component is first initiated
> and it's only called once. The next one is componentWillMount. After
> that is the render method, where the component is actually rendered to
> the page. And after that is componentDidMount which happens
> immediately after the render method. The next phase is the updating
> phase. The updating phase occurs when a component state changes and
> the component has to read the render itself. The first life cycle
> method that occurs is componentsWillReceiveProps. After that there is
> the shouldComponentUpdate life cycle method. After that is the
> componentWillUpdate. And after that is the render method where the
> component is actually re-rendered. And lastly, there is the component
> did update, which happens immediately after it has been rendered. The
> last phase is the unmounting phase which occurs when a component is
> being unmounted from the DOM. And there's only one life cycle method
> they are called componentWillUnmount.

---

#### Module 2 | State, Life Cycle, and Event Handlers   Event Handlers   Event Handlers

# Adding Event Handlers

Handling events in React is similar to handling events in HTML. To attach an event handler to a React Element, assign the event 
handler method to the appropriate event attribute.

Here are the main differences:

* One main difference in React is that **you can use JSX brackets to specify the event handler function** instead of declaring it as a string.

* The next difference is that **React events are named using camelCase** instead of being all lowercase. For example, `onclick` and `onkeypress` in HTML become `onClick` and `onKeyPress` in React respectively.

Click event in **React**:

```javascript
<button onClick = {clickHandler} >Click Me</button>
```

Click event in HTML:

```html
<button onclick = "clickHandler()" >Click Me</button>
```

### Binding Event Handlers to Class Components

Event handlers can be defined as methods within a class Component.

In this example, the `clickHandler` method is defined within the Class Component and is assigned to the `onClick` attribute of 
the `<button>` element. The component renders a button that increments the number displayed inside it whenever it is clicked.

```javascript
class Counter extends React.Component{
    constructor(props){
        super(props)
        this.state = {count:0}
        //binding is necessary to make `this` point to the correct object
        this.clickHandler = this.clickHandler.bind(this)
    }
    clickHandler(){
      //increments the count of the state
      this.setState((prevState,props) => {
        return {count: prevState.count + 1}
      })
    }
    render(){
        //renders a button that displays the state count
        return <button onClick = {this.clickHandler}>{this.state.count}</button>
    }
}

ReactDOM.render(
  <Counter/>,
  document.getElementById("root")
)
```

The `bind()` method is used to bind the `clickHandler()` method's this keyword to the component instance. Without binding 
the function, the function will have its this keyword point to an incorrect object and the `setState()` method will not work correctly.

Binding example:

```javascript
this.clickHandler = this.clickHandler.bind(this)
```

An alternative to using `bind()` is to attach the event handler to the React Element using an **ES6 arrow function**. 
The arrow function will automatically have its this keyword point to the enclosing scope which happens to be the component instance.

Fat arrow example:

```javascript
<button onClick = {{ () => this.clickHandler()}}>{this.state.count}</button>
```
---

#### Module 2 | State, Life Cycle, and Event Handlers   Event Handlers   Event Handlers Video

# Event Handlers Video

https://youtu.be/Z2fI-5qyRtA

> Hello, in this example, we're going to be creating a button, and when
> we click that button, the value inside that button is going to
> increment by one. This is to show you how to tie event handlers to
> your React components. So let's start. So first, we're going to define
> our class component, and let's call it counter. And it's going to
> extend React.component. And next we're going to define our render
> method. And we're going to return, button. And inside that button
> let's do the state value and then have a count attribute that keeps
> track of how many times this button has been pressed. So, next, let's
> define our constructor. And let's put in the props and then do
> super(props). So now let's set our initial state. So in our initial
> state, the count is gonna be zero. So this.state = {count: 0}. Next,
> let's make an event handler called clickHandler. And inside this event
> handler we're going to increment that state count attribute by 1. So
> this.setState and provide an object to merge with a count attribute of
> this.state.count + 1. So let's click it and see if anything works. It
> doesn't work. Well that's because we have to do a couple more things
> in order for this to work. First we have to bind our event handler to
> our class component. Otherwise, the this part of this.setState won't
> know what it's referring to. So to bind it we do this.clickHandler =
> this.clickHandler.bind(this). This will make sure that whenever we
> call the clickHandler wherever it may be, it will always have its this
> referenced to the counter class component. So next we need to pass
> this clickHandler to the button. So there's an onClick attribute and
> we can pass in this.clickHandler. And now if we click it, it works. We
> press the button and the button value increments by 1.

---

#### Module 2 | State, Life Cycle, and Event Handlers   Lifting State Up   Lifting State Up

# Lifting State Up

The `setState()` method only allows components to update their own state. However, there are times when an 
event occurs on a component and the event handler needs to update the state of another sibling or parent 
component. In this situation, we need to lift the state up to a parent component that encapuslates all of 
the components that need updating. The parent component will then pass down binded event handlers to the child 
components. When the child components call the binded event handlers, the parent component will update its 
state and may pass the updated state down to child components that may need it.

To demonstrate this concept we will build the following application:

[Link to Codepen Solution](https://codepen.io/benjlin/pen/OmaLqE)

The application has four buttons and a description section below the buttons. The buttons initially all have 
blue text and are all inactive. The last button that is pressed is considered the active button and its text 
becomes red. Lastly, the description section shows the name of the active button.

We can create a Button, Details, and App Class Component to model the application:

```javascript
class Details extends React.Component{
  render(){
    return <h1>{this.props.details}</h1>
  }
}
class Button extends React.Component{
    render(){
        return (
          <button>
            {this.props.name}
          </button>
        )
    }
}

class App extends React.Component{
    render(){
        return (
            <div>
                <Button name="One"/>
                <Button name="Two"/>
                <Button name="Three"/>
                <Button name="Four"/>
                <Details/>
            </div>
        )
    }
}
```

This application demonstrates the need for lifting the state up because when a Button component is pressed, it needs 
to tell its sibling `Button` components to become inactive and it needs to tell the Details section to change its text. 
Thus, all of the state should be held in the `App` Class Component and binded event handlers should be passed down to 
the child components.

Let's add some event handlers and state to the `App` Class Component: To accomplish this we will add a `constructor()` 
method to the App component so we can initialize its state. We will then declare an event handler named `clickHandler` 
and bind it to the App component. We will also pass down the event handlers down to the `Button` components. We will 
add an id property to each of the Button components so we can identify which `Button` we are pressing later on. The 
event handler will take in the id and name of the `Button` component that is clicked and will update the active Array 
and details section accordingly.


```javascript
class App extends React.Component{
    constructor(props){
        super(props)
        this.state = {activeArray:[0,0,0,0], details:""}
        this.clickHandler = this.clickHandler.bind(this)
    }

    clickHandler(id,details){
        var arr = [0,0,0,0]
        arr[id] = 1
        this.setState({activeArray:arr,details:details})
        console.log(id,details)
    }
    render(){
        return (
            <div>
                <Button id = {0} active = {this.state.activeArray[0]} clickHandler = {this.clickHandler} name="bob"/>
                <Button id = {1} active = {this.state.activeArray[1]} clickHandler = {this.clickHandler} name="joe"/>
                <Button id = {2} active = {this.state.activeArray[2]} clickHandler = {this.clickHandler} name="tree"/>
                <Button id = {3} active = {this.state.activeArray[3]} clickHandler = {this.clickHandler} name="four"/>
                <Details/>
            </div>


        )
    }
}
```
Next, we will edit the Button component. We will change its text color based on whether or not the button is active 
and we will define its onClick attribute based on the event handler that was passed down.

```javascript
class Button extends React.Component{
    render(){
        return (
          <button style = {{color: this.props.active? 'red': 'blue'}} onClick={() => {this.props.clickHandler(this.props.id,this.props.name)}}>
            {this.props.name}
          </button>
        )
    }
}
```

In the end, it should look like this:

```javascript
class Details extends React.Component{
  render(){
    return <h1>{this.props.details}</h1>
  }
}
class Button extends React.Component{
    render(){
        return (
          <button style = {{color: this.props.active? 'red': 'blue'}} onClick={() => {this.props.clickHandler(this.props.id,this.props.name)}}>
            {this.props.name}
          </button>
        )
    }
}
class App extends React.Component{
    constructor(props){
        super(props)
        this.state = {activeArray:[0,0,0,0], details:""}
        this.clickHandler = this.clickHandler.bind(this)
    }
    clickHandler(id,details){
        var arr = [0,0,0,0]
        arr[id] = 1
        this.setState({activeArray:arr,details:details})
        console.log(id,details)
    }
    render(){
        return (
            <div>
                <Button id = {0} active = {this.state.activeArray[0]} clickHandler = {this.clickHandler} name="bob"/>
                <Button id = {1} active = {this.state.activeArray[1]} clickHandler = {this.clickHandler} name="joe"/>
                <Button id = {2} active = {this.state.activeArray[2]} clickHandler = {this.clickHandler} name="tree"/>
                <Button id = {3} active = {this.state.activeArray[3]} clickHandler = {this.clickHandler} name="four"/>
                <Details details = {this.state.details}/>
            </div>


        )
    }
}



ReactDOM.render(
  <App/>,
  document.getElementById("root")
)
```

#### Module 2 | State, Life Cycle, and Event Handlers   Module 2 Tutorial   Module 2 Tutorial

# Module 2 Tutorial

This tutorial will teach you how to create a Connect 4 game.

[Demo of Game/Solution](https://codepen.io/benjlin/pen/WOZwbV?editors=1011)

### Step 1: Breaking up the application into components

![Step 1](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/82487af4ed13153694e25f172134ada3/asset-v1:Microsoft+DEV281x+4T2017+type@asset+block/m2tutorial1divided.png)

As the above image shows, we have broken up the application into several sections:

* A component that represents a circle (lime green)
* A component that represents a grid cell (dark red)
* A component that represents a row of cells (teal)
* A component that represents the game board (red)
* A section that displays the game messages (blue)
* A section with a restart button ( green)

### Step 2: Creating the individual components

To start off lets create a component that represents the circle that will be put 
inside each grid cell. We can accomplish this by returning a `<div>` tag with 
some styling to make it into a circle.

```javascript
function Circle(props){
    var style = {
        backgroundColor:"white",
        border: "1px solid black",
        borderRadius: "100%",
        paddingTop: "98%"
    }
    return (
       <div style = {style}></div>
    )
}
```
We can test the component by rendering it to the page, be sure to add a root div in the HTML page:

```html
<div id="root"></div>
```

```javascript
ReactDOM.render(
    <Circle/>,
    document.getElementById('root')
)
```

Next, we can create a component that represents the grid cells that make up the 
game board. We can add some styling to make it into a square and we can embed 
the Circle component inside of it.

```javascript
function Cell(props){
    var style = {
        height:50,
        width:50,
        border:"1px solid black",
        backgroundColor:"yellow"
    }

    return (
        <div style = {style}>
            <Circle/>
        </div>
    )
}
```

We can test the component by rendering it to the page:

```javascript
ReactDOM.render(
    <Cell/>,
    document.getElementById('root')
)
```

Next, we can create a component that represents a row of grid cells. We can use a for loop to push 7 cells 
into an array that we will insert in a <div> tag. We can add some styling to make the grid cells align horizontally.

```javascript
function Row(props){
    var style = {
          display: "flex"
    }
    var cells = []
    for(let i = 0; i < 7; i++){
        cells.push(<Cell/>)
    }
    return (
        <div style = {style}>
            {cells}
        </div>
    )
}
```

We can test the component by rendering it to the page:

```javascript
ReactDOM.render(
    <Row/>,
    document.getElementById('root')
)
```

Next, we can create a component that represents the game board. We can use a for loop to push 6 rows into 
an array that we will insert in a `<div>` tag.

```javascript
function Board(props){
    var rows = []
    for(let i = 5; i >= 0; i--){
        rows.push(<Row/>)
    }
    return (
        <div>
            {rows}
        </div>
    )
}
```

We can test the component by rendering it to the page:

```javascript
ReactDOM.render(
    <Board/>,
    document.getElementById('root')
)
```

Lastly, we will create a `Game` component that encompasses all of the other components. In addition to the `Board` component, 
we will add a header for the game messages and a restart button to this component. The header and restart button are simple 
enough that we do not need to make them into their own components. The `Game` component will hold all of the application's state 
so we must make it a class component.

```javascript
class Game extends React.Component{
    constructor(props){
        super(props)
    }
    render(){
        return (
            <div>
                <h1>Blacks Turn</h1>
                <Board/>
                <button>Restart</button>
            </div>
        )
    }
}
```

We can test the component by rendering it to the page:

```javascript
ReactDOM.render(
    <Game/>,
    document.getElementById('root')
)
```

### Step 3: Adding game state

The next step is to add state to the `Game` component. The state should keep track 
of everything the game needs to know to function.

The state should keep track of the following:

* Which player's turn it is (true for black, false for red)
* Which grid cell's have pieces and what color those pieces should be (0 for empty, 1 for black, 2 for red)
* Which player has won ( 0 for no one, 1 for black, 2 for red)

The empty grid can be represented by a 2-D array. The 2-D array consists of an array 
that has 6 indexes that each have 7 indexes.

Set the initial state in the constructor.


```javascript
var cells = []
for(let i = 0; i < 6; i++ ){
    cells.push(new Array(7).fill(0))
}

this.state = {player:false, cells:cells, winner:0}
```

### Step 4: Passing State down

The next step is to pass down the cell states all the way down to the individual grid cells. We 
also need to pass down a click event handler down to the grid cells. Once this is accomplished, 
we will implement the basic functionality to change a cell circle's color when it is clicked.

First, add a handleClick() method to the `Game` component:

```javascript
    handleClick(){
        console.log("clicked")
    }
```

Also be sure to bind handleClick to the `Game` component in the constructor:

```javascript
    this.handleClick = this.handleClick.bind(this)
```

Next, pass in the `handleClick` method and the `this.state.cells` attribute into the `Board` component. 
Also, pass in the click event handler.

```javascript
    <Board cells = {this.state.cells} handleClick = {this.handleClick}/>
```

Next, pass in the arrays of length 7 from the `this.state.cells` 2-D array to the `Row` components. Also 
pass in the click event handler.

```javascript
    rows.push(<Row key = {i} row = {i} cells = {props.cells[i]} handleClick = {props.handleClick}/>)
```

Next, pass in the individual cell states to the `Cell` components. Also pass in the click event handler.

```javascript
    cells.push(<Cell key = {i} cell = {props.cells[i]} row = {props.row} col = {i} handleClick = {props.handleClick}/>)
```

Next, pass in the event handler to the `onClick` attribute of the `<div>` tag in the Cell component. 
Also pass in the cell state to the `Circle` component.

```javascript
    <div style = {style} onClick = {() => props.handleClick(props.row,props.col)}>
        <Circle cell = {props.cell}/>
    </div>
```

Next, update the `Circle` component to change its color based on the cell state. If the cell 
state is 1 or 2 the circle will change to be black or red respectively.

```javascript
function Circle(props){
    var color = "white"
    if(props.cell == 1){
        color = "black"
    }
    else if(props.cell == 2){
        color = "red"
    }
    var style = {
        backgroundColor:color,
        border: "1px solid black",
        borderRadius: "100%",
        paddingTop: "98%"
    }
    return (
       <div style = {style}></div>
    )
}
```

If you open up the console and click a cell on the grid, you can see that "clicked" will be output to the console log.

Next, modify the `handleClick` method a bit to get a more detailed idea of which cell is 
being clicked.

```javascript
handleClick(row,col){
	console.log("row: " + row + " | col: " + col)
}
```

Now when a cell is clicked, the console log will display the row and column of the cell that is clicked.

Now lets modify the handleClick method further to update the state of the cells when they are clicked. 
The `slice()` method is used to generate a shallow copy of the inner arrays of the 2-D cells array. 
These shallow copies are then used to build a new 2-D array named temp. The selected row and column 
of the new 2-D array is modified and then the cells state is updated to equal the temp 2-D array.

```javascript
handleClick(row,col){
	console.log("row: " + row + " | col: " + col)
	console.log(this.state.cells)
	var temp = [];
	for(let i = 0; i < 6; i++){
	  temp.push(this.state.cells[i].slice())
	}
	temp[row][col] = 1;
	this.setState({cells:temp})
}
```

If you click on a grid cell now, the corresponding grid circle will now turn black. When a grid cell is 
clicked, it calls the `handleClick()` method which updates the cells state attribute. The state is then 
passed down until it reaches the Circle component and the circle updates its color to reflect the cell 
state.

### Step 5: Adding functionality to alternate player

The next step is to switch the player everytime a new piece is dropped. The pieces should also alternate 
colors based on the player that dropped them.

First, edit the `handleClick` method to alternate the player state everytime a piece is dropped.

```javascript
this.setState({cells:temp, player: !this.state.player})
```

Also, set the value of the `temp` state cell to equal **1** if `this.player.state` is `true` and **2** 
if it is `false`.

```javascript
temp[row][col] = this.state.player? 1 : 2
```

Next, edit the `<h1>` tag in the `Game` component to output whose turn it is based on the player state attribute.

```javascript
<h1>{this.state.player? "Blacks Turn" : "Red Turn"}</h1>
```

Now if you click on a grid cell, the player state will alternate.

The message at the top will display which player's turn it is and the pieces dropped will have their 
color set based on the player that dropped them.


### Step 6: Adding functionality to force pieces to drop all the way down

The next step is to force pieces to drop all the way down until they are on top of another piece or 
on the bottom row.

To help us accomplish this, we will create a function called `findAvailable(col)` that will let us know 
which row a piece should be placed in when it is dropped in a specific column.

The `findAvailableRow(col)` method loops through the cells state attribute and checks all of the 
cells in a specified column. It starts at the bottom of the column and checks each grid cell to see 
if a piece has been placed there. If a grid cell is empty, the method will return the row of that cell. 
Otherwise, it will return -1.

```javascript
findAvailableRow(col){
for(var i = 0; i < 6; i++){
  if(this.state.cells[i][col] == 0){
	return i;
  } 
}
return -1;
}
```

Next, we will modify the `handleClick` method to update the temp state cell 2-D array based on the 
row returned by `findAvailableRow`.

```javascript
var newRow = this.findAvailableRow(col)
temp[newRow][col] = this.state.player? 1 : 2
```

Now if you test the application, the pieces should drop all the way down.

### Step 7: Adding victory detection

The next step is to add a way to detect if a player has won.

Add in these methods that help determine whether there are 4 pieces in a row:

```javascript
checkDiagonal(row,col){
	//find right and left tops
	var c = this.state.cells;
	var val = this.state.player? 2:1;
	var rR = row;
	var cR = col;
	while(rR < 5 && cR < 6){
		rR++; 
		cR++;
	}

	while( rR >= 3 && cR >= 3){
		if(c[rR][cR] == val && c[rR-1][cR-1] == val && c[rR-2][cR-2] == val && c[rR-3][cR-3] == val){
			return 1
		}
		rR--
		cR--
	}   

	var rL = row;
	var cL = col;

	while(rL < 5 && cL > 0){
		rL++
		cL--
	}

	while(rL >= 3 && cL <= 3){
		if(c[rL][cL] == val && c[rL-1][cL+1] == val && c[rL-2][cL+2] == val && c[rL-3][cL+3] == val){
			return 1
		}
		rL--
		cL++
	}
	return 0
}
checkHorizontal(row,col){
	var c = this.state.cells;
	var i = 6;
	var val = this.state.player? 2:1;

	while( i >= 3){
		if(c[row][i] == val && c[row][i-1] == val && c[row][i-2] == val && c[row][i-3] == val){
			return 1
		}
		i--
	}
	return 0
}
checkVertical(row,col){
	var c = this.state.cells;
	var i = row;
	var val = this.state.player? 2: 1;

	if(i >= 3){
		if(c[i][col] == val && c[i - 1][col] == val && c[i - 2][col] == val && c[i - 3][col] == val){
			return 1
	}
	}
	return 0

}
checkVictory(row,col){
	return this.checkVertical(row,col)   || this.checkHorizontal(row,col) ||   this.checkDiagonal(row,col)


}
```
Also, add this to the top of the `handleClick` method to stop the game once someone has won.

```javascript
if(this.state.winner)
    return
```

Lastly, edit the `<h1>` tag to display the winner if the game has ended.

```javascript
<h1>{this.state.winner > 0 ?  this.state.winner == 1? "Black Wins":"Red Wins": this.state.player? "Blacks Turn" : "Reds Turn"} </h1>
```

The game should now display the winner of the game and stop the game if someone wins.

### Step 8: Adding reset functionality

The last step is to make the **Restart** button restart the game.

First, create a method called `restart()` within the `Game` component. This method will 
reset the cells, winner and player state attributes.

```javascript
restart(){
    var cells = [];
    for(let i = 0; i < 6; i++ ){
      cells.push(new Array(7).fill(0));
    }
    this.setState({ player : false, cells : cells, winner:0})
}
```

Next, edit the button element's `onClick` attribute to call the `restart()` method.

```javascript
<button onClick = { () => this.restart()}>Restart</button>
```

Pressing the restart button should now restart the game.

---

#### Module 2 | State, Life Cycle, and Event Handlers   Module 2 Lab   Module 2 Lab

# Module 2 Lab

The assignment for this module is to build a trivia application.

![Image of Lab 2](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/ea73b30595280982493fae08daaa81e7/asset-v1:Microsoft+DEV281x+4T2017+type@asset+block/m2lab1.png)

### Visual Elements

The user should see the following visual elements:

* A section where the question is displayed
* A section where the answer choices are displayed as buttons
* A section that shows the number of correct answers
* A section that shows the number of incorrect answers

### Functional Elements

The user should be able to do the following:

* When the user clicks on an answer choice, the number of correct/incorrect answers should update based on whether the answer is correct or not.
* When the user clicks on an answer choice, the next question and set of answers will be displayed
* The user should be able to go through at least 10 questions

### Module 2 Lab Submission Guidelines

Please create a codepen containing your solution and post a link to your codepen in the discussions forums. 
Codepen is used so other students can have an easier time viewing and testing your application. A link to 
the appropriate section of the forums can be found at the bottom of this page. Your submission will be 
critiqued by your peers but will not count towards your overall course grade.



https://codepen.io/Monpeco/pen/mBzLqE
