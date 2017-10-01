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