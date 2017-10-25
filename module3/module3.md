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

# Step 2: Creating the PostList Component

Creating the **PostButton** Component

### To start off we are going to create the component that represents the square buttons that are a part of each of the posts. 
We are going to add some style to it and display its label property.

```javascript
function PostButton(props){
    var style = {
        width:24,
        height:24
    }
    return (
        <button style = {style}>{props.label}</button>
    )
}
```

### Creating the PostText Component

Next, we are going to create the component that represents the text areas that are a part of each of the posts (**PostText**). 
We are going to add some style to it and display its label property. Its width will vary based on its width property.

```javascript
function PostText(props){
    var style = {
        border:"1px solid black",
        width: props.width
    }
    return (
        <div style = {style}>{props.text}</div>
    )
}
```

### Creating the Post Component

Next, we are going to create the component **Post** that represents the posts that go in the list of posts. We are going to 
add some styling to make it display its subcomponents horizontally. We are also going to pass in a title and 
score property down to its **PostText** components.

```javascript
function Post(props){
    var style = {
        display:"flex"
    }
    return (
        <div style = {style}>
            <PostButton label = "x"/>
            <PostText text = {props.title} width = "200"/>
            <PostButton label = "+" />
            <PostText text = {props.score} width = "20"/>
            <PostButton label = "-"/>
        </div>
    )
}
```

### Creating the PostList Component

Next, we are going to create the component that represents the list of posts (**PostList**). 
We are going to accomplish this by using the `map()` method to generate a **Post** component 
for each item in the componets **PostList** property array. We will wrap all of the **Post** 
components in a `<ol>` tag.

```javascript
function PostList(props){
    return (
        <ol>
        {
            props.postList.map((item,index) => 
                <Post key = {index} 
                      title = {item.title} 
                      score = {item.score}
                />
             )
         }
        </ol>
    )  
}
```

Test the **PostList** component by rendering it to the page with some test data.

```javascript
ReactDOM.render(
    <PostList postList = {[1,2,3,4,5]}/>,
    document.getElementById("root")
)
```

### Step 3: Creating a Controlled Component from the input field

To start off we are going to create an **App** component that will hold all of the 
other components.

```javascript
class App extends React.Component{
    constructor(props){
        super(props)
        this.state = {value:"", items : []}
    } 
    handleChange(event){
        this.setState({value:event.target.value})
        console.log(this.state.value)

    }
    render(){
        return (
            <div>
                <input value = {this.state.value} onChange = {this.handleChange.bind(this)}/>
            </div>
        )
    }
}
```

Test the **App** component by rendering it to the page.

```javascript
ReactDOM.render(
    <App/>,
    document.getElementById("root")
)
```

Next, we are going to initialize the App component's state. The **App** component 
will have two state attributes: one to hold the value of the input element and one 
to hold the array of post data.

Add this to the **constructor()** method:

```javascript
    this.state = {value:"", items : []}
```

Next, we are going to add an input element and make it a controlled component 
by tyings its value to the component state. We will accomplish this by declaring 
a **handleChange()** method that updates the components state whenever the 
input element's value is changed. We also have to bind the **handleChange** method 
to the **App** component so that the method refers to the right place.

```javascript
class App extends React.Component{
    constructor(props){
        super(props)
        this.state = {value:"", items : []}
    } 
    handleChange(event){
        this.setState({value:event.target.value})
        console.log(this.state.value)

    }
    render(){
        return (
            <div>
                <input value = {this.state.value} onChange = {this.handleChange.bind(this)}/>
            </div>
        )
    }
}
```

Test the input field to make sure that it is tying its value back to the component state 
by typing in some characters and viewing the console.


### Step 4: Adding values to the Post List

Next, are are going to add the functionality to add items to the state array.

To start, we are going to declare an event handler called **addItem()** to the App component. 
The method first makes a copy of the current items state array by using the `slice()` array. 
Then it takes in the value state attribute and truncates it to 20 characters using 
the `substring()` method. Then it creates an object containing the truncated string as a title 
and the value 0 as its score and adds it to the copied items array. Then it sorts the copied 
items array in descending order of score. Lastly, it updates the state to equal the sorted 
copied items array and sets the value state attribute back to an empty string.

Add to App component:
```javascritp
    addItem(){
        var itemsCopy = this.state.items.slice()
        var truncatedString = this.state.value.substring(0,20);
        itemsCopy.push({"title":truncatedString,"score":0})
        itemsCopy.sort((a,b)=>{
          return b.score - a.score;
        })
        this.setState({items:itemsCopy,value:""})
    }
```

Now that the **addItem()** event handler has been created, we need to create a submit button 
that will call the **addItem()** method when it is clicked. We will add it below the input element 
in the **render()** method of the App component.

Edit the button element in the **App render()** method:

```javascritp
    <button onClick = { () => this.addItem() }>Submit</button>
```

Now lets add the **PostList** component inside the **render()** method of the App component. We will 
supply its **postList** attribute with the **this.state.items** array that contains all of the post data.

Add to the **App render()** method:

```javascritp
    <PostList postList = {this.state.items}/>
```

Test the **App** component by typing something in the input field and pressing the submit button. 
A post should be added to the **PostList** with a title equal to the string entered in the input field.

### Step 5: Updating the post score

Next, we are going to add the functionality to update the post score when the **+** or **-** buttons are pressed.

To start, add a method called **updateScore()** to the **App** component. The **updateScore()** method should 
make a copy of the the items state attribute by using the `slice()` method. It will then reference a specific 
index of the copied items array and update that items score based on the val argument. The copied items array 
is then sorted and the state is set to equal the sorted copied array.

Add to **App** component:

```javascript
updateScore(index,val){
	var itemsCopy = this.state.items.slice()
	itemsCopy[index].score += val
	itemsCopy.sort((a,b) => {
		return b.score - a.score
	})
	this.setState({items:itemsCopy})
}
```

The **updateScore()** method needs to be passed down all the way to the button elements.

Pass the **updateScore()** method into the **PostList** component. Do not forget to bind the **updateScore()** 
method to the **App** component before passing it in.

Edit in App **render()** method:

```javascript
<PostList postList = {this.state.items}
			updateScore = {this.updateScore.bind(this)}  
/>
```
	
Create two attributes on the **Post** component that is rendered in the **PostList** component. The first 
will be an attribute named **incrementScore** that calls **updateScore(index,1)** which increments the score of 
the specified index in the items state array by 1. The second will be an attribute named **decrementScore** 
that calls **updateScore(index,-1)** which decrements the score of the specified index in the items state 
array by 1.

Edit in PostList component:

```javascript
<Post key = {index} 
		title = {item.title} 
		score = {item.score}
		incrementScore = {() => props.updateScore(index,1)}                         
		decrementScore = {() => props.updateScore(index,-1)} 
/>
```

Next, create a **handleClick** attribute on the **+** and **-** **PostButtons**. The **+** **PostButton** 
should have its **handleClick** attribute set equal to **incrementScore**, while the **-** **PostButton** 
should have its **handleClick** attribute set to equal **decrementScore**.

Edit in Post component:

```javascript
<PostButton label = "+" handleClick = {props.incrementScore}/>
<PostButton label = "-" handleClick = {props.decrementScore}/>
```

Lastly, edit the button element in the **PostButton** component to call **handleClick()** when it is 
clicked. This should make the button either increment or decrement its post's score.

Edit in PostButton component:

```javascript
    <button style = {style} onClick = { () => props.handleClick()}>{props.label}</button>
```

Test the **+** and **-** buttons by to see if they increment and decrement their post's scores. 
The **PostList** should automatically sort itself by descending post score whenever a post score is updated.

### Step 6: Removing posts

Next, we are going to add the functionality to remove 
posts.

To start, we are going to add a method called 
**removeItem()** to the **App** component. 
The **removeItem()** method will make a copy 
of the items state array by using the `slice()` 
method. It will then remove the specified index 
using the `splice()` method and then sort the 
array by descending score. It will then update 
the state to equal the sorted copied items array.

Add to App component:

```javascript
    removeItem(index){
        var itemsCopy = this.state.items.slice()
        itemsCopy.splice(index,1);
        itemsCopy.sort((a,b) => {
            return b.score - a.score
        })

        this.setState({items:itemsCopy})
    }
```

The **removeItem()** method needs to be passed 
down all the way to the button elements.

Pass the **removeItem()** method into the **PostList** 
component. Do not forget to bind the **removeItem()** 
method to the **App** component before passing it in.

Edit in **App** component **render()** method:

```javascript
    <PostList postList = {this.state.items}
                updateScore = {this.updateScore.bind(this)}  
                removeItem = {this.removeItem.bind(this)}
    />
```

Next, add a **removeItem** attribute in the **Post** 
component that is rendered in the **PostList** component.

The **removeItem** attribute should call the **removeItem()**
 method that was passed in with the **PostList**'s properties.

Edit in PostList component:

```javascript
    <Post key = {index} 
            title = {item.title} 
            score = {item.score} 
            incrementScore = {() => props.updateScore(index,1)}                         
            decrementScore = {() => props.updateScore(index,-1)} 
            removeItem = {() => props.removeItem(index)}/>
```

Next, create a **handleClick** attribute on the "x" 
**PostButton**. The "x" PostButton should have its **handleClick** 
attribute set equal to the **removeItem()** method that was passed 
in with **PostButton**'s properties.

Edit in **Post** component:

```javascript
    <PostButton label = "x" handleClick = {props.removeItem}/>
```

Test the "x" button to see if the posts are able to be removed.

