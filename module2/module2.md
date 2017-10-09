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



