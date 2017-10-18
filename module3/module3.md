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