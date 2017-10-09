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

#### 