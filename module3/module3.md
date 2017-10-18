#### Module 3 | Lists and Forms   Module 3 Intro   Module 3 Intro Video

# Module 3 Intro Video

> Welcome to Module 3, this module is about lists and forms. If you
> think about it, lists are actually pretty fun to generate using React.
> If you have a React component and you pass in an array as one of its
> properties, you just have to modify that array and return a new array
> of list items, and then render it. Forms are a bit trickier. Input
> elements naturally have some state already associated with their DOM
> elements, so we have to tie that state back into the React components.
> We call these types of inputs controlled components. So if you're
> ready to generate some list and some, forms let's move on to Module 3.

Tags: `lists`, `forms`, `controlled components`

---

#### Module 3 | Lists and Forms   Lists   Lists

# Rendering arrays of React Elements

JSX will render an array of React Elements as long as there is at least one element enclosing all of the array elements. 
The array elements will be inserted into the enclosing element.

For example, it is possible to render multiple components at the same time using a for loop with JSX:

```javascript
var elements = [] 
var array = [1,2,3,4,5]

for(let i = 0; i < array.length; i++){
   elements.push(<li>{array[i]}<li/>)
}


ReactDOM.render(
  <ol>{elements}</ol>,
  document.getElementById('root')
)
```

# Using Map() to render arrays of React Elements

The `map()` method is often used to create an array of React Elements. The `map()` method is called on an array and 
returns a new array with a provided function applied to each element in the original array.

Example of using the `map()` method to return an array of React Elements:

```javascript
var array =[
  {product:"Apple", price:3},
  {product:"Banana", price:1},
  {product:"Carrot", price:2},
  {product:"Donuts", price:5},
  {product:"Eggplant", price:4}
]

var elements = array.map( (item) => {
  return <li>Product: {item.product} | Price: ${item.price}  </li>>
})

ReactDOM.render(
  <ol>{elements}</ol>,
  document.getElementById('root')
)
```

The map() method can also be directly used inside a JSX expression:

```javascript
ReactDOM.render(
  <ol>{
      array.map( (item) => 
          <li>Product: {item.product} | Price: ${item.price} </li>
      )}
  </ol>,
  document.getElementById('root')
)
```

# Adding Keys to List Items

React uses **Keys** to help render list items quickly. Keys should be a string that uniquely identifies a list item 
from the other items on the list, such as an ID attribute.

Exmaple of using an ID as a key value:

```javascript
var array =[
  {id: 100, product:"Apple", price:3},
  {id: 101, product:"Banana", price:1},
  {id: 102, product:"Carrot", price:2},
  {id: 103, product:"Donuts", price:5},
  {id: 104, product:"Eggplant", price:4}
]

var elements = array.map( (item) => {
  return <li key={item.id}>Product: {item.product} | Price: ${item.price}  </li>
})

ReactDOM.render(
  <ol>{elements}</ol>,
  document.getElementById('root')
)
```

If your array items do not have anything that can uniquely identify them, you can use the item index as a last resort 
for the key value. The drawback to using indexes as keys is that list item reordering is slow to rerender.

Example of using the item index as a key value:

```javascript
var array =[
  {product:"Apple", price:3},
  {product:"Banana", price:1},
  {product:"Carrot", price:2},
  {product:"Donuts", price:5},
  {product:"Eggplant", price:4}
]

//the item index is the second argument to the map() method
var elements = array.map( (item,index) => {
  return <li key={index}>Product: {item.product} | Price: ${item.price}  </li>>
})

ReactDOM.render(
  <ol>{elements}</ol>,
  document.getElementById('root')
)
```

# Building a List Component

It is useful to be able to build a React Component that can dynamically generate a list from an array property 
that is passed into it.

```javascript
class ProductList extends React.Component{
  constructor(props){
    super(props)
  }
  render(){
    var elements = this.props.productArray.map( (item,index) => {
      return <li key={item.id}>Product: {item.product} | Price: ${item.price}  </li>
    })
    return <ol>{elements}</ol>
  }
}

var array =[
  {id: 100, product:"Apple", price:3},
  {id: 101, product:"Banana", price:1},
  {id: 102, product:"Carrot", price:2},
  {id: 103, product:"Donuts", price:5},
  {id: 104, product:"Eggplant", price:4}
]


ReactDOM.render(
  <ProductList productArray = {array}/>,
  document.getElementById('root')
)
```

# Extracting List Items

Each list item may be extracted into its own React Component to make the code more maintainable. If the list items are extracted, the keys do not need to be passed down to the list item components. Keys are only necessary when React Elements are generated dynamically using arrays.

```javascript
function ListItem(props){
  render(){
    //don't need to add a key to 
    return <li>Product: {props.product} | Price: ${props.price}  </li>
  }
}


class ProductList extends React.Component{
  render(){
    var elements = array.map( (item,index) => {
      //need to add a key here
      return <ListItem key={item.id} product={item.product} price = {item.price}/>
    })

    return (
      <ol>
        {elements}
      </ol>
    )

  }

}

var array =[
  {id: 100, product:"Apple", price:3},
  {id: 101, product:"Banana", price:1},
  {id: 102, product:"Carrot", price:2},
  {id: 103, product:"Donuts", price:5},
  {id: 104, product:"Eggplant", price:4}
]

ReactDOM.render(
  <ProductList productArray = {array}/>,
  document.getElementById('root')
)
```

--- 

#### Module 3 | Lists and Forms   Lists   Lists Video

Missing video

> Hello, in this video I will be covering how to create a list component
> back and dynamically generate a list of react elements. The end goal
> is to take an array of items pass it into a component and hide a
> dynamic generated list of React or spread into the page. So to begin,
> let's create a class component named ProductList. Next, we're gonna
> create its constructor. We're gonna pass it props so that it can use
> properties. Next, we're gonna call super so that the properties work
> correctly. And then, we're gonna define the render method. To start
> off we're going to return an ordered list tag, cuz all of our list
> items have to be surrounded by something. Now we're gonna define what
> we're gonna return. So I'm gonna create a variable named elements, and
> I'm going to set that equal to this item array that was passed in.
> This array was passed in as a productArray attribute, so I can
> reference it by this.props.productArray. Now I'm gonna use the map
> method to transform all of the values in the array. I'm gonna
> transform them into a bunch of list items instead of just having
> objects. So I could do that by writing the call back like this. This
> item And inside list items, I'm just going to define, Product is being
> displayed, And what the price of the product is. Now, I'm gonna use a
> JSX expression to embed this elements variable to be ordered list
> type. And now, if we look over here, you see that a list of React
> elements has been rendered to the page. Now, it is important to add a
> key to this items. So, I'm gonna define the attribute and set that
> equal to the item.id attribute. This will ensure that the lists
> re-render efficiently whenever an update happens.

---

#### Module 3 | Lists and Forms   Forms   Forms

# Forms

# Controlled Components

HTML form elements such as inputs, text areas, and select fields naturally keep some internal state. 
When we use HTML form elements in React, we tie that natural state to the React Component state so 
that all of the state can be maintained by a single source.

We accomplish this by doing the following two steps:

1. Whenever the input value is changed, call an event handler to update the component state to the new input value
2. Re render the the React Element with its value attribute set to the updated state input value

Form elements that have their state's controlled by React in his manner are called **Controlled Components**.

### Controlling Input fields

To turn an input field into a **Controlled Component**, we must first declare an event handler that will update 
the state input value whenever the form input value is changed.

The `event.target.value` attribute can be used to obtain the form input value:

```javascript
handleChange(event){
	this.setState({value: event.target.value})
}
```

We then must attach the event handler to the `<input>` element and set the input value equal to the state input value:

```javascript
render(){
	return (
		<input type = "text" value = {this.state.value} onChange = {this.handleChange}/>
	)
}
```

Lastly, we must not forget to bind the event handler to the component instance and also declare the initial state value:

```javascript
constructor(props){
	super(props)
	this.state = {value: ''}
	this.handleChange = this.handleChange.bind(this)
}
```

Putting it all together:

```javascript
class ControlledInput extends React.Component{

    constructor(props){
        super(props)
        this.state = {value: ''}
        this.handleChange = this.handleChange.bind(this)
    }
    handleChange(event){
        this.setState({value: event.target.value})
    }
    render(){
        return (
            <input type = "text" value = {this.state.value} onChange = {this.handleChange}/>
        )
    }
}
```

### Controlling Checkboxes

Checkboxes use a checked attribute instead of a value attribute.

```javascript
class ControlledInput extends React.Component{

    constructor(props){
        super(props)
        this.state = {checked: false}
        this.handleChange = this.handleChange.bind(this)
    }
    handleChange(event){
        this.setState({checked: event.target.checked})
    }
    render(){
        return (
            <input type = "checkbox" checked = {this.state.checked} onChange = {this.handleChange}/>
        )
    }
}
```

### Controlling TextArea fields

Controlling TextAreas is similar to controlling Input Fields in React:

```javascript
class ControlledTextArea extends React.Component{

    constructor(props){
        super(props)
        this.state = {value: ''}
        this.handleChange = this.handleChange.bind(this)
    }
    handleChange(event){
        this.setState({value: event.target.value})
    }
    render(){
        return (
            <textarea type = "text" value = {this.state.value} onChange = {this.handleChange}/>
        )
    }
}
```

### Controlling Select Tags

Controlling Select Tags is similar to controlling Input Fields in React:

```javascript
class ControlledSelect extends React.Component{

    constructor(props){
        super(props)
        this.state = {value: 'apple'}
        this.handleChange = this.handleChange.bind(this)
    }
    handleChange(event){
        this.setState({value: event.target.value})
    }
    render(){
        return (
          <select value={this.state.value} onChange={this.handleChange}>
            <option value="apple">apple</option>
            <option value="banana">banana</option>
            <option value="carrot">carrot</option>
            <option value="donuts">donuts</option>
          </select>
        )
    }
}
```

Select Components can also have their options dynamically generated using the `map()` method. Example:

```javascript
class ControlledSelect extends React.Component{

    constructor(props){
        super(props)
        this.state = {value: 'apple'}
        this.handleChange = this.handleChange.bind(this)
    }
    handleChange(event){
        this.setState({value: event.target.value})
    }
    render(){
        var array = ["apple","banana","carrot","donuts"]
        var options = array.map( (item) =>
            <option value = {item}>{item}</option>
        )
        return (
          <select value={this.state.value} onChange={this.handleChange}>
            {options}
          </select>
        )
    }
}
```

### Handling Multiple Inputs

If your form has multiple inputs, you can set each of their values to a different attribute 
on the component state. It is useful to use ES6's computed property name feature to 
accomplish this.

```javascript
class ControlledMultiple extends React.Component{

    constructor(props){
        super(props)
        this.state = {value: 'apple'}
        this.handleChange = this.handleChange.bind(this)
    }
    handleChange(event){


        this.setState({[event.target.name]: event.target.value})
    }
    render(){
        var array = ["apple","banana","carrot","donuts"]
        var options = array.map( (item) =>
            <option value = {item}>{item}</option>
        )
        return (
            <form>
                <input name="inputName" type = "input" value = {this.state.inputName} onChange = {this.handleChange}/>
                <textarea name="textAreaName" type = "text" value = {this.state.textAreaName} onChange = {this.handleChange}/>

                <select name = "selectName" value={this.state.selectName} onChange={this.handleChange}>
                    {options}
                </select>
            </form>
        )
    }
}
```
---

### Module 3 | Lists and Forms   Forms   Forms Video

# Forms Video

missing video

> Hello. In this video I will be explaining, how to take an input
> element. And transform it into a controlled component. So to start,
> let's define a class component. It's the unit control input. Now it
> has been on class imported, because we have to stay. So we can not
> define it as a functional point. Now let's define deconstructor,
> props, and let's do super props. Now let's define your render method.
> And to start off, let's return a simple input element. And if you look
> over here, you can see that the input element has been rendered to the
> page. Now in order to turn this input element into a control
> component, we need to tie its value to the component state. So let's
> do that. So first, let's define some initial states, this.states. And
> we can set the value of the initial state value to be and end the
> string. Now, what we need to do is define an event handler. And what
> this event handler is gonna do is whenever the input value is changed.
> It's going to take that changed value and set it equal to the
> component state. So let's do that. This set state. And we can pass in
> value and set it equal to event target value. Which represents the new
> value of the inputs after it's been changed. So lastly we need to
> attach this to the input element by setting the on change attribute
> equal to handle change. And Let's test this by putting a console log.
> We can log the new state value after it's been updated. So let's test
> if this works. Okay I'm typing stuff but nothing's being logged to the
> console. There's a reason for this. The reason why it doesn't work is
> because we do not bind the handle change method to the custom point.
> So let's do that. So now let's test if it works. So now if you look at
> the console, remember the input elements is changed. The panel change
> method fires, and then it sets the state value to panel change value.
> The bind method ensures that the panel change method is called within
> the right context. And that is how to create a control equivalent out
> of an input element.

---

#### Module 3 | Lists and Forms   Module 3 Tutorial   Module 3 Tutorial

# Module 3 Tutorial

In this tutorial we are are going to learn how to build an application 
that allows users to post topics and upvote/downvote the topics.

[Link to Demo/Solution](https://codepen.io/benjlin/pen/rwGKjW)

Image of an HTML DOM
![HTML DOM](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/9df1f12316a53541b020144002ee0b53/asset-v1:Microsoft+DEV281x+4T2017+type@asset+block/m3tutorial1.PNG)

# Step 1: Breaking up the application into components

Image of an HTML DOM
![HTML DOM](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/282f538d62e8eb239d6c417d27e2ee64/asset-v1:Microsoft+DEV281x+4T2017+type@asset+block/m3tutorial1divided.png)

As the above image shows, we have broken up the application into 
several sections:

* A section that contains an **input field**(red)
* A section that contains a **submit button**(brown)
* A component that contains a **list of posts**(orange)
* A subcomponent that represents a **post**(blue)
* A sub-subcomponent that represents a **square button**(red)
* A sub-subcomponent that represents **text** (green)

