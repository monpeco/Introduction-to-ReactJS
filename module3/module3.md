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
